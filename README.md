SistecVPN Cliente — Enterprise LAN VPN

Software de redes privadas para comunicação LAN VPN feito por Rodrigo B. Silvaston para Sistec Soluções em TI.

O SistecVPN Cliente conecta computadores remotos em uma rede local privada (`172.27.7.0/24`), permitindo acesso direto a sistemas internos, pastas compartilhadas, impressoras, bancos de dados e Área de Trabalho Remota (RDP) com baixa latência.

Principais Recursos

- Adaptador Virtual Layer 3 (Wintun): Comunicação real de rede IP entre todas as máquinas da mesma sala.
- IP Fixo por Máquina: Endereço IP virtual (`172.27.7.x`) gerenciado pelo Servidor SistecVPN, evitando conflitos de IP.
- Salas Privadas com Senha: Isolamento de redes por empresa, setor ou filial.
- Execução em Segundo Plano: Permanece ativo na bandeja do sistema (ao lado do relógio) com inicialização automática no Windows.
- Banco Local Criptografado: Configurações e credenciais protegidas com AES-256-GCM.
- Atualização Automática: Verifica novas versões diretamente no GitHub Releases.

Como Instalar e Usar

1. Baixe e execute o instalador `SistecVPN-Client-Setup-x64.exe` (disponível na aba [Releases](https://github.com/RodrigoSilvaston/SistecVPN-Cliente/releases)).
2. Abra o SistecVPN e clique no ícone de Configurações (⚙️) para informar o IP ou domínio do seu SistecVPN Server (porta padrão `51820`).
3. Ative a chave Conectado à Rede para receber seu IP virtual.
4. Clique em Criar Rede ou Entrar em Rede, informe o nome da sala e a senha.

Requisitos do Sistema

- Windows: Windows 10 / 11 ou Windows Server (64 bits) — *Executável com privilégios de Administrador para criação do adaptador virtual*.
- Linux / macOS: Pacotes `.deb`, `.rpm`, `.tar.gz` e `.dmg` disponíveis nos pacotes multiplataforma.

Desenvolvido por Rodrigo B. Silvaston — Sistec Soluções em TI

