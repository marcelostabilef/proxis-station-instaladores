# Proxis Station — instaladores

Somente instaladores. O código-fonte não é publicado aqui.

Baixe na aba **Releases**. A mais recente é a **2.0.0-1**.

| Arquivo | Para quê |
|---|---|
| `gmp-vms-server_2.0.0-1_amd64.deb` | Servidor GMP VMS para Ubuntu 22.04, 24.04 e 26.04 (amd64) |
| `GMP.VMS_2.0.0_x64-setup.exe` | Cliente GMP VMS para Windows 10/11 (64 bits) |
| `SHA256SUMS` | Somas para conferir os arquivos |

## Servidor (Ubuntu)

```bash
sudo apt install ./gmp-vms-server_2.0.0-1_amd64.deb
```

A instalação pergunta a porta: **Porta padrão (8080)** ou **Personalizar a porta** (1024 a 65535). Se a 8080 estiver ocupada, sugere a primeira livre.

Trocar a porta depois:

```bash
sudo dpkg-reconfigure gmp-vms-server
```

Instalação sem tela com porta definida:

```bash
echo "gmp-vms-server gmp-vms-server/porta_modo select Personalizar a porta" | sudo debconf-set-selections
echo "gmp-vms-server gmp-vms-server/porta string 8081" | sudo debconf-set-selections
sudo DEBIAN_FRONTEND=noninteractive apt install -y ./gmp-vms-server_2.0.0-1_amd64.deb
```

Serviço: `gmp-vms`.

## Cliente (Windows)

Execute `GMP.VMS_2.0.0_x64-setup.exe` e adicione o servidor como `IP:porta`.
