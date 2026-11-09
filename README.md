SistecVPN Server — Central de Coordenação & Relay

Software de redes privadas para comunicação LAN VPN feito por Rodrigo B. Silvaston para Sistec Soluções em TI.

O SistecVPN Server é o servidor central de autoridade responsável por autenticar salas privadas, distribuir endereços IP virtuais únicos (`172.27.7.0/24`) e intermediar a comunicação P2P e Relay entre os clientes SistecVPN.

Principais Funções

- Autoridade de IP (IPAM): Garante que cada cliente receba um IP exclusivo na sub-rede `172.27.7.0/24`.
- Gerenciamento de Redes Privadas: Criação, listagem e exclusão de salas em tempo real pelo painel administrativo.
- Controle de Dispositivos: Visualização de clientes online e desconexão/expulsão imediata de máquinas.
- Sinalização P2P + Relay Integrado: Coordena túneis diretos via STUN e encaminha pacotes via Relay UDP quando necessário.
- Persistência Segura: Banco de dados SQLite criptografado em disco com AES-256-GCM.
- Atualização Automática: Verifica novas versões diretamente no GitHub Releases.

Portas Utilizadas

Certifique-se de que as seguintes portas estejam liberadas no firewall/roteador do servidor:

| Porta | Protocolo | Serviço |
| `51820` | `TCP` | Sinalização REST, Autenticação de Salas e IPAM |
| `3478` | `UDP` | STUN NAT Traversal |
| `51821` | `UDP` | Relay Fallback (Encaminhamento de pacotes VPN) |

Como Instalar

1. Baixe e execute o instalador `SistecVPN-Server-Setup-x64.exe` (disponível na aba [Releases](https://github.com/RodrigoSilvaston/SistecVPN-Server/releases)).
2. O instalador configurará automaticamente as regras do Windows Firewall e abrirá o painel do servidor.
3. Copie o IP Público ou IP Local exibido no painel e informe-o nas configurações dos clientes SistecVPN.

Desenvolvido por Rodrigo B. Silvaston — Sistec Soluções em TI
