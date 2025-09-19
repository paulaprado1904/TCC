```mermaid
flowchart TD

    A[Inicio] --> B[Escreve Arquivo]
    B --> C[Le Arquivo -> Parametros]
    C --> D[Alfabeto Parametros]
    D --> E[Inicializa Populacao]

    E --> F[Loop: enquanto geracao menor_igual maxGeracoes]
    
    F --> G[Reproducao]
    G --> G1[Elitismo: mantem os melhores]
    G1 --> G2[Selecao por Torneio: escolhe pais]
    G2 --> G3[Recombinacao Uniforme: gera filhos]
    G3 --> G4[Mutacao: altera genes]
    G4 --> G5[Fitness: avalia frases]
    G5 --> H[Melhor individuo atualizado]

    H --> I{Fitness igual a zero?}
    I -- Nao --> J[Proxima Geracao]
    J --> F
    I -- Sim --> K[Fim do Loop]

    K --> L[Calcular Tempo Total]
    L --> M[Escreve Relatorio]
    M --> Z[Fim]

    %% Grupos de processos
    subgraph Classes [Classes Auxiliares]
        IND[Classe Individuo]
        PAR[Classe Parametros]
    end

    subgraph Arquivos [Arquivos]
        ARQ1[entrada.in]
        ARQ2[relatorio.txt]
        ARQ3[metricas.in]
    end

    %% Ligacoes externas
    B --> ARQ1
    C --> ARQ1
    M --> ARQ2
    M --> ARQ3
