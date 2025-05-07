# understanding_compilation_process

## Descrição

Este projeto foi feito para entender como uma linguagem de alto nível como C se torna código binário, explicando cada etapa desse processo.

## Introdução

Para compilarmos um código C para código binário, o comando mais comum é:

```sh
gcc main.c -o main
```

Mas vamos entender internamente o que ocorre quando esse comando é executado.

## Etapas do Processo de Compilação

### 🔹 1. Pré-processamento

- Gera o arquivo intermediário **`main.i`**, realizando transformações como inclusão
de arquivos (#include), expansão de macros (#define) e remoção de comentários.

Para inspecionar o arquivo gerado:

```sh
gcc -E main.c -o main.i
```

![main.i](https://raw.githubusercontent.com/gheysiell/images/main/understanding_compilation_proccess.i.png)

---

### 🔹 2. Compilação

- O arquivo **`main.i`** é então convertido para código Assembly **`main.s`**.

Para inspecionar o arquivo gerado:

```sh
gcc -S main.c -o main.s
```

![main.s](https://raw.githubusercontent.com/gheysiell/images/main/understanding_compilation_proccess.s.png)

---

### 🔹 3. Montagem

- O arquivo **`main.s`** é convertido para código binário gerando um arquivo de objeto **`main.o`**.
- O arquivo **`main.o`** contém binário, mas ainda não é executável, pois ainda não passou pelo Linker, que
  no caso é a próxima etapa.

Para inspecionar o arquivo gerado:

```sh
gcc -c main.c -o main.o
```

![main.o](https://raw.githubusercontent.com/gheysiell/images/main/understanding_compilation_proccess.o.png)

---

### 🔹 4. Linkagem

- Vinculações de chamadas de funções são feitas.
- Código extra é adicionado para inicialização e finalização do programa.
- Gera o executável final **`main`**.

Para inspecionar o arquivo gerado:

```sh
gcc main.o -o main
```

![main.exe](https://raw.githubusercontent.com/gheysiell/images/main/understanding_compilation_proccess.exe.png)

---

## Conclusão

Esse fluxo mostra como um código-fonte C é transformado em um programa executável. Com isso, é possível entender melhor cada etapa do processo de compilação.
