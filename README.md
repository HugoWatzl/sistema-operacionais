# Resumo Completo: Fundamentos de SO e Comandos Linux

Este resumo abrange os conceitos teóricos de Sistemas Operacionais (SO) e os comandos práticos do Linux abordados nos questionários.

## Parte 1: Fundamentos de Sistemas Operacionais (Teoria)

### 1. Objetivos e Estrutura do SO

-   [cite_start]**Objetivos Principais**[cite: 9]:
    1.  **Abstrair o Hardware**: Criar uma camada (máquina estendida) que esconde a complexidade do hardware e oferece uma interface simples para os programas e usuários.
    2.  **Gerenciar Recursos**: Distribuir de forma justa e eficiente os recursos do computador (CPU, memória, disco) entre os vários processos.
-   [cite_start]**Estrutura Básica**[cite: 20]:
    -   **Kernel (Núcleo)**: É o cérebro do SO. [cite_start]Gerencia diretamente o hardware, controla a execução de processos, gerencia memória e dispositivos[cite: 21].
    -   **Shell**: É a camada de interface com o usuário. [cite_start]Interpreta os comandos do usuário (seja por linha de comando, CLI, ou por interface gráfica, GUI) e os repassa para o kernel executar[cite: 20, 22].

### 2. O Conceito de Processo

-   **O que é?**: Um processo é um programa em execução. [cite_start]É a unidade fundamental de trabalho para o SO, com seu próprio espaço de memória, registradores e estado[cite: 23, 24].
-   [cite_start]**Importância**: Essencial em sistemas multitarefa, pois permite que o SO gerencie e alterne entre várias tarefas concorrentes[cite: 23].
-   [cite_start]**Estados de um Processo**[cite: 25, 26]:
    -   `New` (Novo): O processo está sendo criado.
    -   `Ready` (Pronto): Aguardando na fila para usar a CPU.
    -   `Running` (Executando): Usando a CPU no momento.
    -   `Waiting` (Aguardando): Esperando por um evento (ex: uma leitura de disco).
    -   `Terminated` (Terminado): A execução foi concluída.
-   [cite_start]**Processos em Background**: Conhecidos como *daemons* (ou serviços), são processos que rodam sem interação direta do usuário para realizar tarefas do sistema[cite: 29].

### 3. Classificação (Taxonomia) dos SO

-   **Quanto às Tarefas**:
    -   [cite_start]**Monotarefa**: Executa apenas uma tarefa por vez[cite: 10].
    -   [cite_start]**Multitarefa**: Executa múltiplas tarefas concorrentemente, dividindo o tempo da CPU[cite: 10].
-   **Quanto ao Tempo de Resposta**:
    -   [cite_start]**Tempo Compartilhado (Time-Sharing)**: Otimiza o uso interativo para vários usuários, dando a ilusão de simultaneidade[cite: 12].
    -   **Tempo Real (Real-Time)**: O fator crítico é a **garantia** de que uma tarefa será concluída dentro de um prazo rigoroso (deadline). [cite_start]Essencial para sistemas críticos (usinas nucleares, freios ABS, etc.)[cite: 12, 18].
-   **Quanto à Arquitetura de Processadores**:
    -   **Fortemente Acoplados**: Múltiplos processadores que compartilham a mesma memória e relógio. [cite_start]A comunicação é muito rápida[cite: 14].
        -   [cite_start]**SMP (Simétrico)**: Todos os processadores têm o mesmo tempo de acesso à memória[cite: 15].
        -   [cite_start]**NUMA (Não Uniforme)**: O acesso à memória local de um processador é mais rápido que o acesso à memória de outro[cite: 15].
    -   [cite_start]**Fracamente Acoplados**: Múltiplos computadores independentes conectados por uma rede[cite: 14].
        -   [cite_start]**Clusters**: Trabalham juntos em um local para alta disponibilidade ou alto desempenho[cite: 16].
        -   [cite_start]**Sistemas Distribuídos**: Apresentam-se ao usuário como um único sistema, podendo estar geograficamente separados[cite: 17].

## Parte 2: Comandos e Recursos do Shell Linux (Prática)

### 1. Controle de Sessão e Sistema

-   [cite_start]`logout` ➡ Finaliza uma sessão de **login shell**[cite: 84, 98].
-   `exit` ➡ Finaliza o **shell atual**. [cite_start]Se for o de login, funciona como `logout`[cite: 85, 98].
-   [cite_start]`shutdown` ➡ Comando **seguro e versátil** para desligar (`-h`) ou reiniciar (`-r`)[cite: 88, 100].
-   `reboot` ➡ Reinicia a máquina. [cite_start]Atalho para `shutdown -r now`[cite: 86, 99].
-   `halt` ➡ Interrompe o sistema. [cite_start]Atalho para `shutdown -h now`[cite: 87, 99].

### 2. Navegação e Manipulação de Arquivos

-   [cite_start]**Hierarquia de Arquivos (FHS)**: Um padrão que organiza os diretórios no Linux[cite: 45].
    -   [cite_start]`/bin`: Comandos essenciais[cite: 46].
    -   [cite_start]`/home`: Diretórios dos usuários[cite: 46].
    -   [cite_start]`/etc`: Arquivos de configuração[cite: 46].
    -   [cite_start]`/var`: Dados variáveis, como logs[cite: 46].
-   **Comandos Essenciais**:
    -   [cite_start]`ls`: **Lista** o conteúdo de diretórios[cite: 89].
    -   [cite_start]`cd`: **Altera** o diretório[cite: 90].
    -   [cite_start]`mkdir`: **Cria** diretórios[cite: 91].
    -   [cite_start]`rmdir`: **Remove diretórios vazios**[cite: 92, 112].
    -   [cite_start]`cp`: **Copia** arquivos/diretórios[cite: 93].
    -   [cite_start]`mv`: **Move** ou **renomeia** arquivos/diretórios[cite: 94].
    -   [cite_start]`rm`: **Remove** arquivos e diretórios (`-r` para diretórios com conteúdo)[cite: 95, 112].

### 3. Metadados e Links

-   [cite_start]**Caminho Absoluto vs. Relativo**: Absoluto começa da raiz (`/`), Relativo começa do diretório atual (`.`)[cite: 47].
-   [cite_start]**i-node**: O "RG" de um arquivo, contendo seus metadados (permissões, dono, etc.)[cite: 48].
    -   [cite_start]`stat <arquivo>`: Mostra todos os metadados[cite: 49, 96].
-   [cite_start]**Links** (`ln`)[cite: 56, 97]:
    -   **Hard Link**: Um novo nome para o **mesmo i-node**. [cite_start]Sobrevive à exclusão do original[cite: 56].
    -   **Soft Link (`ln -s`)**: Um atalho para o **nome** do arquivo original. [cite_start]Quebra se o original for removido[cite: 56].

### 4. Processamento de Texto e Busca

-   **Visualização**:
    -   [cite_start]`cat`: Mostra o conteúdo **inteiro** de um arquivo[cite: 123].
    -   [cite_start]`more`/`less`: Mostram o conteúdo **página por página**[cite: 124, 135].
    -   [cite_start]`head`/`tail`: Mostram o **início** ou o **fim** de um arquivo[cite: 125, 126].
-   **Busca e Manipulação**:
    -   [cite_start]`grep`: **Busca** por padrões de texto dentro de arquivos[cite: 129, 139].
    -   [cite_start]`find`: **Procura** por arquivos no sistema com base em critérios (nome, tamanho, etc.)[cite: 131, 140].
    -   [cite_start]`wc`: **Conta** linhas, palavras e caracteres[cite: 127].
    -   [cite_start]`cut`: **Extrai colunas** de um texto[cite: 128, 138].
    -   [cite_start]`sort`: **Ordena** linhas de um texto[cite: 130].

### 5. Arquivamento e Compactação

-   [cite_start]`tar`: **Agrupa** vários arquivos em um único "pacote" `.tar` (arquivador)[cite: 133, 146].
-   [cite_start]`gzip`: **Compacta** um arquivo[cite: 132, 145].
-   [cite_start]`gunzip` ou `gzip -d`: **Descompacta** um arquivo `.gz`[cite: 145].

### 6. Recursos do Shell

-   [cite_start]**Redirecionadores**[cite: 134]:
    -   `>`: Envia a saída para um arquivo, **sobrescrevendo-o**.
    -   `>>`: Envia a saída para um arquivo, **adicionando** ao final.
    -   `<`: Usa um arquivo como **entrada** para um comando.
-   [cite_start]**Pipe `|`**: Conecta a **saída** de um comando na **entrada** de outro, criando um encadeamento[cite: 136].
-   [cite_start]**Metacaracteres (Globbing)**[cite: 117]:
    -   `*`: Corresponde a **qualquer** sequência de caracteres.
    -   `?`: Corresponde a **um único** caractere.
    -   `[]`: Corresponde a **um dos caracteres** dentro dos colchetes.

### 7. Editor de Texto VIM

-   [cite_start]`:w` ➡ **Salva** (write)[cite: 149].
-   [cite_start]`:q` ➡ **Sai** (quit)[cite: 153].
-   [cite_start]`:x` ou `:wq` ➡ **Salva e sai**[cite: 151].
-   [cite_start]`:e <arquivo>` ➡ **Abre** um arquivo para edição[cite: 148].
