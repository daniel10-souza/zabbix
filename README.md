# zabbix
Procedimento para instalação do agente no Windows


O monitoramento de servidores e/ou estações de trabalho com MS-Windows pode ser feito através do protocolo SNMP ou através do Agente Zabbix, neste tutorial será abordada a instalação do Agente Zabbix.

OBTENDO OS ARQUIVOS:
Podemos fazer o download do agente no site do Zabbix (external link), ou copia-lo do diretório que contém os fontes de instalação do Zabbix Server, neste caso os arquivos se encontram em zabbix-versão/bin, dentro deste diretório temos 2 sub-diretórios (win32 e win64) cada um respectivo a arquitetura do seu processador, a cópia do Linux para o Windows pode ser feita através do software WinSCP (external link).
http://www.zabbix.com/download.php

INSTALAÇÃO:
Crie um diretório de nome Zabbix no C:\
Copiar ou Descompactar os arquivos, para o diretório criado.
Alterar o arquivo de configuração ("zabbix_agentd.conf")que está na pasta conf.


CONTEÚDO MÍNIMO DO ARQUIVO ZABBIX_AGENTD.CONF:
Server=IP do Servidor do Zabbix

EnableRemoteCommands=1
LogRemoteCommands=1
Server="IP do servidor do Zabbix"
StartAgents=5
ServerActive="IP do servidor do Zabbix"
HostnameItem=system.hostname
Timeout=5
DebugLevel=3

LogFile=c:\Zabbix\zabbix_agentd.log
Timeout=3

CRIANDO UM SERVIÇO ZABBIX AGENT NO WINDOWS:
Abrir um prompt de comando de forma administrador e executar o seguinte comando:
-------Para Windows 32bits executar este comando----------
C:\Zabbix\bin\w32\zabbix_agentd.exe -i -c C:\Zabbix\zabbix_agentd.conf

-------Para Windows 64bits executar este comando----------
C:\Zabbix\bin\w64\zabbix_agentd.exe -i -c C:\Zabbix\zabbix_agentd.conf


Se tudo ocorreu bem você recebera as mensagens:
zabbix_agentd.exe [1540]: Service "ZABBIX Agent" installed successfully.
zabbix_agentd.exe [1540]: Event source "ZABBIX Agent" installed successfully.

Ver o arquivo de Log do zabbix se ocorreu tudo certo no caminho:
C:\Zabbix

VERIFICANDO O STATUS DO SERVIÇO DO ZABBIX:
Iniciar // Painel de Controle // Ferramentas administrativas // Serviços:

VERIFICANDO AS PROPRIEDADES DO SERVIÇO:
Duplo clique em ZABBIX Agent

REMOVENDO O SERVIÇO:
Abrir um prompt de comando e executar o seguinte comando:
C:\Zabbix\zabbix_agentd.exe -d -c C:\Zabbix\zabbix_agentd.conf


Se tudo ocorreu bem você recebera as mensagens:
zabbix_agentd.exe [4156]: Service "ZABBIX Agent" uninstalled successfully.
zabbix_agentd.exe [4156]: Event source "ZABBIX Agent" uninstalled successfully.

Criado por: Daniel Souza
