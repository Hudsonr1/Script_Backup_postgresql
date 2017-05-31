Script para realizar o backup e restaurar o backup do Postgresql

Iniciando o codigo

use um editor de texto VIM ou GEDIT

<pre>#!/bin/bash</pre> 

Conectando ao banco de dados
<pre>data=date "+%Y%m%d-%H:%M" usuario=postgres host=localhost banco=postgre senha=1234 restaurar=postgre testar= bancoParaTestar </pre>

Excluir o bancoParaTestar
<pre>su - postgres </pre>

Realizar Backup do banco de dados
<pre>psql -c dropdb $teste </pre>

Criar banco teste e restaurando Backup do banco de dados.</pre>
<pre>pg_dump -h localhost -p 5432 -U postgres -v -f "/backup/$data.dbserver.sql" 

<pre>psql -c createdb $teste</pre>

Compactar o Backup do banco de dados
<pre>pg_restore -U $usuario -h $host -d $teste /backup/$data.dbserver.sql</pre>
 
Apagar arquivos
<pre>tar -zcf /backup/compactado/$data.dbserversql.tar /backup/$data.dbserver.sql </pre>

Criar uma pasta de log p/ backups, acrescentando a data
<pre>rm -rf /backup/$data.dbserver.sql </pre>

<pre>$data >>/var/log/backup.log</pre>
