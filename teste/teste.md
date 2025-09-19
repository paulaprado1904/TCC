flowchart TD

    A[Início] --> B[escreveArquivo()]
    B --> C[leArquivo() → parâmetros]
    C --> D[alfabeto(parametros)]
    D --> E[inicializa população]

    E --> F[Loop: enquanto geração ≤ máx. gerações]
    
    F --> G[reproducao()]
    G --> G1[Elitismo: mantém os melhores]
    G1 --> G2[Seleção por Torneio: escolhe pais]
    G2 --> G3[Recombinação Uniforme: gera filhos]
    G3 --> G4[Mutação: altera genes]
    G4 --> G5[Fitness: avalia frases]
    G5 --> H[Melhor indivíduo atualizado]

    H --> I{Fitness == 0?}
    I -- Não --> J[Próxima geração]
    J --> F
    I -- Sim --> K[Fim do loop]

    K --> L[Calcular tempo total]
    L --> M[escreveRelatorio(tempo, fitness)]
    M --> Z[Fim]

    %% Grupos de processos
    subgraph Classes
        IND[Classe INDIVIDUO: fitness, fraseArray]
        PAR[Classe PARAMETROS: fraseAlvo, população, mutação, etc.]
    end

    subgraph Arquivos
        ARQ1[entrada.in: parâmetros e frase alvo]
        ARQ2[relatorio.txt: tempo e fitness]
        ARQ3[metricas.in: dados binários]
    end

    %% Ligações externas
    B --> ARQ1
    C --> ARQ1
    M --> ARQ2
    M --> ARQ3
