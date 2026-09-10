# laptics-releases

Repo de distribuição do Laptics Capture. Não tem código: só o `version.json`
que o app instalado lê para auto-update, e os binários publicados como GitHub
Releases (`LapticsCapture_vX.exe`, `LapticsUpdater_vX.exe`, `LapticsApply_vX.exe`).

## Quem escreve aqui

Só o CI do `deltacoach-capture` (`.github/workflows/release.yml`), com o
secret `RELEASES_TOKEN`. Ele roda a cada push na main do capture, compara
`APP_VERSION` de `config.py` com o `version.json` daqui e, se a versão for
nova e os dois baterem, builda o `.exe`, cria a Release com a tag `vX.Y.Z` e
commita o `version.json` novo ("release: bump version.json para vX (via CI)").

Sem bump de versão no capture, o workflow roda e não publica nada. Merge só de
docs no capture não gera release.

## Armadilhas conhecidas

- Nunca edite `version.json` à mão: o app lê `url`, `updater_url` e
  `apply_url` daqui e um caminho errado quebra o auto-update de todo mundo.
- As notas de release vêm em dois idiomas (`notes` e `notas`) e são o texto
  que o piloto vê na tela de atualização. Quem escreve é o PR do capture.
- O `LapticsSetup.exe` na raiz é o instalador antigo de julho; a distribuição
  real é pelas Releases.
- As tags locais podem estar atrás das remotas: `git fetch --tags` antes de
  olhar qual é a última.

## Ecossistema

Mapa dos repos, acessos e regras de trabalho: `../CLAUDE.md` (laptics-workspace).
