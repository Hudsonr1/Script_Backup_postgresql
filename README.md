Script para realizar o backup e restaurar o backup do Postgresql

Iniciando o codigo

use um editor de texto VIM ou GEDIT

<pre>
#!/bin/bash

Conectando ao banco de dados
data=date "+%Y%m%d-%H:%M" usuario=postgres host=localhost banco=postgre senha=1234 restaurar=postgre testar= bancoParaTestar 

Excluir o bancoParaTestar
su - postgres 

Realizar Backup do banco de dados
psql -c dropdb $testar 

Criar banco teste e restaurando Backup do banco de dados.</pre>
pg_dump -h localhost -p 5432 -U postgres -v -f "/backup/$data.dbserver.sql" 

psql -c createdb $testar

Compactar o Backup do banco de dados
pg_restore -U $usuario -h $host -d $testar /backup/$data.dbserver.sql
 
Apagar arquivos
tar -zcf /backup/compactado/$data.dbserversql.tar /backup/$data.dbserver.sql 

Criar uma pasta de log p/ backups, acrescentando a data
rm -rf /backup/$data.dbserver.sql 

$data >>/var/log/backup.log
</pre>
