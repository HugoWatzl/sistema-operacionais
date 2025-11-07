# Relatório: Avaliação Contínua de Sistemas Operacionais

**Instituição:** IBMEC
**Disciplina:** Sistemas Operacionais
**Código:** IBM8940
**Professor:** Luiz Fernando T. de Farias
**Semestre:** 2 de 2025
**Turma:** 8001

### Equipe Desenvolvedora
* Hugo Watzl
* Eduardo Jacob
* Lucca Barcelos

---

## 1. Descrição dos Módulos e Sub-rotinas

Nosso script foi desenvolvido de forma modular para facilitar a leitura e a manutenção. Cada funcionalidade principal do menu é uma função BASH independente, que é chamada pelo loop principal do programa.

As sub-rotinas desenvolvidas são:

### `criar_dir()`
* **Propósito:** Esta função é responsável pela criação de novos diretórios.
* **Descrição:** Ela solicita ao usuário o nome do diretório que deseja criar e, em seguida, executa o comando `mkdir`. Como um recurso adicional, a função pergunta se o usuário deseja mover este diretório recém-criado para dentro de um diretório "pai" já existente, utilizando `mv` para a operação.

### `list_dir()`
* **Propósito:** Este é o módulo mais interativo, focado em listar arquivos e diretórios.
* **Descrição:** A função guia o usuário por uma série de sub-menus para filtrar exatamente o que ele deseja ver. O usuário pode escolher:
    1.  *O quê* listar (apenas arquivos, apenas diretórios, ou ambos).
    2.  *Onde* listar (em um diretório específico ou no atual).
    3.  *Como* listar (listagem simples, detalhada, em árvore ou recursiva).
* Com base nessas escolhas, a função combina comandos como `find`, `ls` e `tree` para exibir o resultado formatado.

### `criar_arq()`
* **Propósito:** Gerenciar a criação de novos arquivos.
* **Descrição:** A função primeiro solicita um nome para o arquivo e o cria (via `touch`). Em seguida, ela oferece a opção de inserir conteúdo imediatamente. Caso o usuário aceite, o script utiliza o comando `cat` para capturar a entrada do teclado e salvá-la diretamente dentro do novo arquivo.

### `busca()`
* **Propósito:** Implementar um sistema de busca de arquivos.
* **Descrição:** Este módulo oferece duas formas de busca:
    1.  **Por Nome:** Utiliza o comando `find` para localizar arquivos que correspondam ao termo de busca. O script informa quantos arquivos foram encontrados e, caso encontre, oferece a opção de exibir o conteúdo do arquivo com `cat`.
    2.  **Por Palavra-chave:** Utiliza o comando `grep` para buscar recursivamente por uma palavra ou frase *dentro* do conteúdo dos arquivos, listando quais arquivos contêm o termo.

---

## 2. Listagem de Comandos Utilizados

Conforme solicitado, abaixo estão os principais comandos do sistema operacional usados no projeto e seus propósitos (excluindo estruturas da própria linguagem, como `if` ou `while`):

* **`mkdir`**: Usado para criar um novo diretório com o nome fornecido pelo usuário.
* **`mv`**: Usado para mover o diretório recém-criado para um diretório "pai".
* **`find`**: Comando central para as funções de listar e buscar. Foi usado para localizar arquivos e diretórios com base em critérios como tipo (`-type`), nome (`-iname`) e profundidade (`-maxdepth`).
* **`ls`**: Usado para exibir a listagem de arquivos/diretórios nos formatos simples, detalhado (`-l`) e recursivo (`-R`).
* **`tree`**: Usado como uma opção de visualização para exibir a estrutura de diretórios em formato de árvore.
* **`grep`**: Essencial para a busca por palavra-chave (`-rli`) e também usado para filtrar a saída de outros comandos na função de listagem.
* **`touch`**: Usado para criar um novo arquivo vazio com o nome especificado.
* **`cat`**: Utilizado de duas formas: para capturar a entrada do usuário e escrevê-la em um arquivo (`>`); e para exibir o conteúdo de um arquivo na tela.
* **`wc`**: Usado com a flag `-l` (contar linhas) para determinar quantos arquivos foram encontrados pelo comando `find`.
* **`date`**: Usado no cabeçalho do script para exibir a data e a hora atuais do sistema, tornando-o dinâmico.

---

## 3. Referências Utilizadas
* **GNU Bash Manual**
    * [https://www.gnu.org/software/bash/manual/bash.html](https://www.gnu.org/software/bash/manual/bash.html)

* **Material de aula**
   : Slides da matéria
