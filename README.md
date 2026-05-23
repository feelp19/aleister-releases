# Aleister

> README do repositório **público** de downloads (`aleister-releases`).
> O código-fonte fica em um repositório privado; aqui ficam apenas os binários.

Assistente de desktop _voice-first_ para desenvolvedores. Você fala as
instruções, o Claude Code interpreta e implementa. HUD em formato de cérebro,
TTS opcional, memória conversacional. Compatível com assinatura Claude Pro/Max
(não exige API key por padrão). Aplicativo **local** — sem telemetria; nenhum
dado sai da máquina exceto chamadas às APIs cujas chaves você fornecer.

## Download

Pegue a versão mais recente em **[Releases](../../releases/latest)**:

| Sistema | Arquivo |
|---|---|
| Linux (x86-64) | `aleister-linux-amd64-<versão>.tar.gz` |
| Windows (x86-64) | `aleister-windows-amd64-<versão>.zip` |

> macOS ainda não tem build publicado.

## Instalação

### Linux

```bash
tar -xzf aleister-linux-amd64-*.tar.gz
cd aleister-linux-amd64
./run.sh                  # roda o app
./install-desktop.sh      # opcional: registra no menu de apps (sem root)
```

### Windows

1. Extraia o `.zip` em qualquer pasta.
2. Rode `run.bat` (duplo-clique ou pelo terminal).

O bundle é **portátil**: extraia onde quiser e rode. As DLLs de runtime já vão
junto.

## Requisitos na máquina

- **Node 20+** no PATH (o app usa um sidecar Node para falar com o Claude).
- **Linux:** bibliotecas do WebKit2GTK 4.1.
- **Windows:** [WebView2 Runtime](https://developer.microsoft.com/microsoft-edge/webview2/)
  (já vem no Windows 11 / Edge atual).
- **Modo offline (opcional):** `whisper-cli` + um modelo whisper.cpp + `espeak-ng`.

## Primeiro uso

A configuração acontece dentro do app:

- Nome do dono + nome do assistente
- Diretório do projeto
- Chaves Deepgram + ElevenLabs (ou ative o modo offline)

## Onde ficam seus dados

| Caminho | Conteúdo |
|---|---|
| `~/.aleister/config.json` | Configuração (as API keys ficam aqui). |
| `~/.aleister/aleister.db` | Memória SQLite (por projeto). |

Resetar memória: Settings → "Zona de risco" → "Esquecer memória" (preserva a
identidade dono/assistente).

## Aviso

Binários **não assinados**. No primeiro uso o Windows (SmartScreen) pode avisar
"editor desconhecido" — é esperado para ferramenta local de dev.
