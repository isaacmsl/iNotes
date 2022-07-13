*Portuguese version*

## Entrada e saída

Troca de dados entre o meio externo e o processador.

### Controlador E/S

- Necessidade de um controlador E/S
  - Variedade de E/S
  - Transferência mais lenta do que a memória e processador
  - Transferência de dados extensos
  - Formato de dados e palavras diferentes

### Portas E/S

- Interface entre o barramento de sistemas e os dispositivos E/S
- Permitem troca, retirada e acréscimo de dispositivos E/S sem alterar arquitetura do computador
- Dedicadas
  - Espaço de endereço único
  - Comandos especiais de E/S
- Mapeadas em memória
  - Compartilham o mesmo espaço de endereçamento de memória
  - Vistos pelo processador como locais na memória

### Modos de transmissão

- Paralela: uma linha por bit transmitidos simultaneamente
- Serial: uma linha e cada bit é enviado serialmente um por vez

### Transferência de dados

- Transferência entre memória e E/S ocorre por meio de protocolos
- 3 técnicas básicas
```
                      ^
Grau de envolvimento  | Polling
do processador        | Orientado a interrupções
                      | Direct Memory Access (DMA)
```
  - Polling
    - Testa repetida e sequencialmente se E/S's estão prontos
    - Frequência do dispositivo que exige a maior taxa
  - Interrupções: CPU responde somente quando requisitada
  - DMA
    - Transferir dados diretamente a memória sem envolver CPU
    - Interrupções para informar finalização de transferências ou erros