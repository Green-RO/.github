<div align="center">

<img src="https://github.com/Green-RO/.github/blob/main/assets/banner.svg?raw=true" alt="Green RO Banner" width="100%" />

# Green RO

### Ragnarok Online Development Server

[![Status](https://img.shields.io/badge/server-online-brightgreen?style=for-the-badge&logo=docker&logoColor=white)](https://github.com/Green-RO)
[![rAthena](https://img.shields.io/badge/rAthena-Custom_Fork-blue?style=for-the-badge)](https://github.com/Green-RO/green-emulador)
[![PacketVer](https://img.shields.io/badge/packetver-20250508-orange?style=for-the-badge)](https://github.com/Green-RO/green-emulador)

---

*Servidor privado de desenvolvimento focado em qualidade, automacao e boas praticas.*

</div>

## Sobre

Green RO e um servidor de desenvolvimento de Ragnarok Online construido do zero com infraestrutura moderna. Todo o ambiente roda em **Docker** com deploy automatizado, monitoramento completo e acesso seguro via **WireGuard VPN**.

## Arquitetura

```
                    ┌─────────────────────────────────────────┐
                    │           VPS (Ubuntu 24.04)            │
                    │                                         │
   WireGuard VPN    │  ┌─────────┐  ┌─────────┐  ┌────────┐ │
  ──────────────────┤  │  Login  │  │  Char   │  │  Map   │ │
   10.10.0.0/24     │  │  :6900  │  │  :6121  │  │  :5121 │ │
                    │  └────┬────┘  └────┬────┘  └───┬────┘ │
                    │       └────────────┼───────────┘      │
                    │               ┌────┴────┐             │
                    │               │  MySQL  │             │
                    │               │  :3306  │             │
                    │               └─────────┘             │
                    │                                         │
                    │  ┌─────────┐  ┌─────────┐  ┌────────┐ │
                    │  │ FluxCP  │  │  Nginx  │  │ Wiki.js│ │
                    │  │  (PHP)  │  │  :80    │  │  :3000 │ │
                    │  └─────────┘  └─────────┘  └────────┘ │
                    │                                         │
                    │  ┌──────────────────────────────────┐  │
                    │  │     Grafana + Prometheus + Loki   │  │
                    │  │          Monitoring Stack         │  │
                    │  └──────────────────────────────────┘  │
                    └─────────────────────────────────────────┘
```

## Repositorios

| Repo | Descricao | Stack |
|:-----|:----------|:------|
| [**green-ro**](https://github.com/Green-RO/green-ro) | Infraestrutura principal - Docker Compose, scripts de deploy, configs | `Docker` `Bash` `YAML` |
| [**green-emulador**](https://github.com/Green-RO/green-emulador) | Fork customizado do rAthena | `C++` `CMake` |
| [**green-fluxcp**](https://github.com/Green-RO/green-fluxcp) | Painel web (FluxCP) | `PHP` `HTML` |
| [**docs**](https://github.com/Green-RO/docs) | Documentacao do projeto | `Markdown` |

## Stack Tecnologica

<table>
<tr>
<td align="center" width="120">
<b>Emulador</b><br>
rAthena (C++)
</td>
<td align="center" width="120">
<b>Database</b><br>
MySQL 8.0
</td>
<td align="center" width="120">
<b>Web</b><br>
FluxCP + Nginx
</td>
<td align="center" width="120">
<b>Infra</b><br>
Docker Compose
</td>
<td align="center" width="120">
<b>Monitoring</b><br>
Grafana + Loki
</td>
<td align="center" width="120">
<b>VPN</b><br>
WireGuard
</td>
</tr>
</table>

## Quick Start

> Requer [VPN WireGuard](https://github.com/Green-RO/docs/blob/main/wireguard-setup.md) + [chave SSH](https://github.com/Green-RO/docs/blob/main/deploy.md#configurar-ssh-para-devs) configurados.

```bash
# Clone o repositorio principal
git clone https://github.com/Green-RO/green-ro.git
cd green-ro

# Verificar status do servidor
bash scripts/server.sh status

# Deploy apos alteracoes no emulador
bash scripts/deploy.sh rebuild emulador

# Tail de logs do map server
bash scripts/server.sh logs map
```

## Documentacao

Toda a documentacao esta no repo [**docs**](https://github.com/Green-RO/docs):

- [Ambiente de Desenvolvimento](https://github.com/Green-RO/docs/blob/main/ambiente-dev.md) - Setup completo para devs
- [Deploy](https://github.com/Green-RO/docs/blob/main/deploy.md) - Scripts e fluxo de deploy
- [Banco de Dados](https://github.com/Green-RO/docs/blob/main/banco-de-dados.md) - Acesso, backup, tabelas
- [WireGuard VPN](https://github.com/Green-RO/docs/blob/main/wireguard-setup.md) - Configuracao da VPN
- [Monitoramento](https://github.com/Green-RO/docs/blob/main/monitoramento.md) - Grafana, dashboards, alertas

---

<div align="center">

*Private infrastructure. All repositories are private.*

</div>
