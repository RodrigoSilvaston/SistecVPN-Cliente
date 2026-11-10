SistecVPN

Sistema Corporativo de VPN Mesh Blindada com Criptografia E2EE S3ON, QoS e SQLite Criptografado  

Desenvolvido por Rodrigo B. Silvaston para a Sistec Soluções em TI.

🛡️ Arquitetura de Segurança e Desempenho

1. Topologia Híbrida Mesh P2P Criptografada (Escala para 500+ Nós):
- Rota direta E2EE entre nós remotos via NAT Hole-Punching STUN automático.
- 0 Gbps consumidos no link do servidor central para tráfego P2P direto, eliminando travamentos de servidor em transferências pesadas.
- Fallback automático e transparente para Relay Centralizado com Token Bucket QoS caso um cliente esteja sob NAT Simétrico restrito.

2. Criptografia S3ON (3-Hop Onion Routing):
- 3 camadas sucessivas de encapsulamento criptográfico com verificação de integridade via HMAC-SHA256 (S3ON).
- Salto 1 (Ingress Guard) ➔ Salto 2 (Middle Shuffler) ➔ Salto 3 (Egress Target).

3. Janela Deslizante Anti-Replay (RFC 4303):
- Bitmap de 64 pacotes com contadores monotônicos de 64 bits. Descarta instantaneamente pacotes duplicados, fora de ordem ou retransmitidos por invasores.

4. Controle de Banda e Modelagem de Tráfego (QoS Token Bucket):
- Taxa sustentada de 200 Mbps com burst buffer de 400 Mbps por estação para evitar saturação e congelamento de links.

5. Mitigação Anti-Ransomware e Isolamento Lateral:
- Bloqueio automático de portas NetBIOS (137-139 TCP/UDP) na interface virtual, impedindo infecções cruzadas tipo WannaCry pela VPN.

6. TCP MSS Clamping (1360 bytes):
- Elimina fragmentação de MTU e pacotes perdidos em redes 4G/5G, Wi-Fi e conexões PPPoE.

7. Sub-rede Virtual Segura e Stealth Gateway:
- Endereçamento corporativo seguro estruturado em faixas privadas (RFC 6598 / RFC 1918) com isolamento estrito de broadcast.
- O endereço virtual do Servidor Central é estritamente invisível e inacessível para clientes.
- Qualquer tentativa de varredura de portas (Nmap), ping (ICMP) ou exploit direcionado ao gateway sofre DROP silencioso total no Kernel/Driver e no Firewall antes de atingir o servidor.

8. Banco de Dados Embarcado com Criptografia Avançada:
- SQLite em WebAssembly (sql.js) cifrado em disco via AES-256-GCM + PBKDF2 (100.000 iterações) (.db.enc).
- Zero arquivos de credenciais ou dados sensíveis em texto plano.

🔗 Repositórios Oficiais
- SistecVPN Cliente: https://github.com/RodrigoSilvaston/SistecVPN-Cliente
- SistecVPN Server: https://github.com/RodrigoSilvaston/SistecVPN-Server

📦 Pacotes e Instaladores Disponíveis

1. Para Estações de Trabalho (Clientes) — Instaladores para Clientes/
- Windows: SistecVPN-Client-Setup-x64.exe (ou SistecVPN-Setup-x64.exe)
  Instalador Inno Setup 64-bit inteligente com suporte a Atualizar, Reparar, Desinstalar ou Bloqueio de Downgrade.
  Driver Wintun de alta performance e serviço nativo em C# (sistecvpn-adapter.exe).
- Linux: SistecVPN-Client-2.2.0-linux-x64.tar.xz
  Pacote completo com script install.sh autônomo.
  Detecta o gerenciador de pacotes (apt, dnf, pacman, zypper) e instala automaticamente dependências de sistema (iproute2, iptables, python3, bibliotecas GTK/NSS).
- macOS: SistecVPN-Client-2.2.0-mac-x64.zip
  Pacote .zip contendo o aplicativo SistecVPN.app e script install.sh para instalação e liberação de quarentena Gatekeeper.
- Linux Headless: sistecvpn-client-headless-2.2.0-linux-x64.tar.xz
  Cliente CLI para servidores sem interface gráfica.

2. Para o Servidor Central — Instaladores para Servidor/
- Windows: SistecVPN-Server-Setup-x64.exe
  Painel de Monitoramento do Servidor com liberação automática de firewall.
- Linux: SistecVPN-Server-2.2.0-linux-x64.tar.xz
  Painel de Monitoramento com script install.sh autônomo.
- macOS: SistecVPN-Server-2.2.0-mac-x64.zip
  Aplicativo e script install.sh.
- Linux Headless VPS: sistecvpn-server-headless-2.2.0-linux-x64.tar.xz
  Modo Daemon com integração nativa ao systemd (systemctl start sistecvpn-server) e console interativo estilo HTOP.

🌐 Portas de Rede do Servidor
- Porta 51820 | TCP | API REST de Sinalização, Autenticação de Salas e IPAM
- Porta 3478  | UDP | Descoberta de NAT e Diagnóstico de Rede
- Porta 51821 | UDP | Roteamento Blindado Layer 3 (Túnel 3-Hop Onion)
