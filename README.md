# Necessario para rodar:

Instalar Docker e Docker compose.

# Construa a imagem do Docker usando o seguinte comando:

    sudo docker build -t mydatabase .

# Execute o seguinte comando para iniciar um novo container usando a imagem que acabou de criar:

    sudo docker run --name db -p 5432:5432 mydatabase

# Importando Pool no projeto Node.js, para fazer conecção com o container:

import { Pool } from 'pg';

const pool = new Pool({
  user: 'postgres',
  password: '123',
  host: 'localhost',
  database: 'mydatabase',
  port: 5432,
});

pool.query('SELECT * FROM users', (err, res) => {
  if (err) {
    console.error('Erro ao conectar ao banco de dados:', err);
  } else {
    console.log('Conexão bem-sucedida:', res.rows);
  }
  pool.end();
});

# Apagar containers

    sudo docker rmi <container-name> -f

# Limpar rastros do container

    sudo docker system prune

# Verificar Conteiners em execução

    sudo docker ps

# Verificar containers criados

    sudo docker images
