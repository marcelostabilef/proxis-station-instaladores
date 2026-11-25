# Proxis Station — instaladores

Somente instaladores. O código-fonte não é publicado aqui.

Baixe na aba **Releases**. A mais recente é a **2.2.0**.

| Arquivo | Para quê |
|---|---|
| `ProxisStation-Servidor-2.2.0-Setup.exe` | Servidor Windows que **convive** com o stream163-vms na mesma máquina |
| `proxis-station-server_2.1.0_amd64.deb` | Servidor Linux que **convive** com o gmp-vms 1.x (Ubuntu 24.04 e 26.04) |
| `gmp-vms-server_2.1.0_amd64.deb` | Servidor Linux GMP VMS que **substitui** o gmp-vms (atualiza) — Ubuntu 22.04, 24.04 e 26.04 |
| `GMP.VMS_2.0.0_x64-setup.exe` | Cliente GMP VMS para Windows 10/11 (64 bits) |
| `SHA256SUMS` | Somas para conferir os arquivos |

## Servidor Windows

Execute `ProxisStation-Servidor-2.2.0-Setup.exe` como administrador. Serviço `ProxisStation`, programa em `C:\Program Files\Proxis Station`, dados em `C:\ProgramData\ProxisStation`.

A instalação pergunta a porta: **Porta padrão (8080)** ou **Personalizar a porta**. Com a 8080 ocupada (por exemplo, pelo stream163-vms), sugere a primeira livre. Instalação silenciosa:

```
ProxisStation-Servidor-2.2.0-Setup.exe /S /PORTA=8081
```

## Servidor Linux

- **Máquina que já tem o gmp-vms e ele deve continuar rodando:** `proxis-station-server`. Com a 8080 ocupada, sugere a 8081.
- **Máquina nova, ou trocar o gmp-vms pela 2.x:** `gmp-vms-server`. Usa o banco do gmp-vms existente.

```bash
sudo apt install ./proxis-station-server_2.1.0_amd64.deb
```

A instalação pergunta a porta. Trocar depois: `sudo dpkg-reconfigure proxis-station-server`.

Instalação sem tela com porta definida:

```bash
echo "proxis-station-server proxis-station-server/porta_modo select Personalizar a porta" | sudo debconf-set-selections
echo "proxis-station-server proxis-station-server/porta string 8081" | sudo debconf-set-selections
sudo DEBIAN_FRONTEND=noninteractive apt install -y ./proxis-station-server_2.1.0_amd64.deb
```

Para o `gmp-vms-server`, troque o nome do pacote nos comandos.

## Cliente (Windows)

Execute `GMP.VMS_2.0.0_x64-setup.exe` e adicione o servidor como `IP:porta`.
