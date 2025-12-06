# Explicação de requirements.txt

## Objetivo da mudança
Ajustar as dependências para remover o TgCrypto, que requer toolchain de compilação no Windows.

## O que mudou (resumo)
- Removido `tgcrypto` do `requirements.txt`.

## Motivação/Contexto
O TgCrypto é opcional para Pyrogram e exige Microsoft C++ Build Tools para compilar em Windows. Removendo-o, o projeto roda apenas com dependências puramente Python.
