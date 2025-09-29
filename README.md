# Resumo Rápido de Comandos e Conceitos Linux

Este é um guia baseado nos exercícios para fixar os principais comandos e conceitos do shell Linux.

## 1. Controle de Sessão e Sistema

A diferença principal é entre **encerrar sua sessão** e **desligar a máquina**.

-   `logout` ➡ Finaliza uma sessão de **login shell**. É o comando para "desconectar".
-   `exit` ➡ Finaliza o **shell atual**. Se for o shell de login, funciona como `logout`.
-   `shutdown` ➡ O comando **mais seguro** para desligar (`-h`) ou reiniciar (`-r`). Permite agendar e avisa outros usuários.
-   `reboot` ➡ Atalho para `shutdown -r now`. Reinicia a máquina.
-   `halt` ➡ Interrompe o sistema. Em geral, desliga a máquina.

## 2. Manipulação de Arquivos e Diretórios

Comandos essenciais para navegar e organizar o sistema de arquivos.

-   `ls` ➡ **Lista** o conteúdo de um diretório.
    -   `ls -l`: Lista longa (detalhada).
    -   `ls -a`: Mostra arquivos ocultos.
    -   `ls -h`: Tamanho legível por humanos (ex: 1K, 2M).
-   `cd` ➡ **Altera** o diretório atual.
    -   `cd ..`: Vai para o diretório pai.
    -   `cd ~` ou `cd`: Vai para o seu diretório home.
-   `mkdir` ➡ **Cria** um novo diretório.
-   `rmdir` ➡ **Remove** um diretório, mas **somente se estiver vazio**.
-   `rm` ➡ **Remove** arquivos.
    -   `rm -r <diretorio>`: Remove um diretório e todo o seu conteúdo (cuidado!).
-   `cp` ➡ **Copia** arquivos/diretórios.
    -   `cp <origem> <destino>`
-   `mv` ➡ **Move** ou **renomeia** arquivos/diretórios.
    -   `mv <antigo_nome> <novo_nome>`: Renomeia.
    -   `mv <arquivo> <diretorio/>`: Move.
-   **Dica de Segurança:** Use a opção `-i` (interativo) com `cp`, `mv` e `rm` para que o sistema peça confirmação antes de sobrescrever ou apagar algo. Ex: `rm -i arquivo.txt`.

## 3. Metadados e Links (Conceito de i-node)

-   **i-node**: É o "RG" de um arquivo. Contém todas as informações sobre ele (permissões, dono, tamanho), **exceto** o nome e o conteúdo.
    -   `stat <arquivo>`: Mostra todas as informações do i-node.
    -   `ls -i <arquivo>`: Mostra o número do i-node do arquivo.
-   **Links**: São "atalhos" para arquivos.
    -   `ln <arquivo> <hard_link>`: **Hard Link**. Um novo nome que aponta para o **mesmo i-node**. Se o arquivo original for apagado, o hard link continua funcionando.
    -   `ln -s <arquivo> <soft_link>`: **Soft Link**. Um atalho que aponta para o **nome do arquivo original**. Se o original for apagado, o link quebra.

## 4. Visualização e Processamento de Texto

-   `cat` ➡ Mostra o conteúdo **inteiro** de um arquivo na tela.
-   `more` ➡ Mostra o conteúdo página por página (só permite avançar).
-   `less` ➡ Versão melhorada do `more` (permite avançar e voltar).
-   `head` ➡ Mostra as **primeiras** 10 linhas de um arquivo.
-   `tail` ➡ Mostra as **últimas** 10 linhas de um arquivo.
-   `wc` ➡ **Conta** linhas, palavras e caracteres (`-l`, `-w`, `-c`).
-   `grep` ➡ **Busca** por uma palavra ou padrão dentro de um arquivo.
-   `sort` ➡ **Ordena** as linhas de um arquivo.
-   `cut` ➡ **Corta** e extrai colunas de um texto, usando um delimitador.

## 5. Busca e Arquivamento

-   `find` ➡ **Procura** por arquivos no sistema com base em critérios (nome, tamanho, data, etc.).
    -   `find . -name "*.txt"`: Encontra arquivos .txt no diretório atual.
-   `gzip` ➡ **Compacta** um arquivo (`gzip arquivo`).
-   `gunzip` ➡ **Descompacta** um arquivo `.gz` (`gunzip arquivo.gz`).
-   `tar` ➡ **Agrupa** vários arquivos em um único "pacote" `.tar` (um arquivador).
    -   `-c` (create): `tar -cvf pacote.tar /diretorio`
    -   `-t` (list): `tar -tvf pacote.tar`
    -   `-x` (extract): `tar -xvf pacote.tar`

## 6. Recursos do Shell (Muito Importante!)

-   **Redirecionadores**:
    -   `>`: Envia a saída de um comando para um arquivo, **sobrescrevendo** o conteúdo.
        -   `ls -l > lista.txt`
    -   `>>`: Envia a saída de um comando para um arquivo, **adicionando** ao final.
        -   `echo "Nova linha" >> lista.txt`
    -   `<`: Usa um arquivo como **entrada** para um comando.
        -   `wc -l < lista.txt`
-   **Pipe `|`**: Conecta a **saída** de um comando na **entrada** de outro.
    -   `cat arquivo.log | grep "erro" | wc -l` (Mostra o conteúdo, filtra as linhas com "erro" e conta quantas são).
-   **Metacaracteres (Globbing)**:
    -   `*`: Corresponde a **qualquer** sequência de caracteres.
    -   `?`: Corresponde a **um único** caractere.
    -   `[]`: Corresponde a **um dos caracteres** dentro dos colchetes. Ex: `arq[123].txt`.

## 7. Editor VIM (Comandos Básicos no Modo Normal)

-   `:w` ➡ **Salva** (write).
-   `:q` ➡ **Sai** (quit).
-   `:wq` ou `:x` ➡ **Salva e sai**.
-   `:q!` ➡ **Sai sem salvar** (forçado).
-   `:e <arquivo>` ➡ **Abre** um arquivo para edição.
