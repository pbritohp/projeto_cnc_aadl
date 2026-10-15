# Projeto CNC AADL

Modelo em AADLv2 de uma máquina CNC de três eixos (Technodrill) e da sua
comunicação por Ethernet com um gateway ESP32, que recebe a telemetria da
máquina. O projeto é avaliado apenas em simulação.

Trabalho da disciplina DAS410056 – Projeto e Desenvolvimento de Sistemas
Embarcados (PPGEAS/UFSC), Prof. Leandro Buss Becker.

## Estrutura

```
aadl/
  types.aadl          CNC::Types       tipos de dados
  hardware.aadl       CNC::Hardware    barramentos, processadores, motores e sensores
  software.aadl       CNC::Software    processos e threads
  cnc_system.aadl     CNC::Integration sistema raiz: conexões, alocações e fluxos
property_sets/
  Cheddar_Properties.aadl              propriedades usadas pelo Cheddar
requirements/
  cnc_campo.reqspec                    requisitos CNC <-> atuadores (críticos)
  cnc_telemetria.reqspec               requisitos CNC -> ESP32 (não críticos)
cheddar/                               modelo convertido para o Cheddar (gerado)
```

## Ferramentas

- **OSATE 2.20**: modelagem, validação, instanciação e requisitos (ReqSpec).
- **Cheddar 3.3**: análise de escalonamento (Rate Monotonic preemptivo).
- **[aadl_v2_to_v1_Cheddar_use](https://github.com/pbritohp/aadl_v2_to_v1_Cheddar_use)**:
  script que converte o modelo AADLv2 para o AADLv1 aceito pelo Cheddar.

## Como usar

1. No OSATE: `File > Import > Existing Projects into Workspace` e selecione
   esta pasta (projeto `CNC_Technodrill`).
2. Instancie `CNC::Integration::CNC_Machine.impl` (botão direito > `Instantiate`).
3. Para o escalonamento, gere o modelo do Cheddar com o script de conversão e
   rode a simulação no Cheddar.

## Autores

Esther Ijeoma Ugo · José Antonio de Oliveira · Pedro Teixeira Brito
