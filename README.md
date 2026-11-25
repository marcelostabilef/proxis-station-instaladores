# Proxis Station — instaladores

Somente instaladores. O código-fonte não é publicado aqui.

Baixe na aba **Releases**.

## 2.0.0

| Arquivo | Para quê |
|---|---|
| `gmp-vms-server_2.0.0_amd64.deb` | Servidor GMP VMS para Ubuntu 22.04, 24.04 e 26.04 (amd64) |
| `GMP.VMS_2.0.0_x64-setup.exe` | Cliente GMP VMS para Windows 10/11 (64 bits) |
| `SHA256SUMS` | Somas para conferir os arquivos |

### Servidor (Ubuntu)

```bash
sudo apt install ./gmp-vms-server_2.0.0_amd64.deb
```

Serviço `gmp-vms`, porta 8080.

### Cliente (Windows)

Execute `GMP.VMS_2.0.0_x64-setup.exe`.
