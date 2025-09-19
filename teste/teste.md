```mermaid
flowchart TD

    A[Inicio] --> B[escreveArquivo]
    B --> C[leArquivo -> parametros]
    C --> D[alfabeto(parametros)]
    D --> E[Inicializa populacao]

    E --> F[Loop: enquanto geracao <= maxGeracoes]
    
    F --> G[reproducao]
    G --> G1[Elitismo: mantem os melhores]
    G1 --> G2[Selecao por Torneio: escolhe pais]
    G2 --> G3[Recombinacao Uniforme: gera filhos]
    G3 --> G4[Mutacao: altera genes]
    G4 --> G5[Fitness: avalia frases]
    G5 --> H[Melhor individuo atualizado]

    H --> I{Fitness == 0?}
    I -- Nao --> J[Proxima geracao]
    J --> F
    I -- Sim --> K[Fim do loop]

    K --> L[Calcular tempo total]
    L --> M[escreveRelatorio (tempo, fitness)]
    M --> Z[Fim]

    %% Grupos de processos
    subgraph Classes [Classes Auxiliares]
        IND[Classe INDIVIDUO]
        PAR[Classe PARAMETROS]
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
