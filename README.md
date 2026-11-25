# Proxis Station — instaladores

Somente instaladores. O código-fonte não é publicado aqui.

Baixe na aba **Releases**. A mais recente é a **2.1.0**.

| Arquivo | Para quê |
|---|---|
| `proxis-station-server_2.1.0_amd64.deb` | Servidor que **convive** com o gmp-vms 1.x na mesma máquina (Ubuntu 24.04 e 26.04) |
| `gmp-vms-server_2.1.0_amd64.deb` | Servidor GMP VMS que **substitui** o gmp-vms (atualiza) — Ubuntu 22.04, 24.04 e 26.04 |
| `GMP.VMS_2.0.0_x64-setup.exe` | Cliente GMP VMS para Windows 10/11 (64 bits) |
| `SHA256SUMS` | Somas para conferir os arquivos |

## Qual servidor usar

- **Máquina que já tem o gmp-vms e ele deve continuar rodando:** `proxis-station-server`. Pastas e serviço próprios (`/etc/proxis-station`, `/var/lib/proxis-station`, serviço `proxis-station`). Com a 8080 ocupada, a instalação sugere a 8081.
- **Máquina nova, ou trocar o gmp-vms pela 2.x:** `gmp-vms-server`. Usa o banco do gmp-vms existente.

```bash
sudo apt install ./proxis-station-server_2.1.0_amd64.deb
```

## Porta

A instalação pergunta: **Porta padrão (8080)** ou **Personalizar a porta** (1024 a 65535).

Trocar depois:

```bash
sudo dpkg-reconfigure proxis-station-server
```

Instalação sem tela com porta definida:

```bash
echo "proxis-station-server proxis-station-server/porta_modo select Personalizar a porta" | sudo debconf-set-selections
echo "proxis-station-server proxis-station-server/porta string 8081" | sudo debconf-set-selections
sudo DEBIAN_FRONTEND=noninteractive apt install -y ./proxis-station-server_2.1.0_amd64.deb
```

Para o `gmp-vms-server`, troque o nome do pacote nos comandos.

## Cliente (Windows)

Execute `GMP.VMS_2.0.0_x64-setup.exe` e adicione o servidor como `IP:porta`.
