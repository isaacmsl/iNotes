*Portuguese version*

## Barramentos

Comunicação entre dispositivos internos

### Categorias

- Dados, endereço e controle
- Características
  - Dados
    - :satellite: Dados ou instruções
    - :left_right_arrow: Bidirecional

  - Endereço
    - Processador ou E/S envia locais de memória :satellite:
    - Largura (qnt. caminhos elétricos) proporcional a qnt. de locais que se pretende acessar na memória
    - :arrow_right: Unidirecional

  - Controle
    - :satellite: Solicitações e confirmações
    - :left_right_arrow: Bidirecional
    - Clock; reset; I/O read/write etc.

### Vantagens

- Versátil para novos periféricos
- Baixo custo pois é compartilhado por vários dispositivos

### Desvantagens

- A disputa entre os dispositivo pode ser um gargalo
- Velocidade limitada pelo comprimento e qnt. de dispositivos ligados

### Tipos

- Dedicado
  - Barramentos distintos para endereço e dados
  - Alto desempenho/custo

- Multiplexado
  - Um barramento compartilha endereço e dados
  - Baixo custo/velocidade

### Temporização

- Síncrono
  - Incluem sinal de clock
  - Barramento processador/memória
  - É vantajoso pois é rápido e simples de implementar
  - Sua desvantagem é que todos os componentes se comunicam a mesma velocidade

- Assíncrono
  - Não há sinal de clock
  - *Handshaking* para coordenar o uso do barramento
```
+-------+                           +---------+  
|       | - Pronto para receber? -> |         |
| Fonte | <- Pronto -               | Destino |
|       | - Dado enviado ->         |         |
|       | <- Dado recebido -        |         |
+-------+                           +---------+
```
  - Componentes podem se comunicar com !='s velocidades e ++comprimento para o barramento
  - Implementação é muito complexa

### Arbitragem

- Disputa: 2 a n dispositivos tentando acessar ao mesmo tempo
```
--------------------------
    |---->:boom:<----|
   E/S              E/S
```
- *Master/slave* para resolver disputas
  - Somente *Bus master* inicia e controla
  - *Bus slave* responde as requisições do *Bus master*

- Tipos
  - Estática
    - Controle pré-determinado
    - Fácil implementação
    - Não versátil
    - O barramento é alocado mesmo qnd não é preciso (ruim)
  - Dinâmica
    - Aloca somente quando é preciso
    - Duas linhas: *bus request* (*master* solicita uso do barramento) e *bus grant* (*master* recebe permissão)
  
- Política de alocação
  - Por prioridade de dispositivo
  - Justo: tempo de uso distribuído igualmente
  - Híbrido (prioridade e justo)

- *Daisy Chaining*
  - *Bus grant* é enviado
  - Os dispositivos propagam o *Bus grant* até o chegar no *Bus master* (dispositivo que solicitou)
  - Implementação simples
  - Não garante justiça (ruim)

- Requisições independentes
  - Cada dispositivo é conectado por linhas *grant*/*request* com um *Center arbiter*
  - Implementação complexa (ruim)
  
- Híbrida
  - Dispositivos com prioridade semelhante são divididos em classes
  - Cada classe possui linhas *grant*/*request*
  - Cada classe é conectada ao barramento com *Daisy chaining*

- Arbitragem distribuída
  - Dispositivos decidem quem será o *Bus master*

### Hierarquia

Para evitar gargalos devido a grande qnt. de dispositivos (proporcional ao comprimento do barramento).

- Barramento local, sistema, alta velocidade e expansão