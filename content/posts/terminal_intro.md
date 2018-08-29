---
author: "tala1m"
date: 2018-08-07
linktitle: Introdução ao Terminal
title: Guia Introdutório ao Terminal do Linux
categories: ["ENIGMA"]
tags: ["arquivo"]
weight: 1
description: Uma visão geral sobre alguns programas úteis do terminal do Linux para ações offline e uma breve passada por curl e wget. Aumente o seu potencial com o famigerado verde no preto, afinal quem precisa de interface gráfica?
---

# 0 - Acesso e controle aos diretórios
## 0.0 - `help` e `man`
Lista de comandos e manuais de referência

## 0.1 - `pwd`
Mostra o **caminho** para o diretório atual

## 0.2 - `ls`
Mostra o conteúdo do caminho especificado (padrão: diretório atual).
-a e -A : mostra até ocultos, mas o segundo ignora link para pasta atual e superior

## 0.3 - `mkdir`
Cria diretórios
-p: Cria o caminho se inexistente

## 0.4 - `cd`, `pushd` e `popd`
Navegação em diretórios

## 0.5 - `touch`
Altera a data de modificação ou acesso de um arquivo (útil para criar um arquivo vazio)

## 0.6 - `vim` e `nano`
Editores

# 1 - Bash
## 1.1 - Variáveis
- $?: Último reusltado
- $1..9: Parâmetros

## 1.1.1 - `export` (Escopo)

## 1.1.2 - `(( ))` (Operações aritméticas)

## 1.2 - Entrada e saída de texto
### 1.2.1 - `read`
Preenche uma variável com um valor digitado pelo usuário
`-s`: oculta os caracteres
`-p`: exibe um texto antes do prompt

### 1.2.2 - `echo`
Escrever no destino definido, seja arquivo ou terminal
-n: não quebra linha
-e: Interpreta caracteres especiais

### 1.2.3 - `|` (pipe)
Redireciona a saída de um comando para o seguinte

### 1.2.4 - `>` e `>>` (redirecionamento de saída)
Define um destinatário para a saída de um comando

### 1.3 - Condição
http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html
### 1.3.1 - `[ ]` e `test`

### 1.3.2 - `[[ ]]`

### 1.4 - Loop
```
while [ CONDIÇÂO ]
do
    COMANDOS
done
```

```
for i in $( COMANDO ); do
    COMANDOS
done
```

### 1.4.1 - `seq`
Exibe um sequência de números


### 1.5 - Função
function FUNCNAME {
    echo $1
    exit
} 

### 1.6 - Tratamento de string
${stringZ:7:3}

## 2 - Programas úteis
### 2.1 - `cat`, `head`, `tail`

### 2.2 - `grep`
Busca termos em arquivos

### 2.3 - `find`
Busca de arquivos

### 2.4 - `strings`
Exibe as strings de um arquivo (mesmo que este esteja codificado como binário)

### 2.5 - `ps` e `top`
Exibem os programas em execução

### 2.6 - `awk` e `sed`


### 2.7 - `wget` e `curl`
Realiza requisições http

                
# 3 - Prática
## 3.1 - Matrioska
Loop de unzip
- Baixe `wget https://decifre.me/static/chall_3/y6gvj84cuyxe0tsm.zip`
- Loop `while [ -e *.zip ]; do unzip *.zip -d aux > /dev/null; rm *.zip; mv aux/*.zip .; done`
- Uma busca contextualizada `grep -a -o -P 'enigma.{0,20}' y6gvj84cuyxe0tsm.zip`
- Combinando ferramentas `strings y6gvj84cuyxe0tsm.zip | grep enigma`

## 3.2 - Ta falando grego?
Recebe uma sequência de caracteres S e um número N. Rotaciona cada caractere de S em N letras do alfabeto.
https://decifre.me/static/chall_2/6kjpiekfaamx5c8o.html

## 3.3 - Comunicação Insegura
Faz um _post request_ para a URL presente no código da página com o parâmetro certo.
- Acesse a página do desafio http://67.205.128.230/75E735706CC02C7DD078DDFEE601FB8BFD13C21A3D4DBB81BB110D4178F6093A/
- Procure o script no código da página 
- Pegue a flag com `wget http://67.205.128.230/75E735706CC02C7DD078DDFEE601FB8BFD13C21A3D4DBB81BB110D4178F6093A/api.php --post-data "op=getflag"`