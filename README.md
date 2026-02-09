# 🛒 E-commerce PHP Completo

[![PHP](https://img.shields.io/badge/PHP-7.4%2B-777BB4?style=for-the-badge&logo=php)](https://www.php.net/)
[![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-4479A1?style=for-the-badge&logo=mysql)](https://www.mysql.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?style=for-the-badge&logo=bootstrap)](https://getbootstrap.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

Plataforma de e-commerce profissional e escalável desenvolvida com PHP, MySQL e Bootstrap. Inclui carrinho de compras, painel administrativo completo com CRUD, sistema de pedidos, gerenciamento de inventário, integração com gateway de pagamento e muito mais.

## 🎯 Objetivo

Criar uma solução de e-commerce robusta, segura e profissional que demonstre boas práticas de desenvolvimento web, arquitetura escalável e padrões de segurança.

## ✨ Funcionalidades

### Para Clientes
- 🛍️ Catálogo dinâmico com filtros avançados
- 🔍 Sistema de busca inteligente
- 🛒 Carrinho de compras com persistência
- 💳 Integração com gateway de pagamento (Stripe/PayPal)
- 👤 Autenticação e gerenciamento de perfil
- 📦 Rastreamento de pedidos
- ⭐ Sistema de avaliações e comentários
- 📧 Notificações por email
- 📱 Design 100% responsivo

### Para Administradores
- 📊 Dashboard com estatísticas em tempo real
- 📦 Gerenciamento completo de produtos
- 📂 Categorização e organização
- 👥 Gerenciamento de usuários e permissões
- 📈 Relatórios de vendas
- 💰 Gerenciamento de pedidos
- 🚚 Integração com transportadoras
- 🔐 Controle de acesso por função
- 📧 Gerenciamento de emails

## 🛠️ Tecnologias Utilizadas

### Backend
- **PHP 7.4+** - Linguagem de programação
- **MySQL 5.7+** - Banco de dados relacional
- **PDO** - Acesso seguro ao banco
- **Session Management** - Gerenciamento de sessões
- **Email Service** - Notificações por email

### Frontend
- **HTML5** - Estrutura semântica
- **CSS3** - Estilização moderna
- **Bootstrap 5** - Framework CSS responsivo
- **JavaScript/jQuery** - Interatividade
- **AJAX** - Requisições assíncronas

### Segurança
- **Prepared Statements** - Proteção contra SQL Injection
- **Password Hashing** - Senhas seguras com bcrypt
- **CSRF Protection** - Proteção contra CSRF
- **Input Validation** - Validação de entrada
- **Output Escaping** - Escape de saída

## 📋 Pré-requisitos

- **PHP 7.4+** com extensões: PDO, MySQLi, OpenSSL
- **MySQL 5.7+** ou **MariaDB**
- **Apache/Nginx** com suporte a rewrite
- **Composer** (recomendado)
- **Git** para versionamento

## 🚀 Instalação e Setup

### 1. Clonar o Repositório

```bash
git clone https://github.com/FHPBeto/ecommerce-php-completo.git
cd ecommerce-php-completo
```

### 2. Instalar Dependências

```bash
composer install
```

### 3. Configurar Banco de Dados

```bash
# Criar banco de dados
mysql -u root -p < database/schema.sql

# Importar dados iniciais (opcional)
mysql -u root -p ecommerce < database/seeders.sql
```

### 4. Configurar Variáveis de Ambiente

```bash
cp .env.example .env
```

Editar `.env`:

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=sua_senha
DB_NAME=ecommerce

STRIPE_KEY=pk_test_...
STRIPE_SECRET=sk_test_...

MAIL_HOST=smtp.gmail.com
MAIL_PORT=587
MAIL_USER=seu_email@gmail.com
MAIL_PASSWORD=sua_senha_app
```

### 5. Iniciar Servidor

```bash
# PHP built-in server
php -S localhost:8000

# Ou usar Apache/Nginx
# Acessar: http://localhost/ecommerce-php-completo
```

## 📁 Estrutura do Projeto

```
ecommerce-php-completo/
├── app/
│   ├── controllers/         # Controladores
│   ├── models/              # Modelos de dados
│   ├── middleware/          # Middlewares
│   └── config/              # Configurações
├── public/
│   ├── index.php            # Ponto de entrada
│   ├── css/
│   ├── js/
│   └── images/
├── resources/
│   ├── views/               # Templates
│   │   ├── layouts/
│   │   ├── products/
│   │   ├── cart/
│   │   ├── orders/
│   │   └── admin/
│   └── assets/
├── database/
│   ├── schema.sql
│   ├── seeders.sql
│   └── migrations/
├── routes/
│   └── web.php              # Definição de rotas
├── vendor/                  # Dependências Composer
├── .env.example
├── .gitignore
├── .editorconfig
├── composer.json
└── README.md
```

## 🔌 API Endpoints

### Produtos

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/products` | Listar produtos |
| `GET` | `/api/products/{id}` | Detalhes do produto |
| `POST` | `/api/products` | Criar produto (admin) |
| `PUT` | `/api/products/{id}` | Atualizar produto (admin) |
| `DELETE` | `/api/products/{id}` | Deletar produto (admin) |

### Pedidos

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `GET` | `/api/orders` | Listar pedidos do usuário |
| `POST` | `/api/orders` | Criar pedido |
| `GET` | `/api/orders/{id}` | Detalhes do pedido |
| `PUT` | `/api/orders/{id}` | Atualizar status (admin) |

### Autenticação

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| `POST` | `/api/auth/register` | Registrar usuário |
| `POST` | `/api/auth/login` | Login |
| `POST` | `/api/auth/logout` | Logout |
| `GET` | `/api/auth/profile` | Perfil do usuário |

## 🗄️ Banco de Dados

### Tabelas Principais

```sql
-- Usuários
CREATE TABLE users (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(100) NOT NULL,
  email VARCHAR(100) UNIQUE NOT NULL,
  password VARCHAR(255) NOT NULL,
  role ENUM('user', 'admin') DEFAULT 'user',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Produtos
CREATE TABLE products (
  id INT PRIMARY KEY AUTO_INCREMENT,
  name VARCHAR(150) NOT NULL,
  description TEXT,
  price DECIMAL(10, 2) NOT NULL,
  stock INT DEFAULT 0,
  category_id INT,
  image VARCHAR(255),
  active BOOLEAN DEFAULT true,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (category_id) REFERENCES categories(id)
);

-- Pedidos
CREATE TABLE orders (
  id INT PRIMARY KEY AUTO_INCREMENT,
  user_id INT NOT NULL,
  total DECIMAL(10, 2) NOT NULL,
  status ENUM('pending', 'processing', 'shipped', 'delivered') DEFAULT 'pending',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  FOREIGN KEY (user_id) REFERENCES users(id)
);

-- Itens do Pedido
CREATE TABLE order_items (
  id INT PRIMARY KEY AUTO_INCREMENT,
  order_id INT NOT NULL,
  product_id INT NOT NULL,
  quantity INT NOT NULL,
  price DECIMAL(10, 2) NOT NULL,
  FOREIGN KEY (order_id) REFERENCES orders(id),
  FOREIGN KEY (product_id) REFERENCES products(id)
);
```

## 🔐 Segurança

### Implementações

- ✅ Prepared Statements contra SQL Injection
- ✅ Password Hashing com bcrypt
- ✅ Session Management seguro
- ✅ CSRF Tokens em formulários
- ✅ Input Validation
- ✅ Output Escaping
- ✅ Rate Limiting
- ✅ HTTPS enforcement

## 🧪 Testando

1. Inicie o servidor: `php -S localhost:8000`
2. Acesse: `http://localhost:8000`
3. Teste as funcionalidades:
   - Registrar novo usuário
   - Navegar pelo catálogo
   - Adicionar ao carrinho
   - Fazer checkout
   - Acessar painel admin

### Credenciais de Teste

- **Admin**: admin@example.com / admin123
- **Usuário**: user@example.com / user123

## 📚 Recursos Úteis

- [Documentação PHP](https://www.php.net/docs.php)
- [MySQL Manual](https://dev.mysql.com/doc/)
- [Bootstrap 5](https://getbootstrap.com/docs/5.0/)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [REST API Best Practices](https://restfulapi.net/)

## 🤝 Contribuindo

1. Fork o repositório
2. Crie uma branch (`git checkout -b feature/MinhaFeature`)
3. Commit (`git commit -m 'feat: descrição'`)
4. Push (`git push origin feature/MinhaFeature`)
5. Abra um Pull Request

## 📝 Licença

MIT - veja [LICENSE](LICENSE) para detalhes.

## 👤 Autor

**FHPBeto**
- GitHub: [@FHPBeto](https://github.com/FHPBeto)

## 📞 Suporte

Encontrou um problema? Abra uma [issue](https://github.com/FHPBeto/ecommerce-php-completo/issues).

---

**Desenvolvido com ❤️ como solução profissional de e-commerce**
