# privatebin-upload-skill

A skill that uploads content to any [PrivateBin](https://privatebin.info/) instance and returns a shareable link.

## Requirements

- `privatebin` CLI (see [Install CLI](#install-cli) below)
- A PrivateBin instance (default: `https://privatebin.net`, or self-hosted)

---

## Install CLI

Install `privatebin-cli` first:

| OS                        | Command                                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| **macOS**           | `brew install privatebin-cli`                                                                   |
| **Arch Linux**      | `yay -Sy privatebin-cli` (or `privatebin-cli-bin`)                                            |
| **Ubuntu / Debian** | `apt install privatebin-cli`                                                                    |
| **Prebuilt**        | [Download from releases](https://github.com/gearnode/privatebin/releases/latest)                     |
| **Source**          | `git clone https://github.com/gearnode/privatebin.git && cd privatebin && make && make install` |

### Configure

```bash
# Default (privatebin.net)
privatebin init

# Custom host
privatebin init --host https://bin.example.com

# Force overwrite
privatebin init --host https://bin.example.com --force
```

### Config file: `~/.config/privatebin/config.json`

```json
{
  "bin": [{ "name": "mybin", "host": "https://bin.example.com" }],
  "expire": "1day",
  "formatter": "plaintext",
  "gzip": true
}
```

### Multiple instances

```json
{
  "bin": [
    { "name": "mybin", "host": "https://privatebin.net" },
    { "name": "work", "host": "https://bin.example.com" }
  ]
}
```

Use with `--bin=work` flag.

### Verify installation

```bash
privatebin --version
privatebin create --help 2>&1 | head -1
```

---

## Usage

Trigger naturally in conversation:

```
"Upload the report I just generated to paste"
"Upload this script and get a shareable link"
"Share this file with my colleague, expire in one week"
"Upload the report, burn after reading"
"Upload this code with password protection"
"Upload this file to my work instance"
```

---

## Options

| Option                   | Values                                                | Default   |
| ------------------------ | ----------------------------------------------------- | --------- |
| `--expire`             | 5min, 10min, 1hour, 1day, 1week, 1month, 1year, never | 1day      |
| `--formatter`          | plaintext, markdown, syntaxhighlighting               | plaintext |
| `--burn-after-reading` | —                                                    | off       |
| `--open-discussion`    | —                                                    | off       |
| `--password`           | any string                                            | none      |
| `--gzip`               | —                                                    | off       |
| `--attachment`         | —                                                    | off       |
| `--bin` *(global)*   | named instance from config                            | default   |
| `--proxy` *(global)* | http/https/socks5 URL                                 | none      |

---

## Skill Definition

Agent instructions are in [SKILL.md](SKILL.md).

## License

MIT
