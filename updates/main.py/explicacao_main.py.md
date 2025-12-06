# Explicação de main.py

## Objetivo da mudança
Corrigir o fluxo de inicialização/encerramento do bot, removendo decoradores inexistentes em Pyrogram e controlando o ciclo de vida manualmente.

## O que mudou (resumo)
- Removidos os decoradores `@app.on_start()` e `@app.on_stop()`.
- Reorganizado `main()` para configurar credenciais, carregar handlers, iniciar o client, executar serviços de startup, ficar em idle e encerrar com serviços de shutdown.
- Execução principal agora usa `asyncio.run(main())`.

## Motivação/Contexto
Pyrogram não oferece `on_start`/`on_stop` no `Client`; isso gerava `AttributeError`. Passamos a controlar o ciclo de vida explicitamente para iniciar/aguardar/parar o bot de forma segura.
