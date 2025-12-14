# 🛒 SmartSales AI

> **Intelligent AI-Powered Sales Assistant for Nigerian Businesses**

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.109-green.svg)](https://fastapi.tiangolo.com/)
[![Meta LLaMA](https://img.shields.io/badge/Meta-LLaMA-purple.svg)](https://ai.meta.com/llama/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

SmartSales AI is an intelligent conversational sales assistant that helps Nigerian businesses automate customer interactions, provide product recommendations, and drive sales through WhatsApp and web chat interfaces.

---

## ✨ Features

### 🤖 AI-Powered Conversations
- Natural language understanding using **Meta LLaMA** via Groq
- Context-aware responses that remember conversation history
- Intent detection for customer queries
- Product recommendations based on customer needs

### 🌍 Multi-Language Support
| Language | Code | Support Level |
|----------|------|---------------|
| English | `en` | Full |
| Nigerian Pidgin | `pcm` | Full |
| Yorùbá | `yo` | Full |
| Hausa | `ha` | Full |
| Igbo | `ig` | Full |
| Fulfulde | `ff` | Basic |
| French | `fr` | Basic |

### 📱 WhatsApp Integration
- Seamless Twilio WhatsApp Business API integration
- Automatic customer identification
- Message delivery tracking
- Rich media support (images, documents)

### 📊 Analytics Dashboard
- Real-time conversation metrics
- Language distribution insights
- Top products analysis
- Customer behavior tracking
- Intent analytics

### 🛍️ Product Management
- Full CRUD operations for products
- Category management
- Inventory tracking
- Search and filtering
- Featured products

---

## 🏗️ Architecture

```
SmartSales AI
├── 🔌 API Layer (FastAPI)
│   ├── Chat Endpoints
│   ├── Business Management
│   ├── Product Catalog
│   ├── Analytics
│   └── Webhooks (Twilio)
│
├── 🧠 AI Layer
│   ├── Sales Agent (LLaMA)
│   ├── Intent Detection
│   ├── Language Detection
│   └── Response Generation
│
├── 💾 Data Layer
│   ├── SQLAlchemy ORM
│   ├── Async Database
│   └── Models (User, Business, Product, etc.)
│
└── 🔒 Security Layer
    ├── JWT Authentication
    ├── Password Hashing
    └── Webhook Verification
```

---

## 🚀 Quick Start

### Prerequisites
- Python 3.11+
- pip or pipenv
- SQLite (development) / PostgreSQL (production)

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/smartsales-ai.git
cd smartsales-ai
```

2. **Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure environment**
```bash
cp .env.example .env
# Edit .env with your configuration
```

5. **Run the application**
```bash
uvicorn app.main:app --reload
```

6. **Access the API**
- API Documentation: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

---

## ⚙️ Configuration

Create a `.env` file in the project root:

```env
# Application
APP_NAME=SmartSales AI
ENVIRONMENT=development
DEBUG=True

# Database
DATABASE_URL=sqlite+aiosqlite:///./smartsales.db

# Security
SECRET_KEY=your-super-secret-key-change-in-production
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30

# Twilio (WhatsApp)
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_WHATSAPP_NUMBER=+14155238886

# AI Services
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile

# Language
DEFAULT_LANGUAGE=en
SUPPORTED_LANGUAGES=en,pcm,yo,ha,ig,ff,fr
```

---

## 📚 API Endpoints

### Chat
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/chat/message` | Send message and get AI response |
| POST | `/api/v1/chat/message/public/{slug}` | Public chat (no auth) |
| GET | `/api/v1/chat/conversations` | List conversations |
| GET | `/api/v1/chat/conversations/{id}/messages` | Get conversation messages |

### Business
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/businesses` | Create business |
| GET | `/api/v1/businesses/me` | Get current business |
| PATCH | `/api/v1/businesses/me` | Update business |
| GET | `/api/v1/businesses/me/stats` | Get statistics |

### Products
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/products` | List products |
| POST | `/api/v1/products` | Create product |
| GET | `/api/v1/products/{id}` | Get product |
| PATCH | `/api/v1/products/{id}` | Update product |
| DELETE | `/api/v1/products/{id}` | Delete product |

### Analytics
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/v1/analytics/dashboard` | Dashboard stats |
| GET | `/api/v1/analytics/conversations/trend` | Conversation trends |
| GET | `/api/v1/analytics/languages` | Language distribution |
| GET | `/api/v1/analytics/products/top` | Top products |

### Webhooks
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/v1/webhooks/twilio/whatsapp` | WhatsApp webhook |
| POST | `/api/v1/webhooks/twilio/status` | Delivery status |

---

## 🧪 Testing

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=app tests/

# Run specific test file
pytest tests/test_chat.py -v
```

---

## 📦 Project Structure

```
smartsales-ai/
├── app/
│   ├── __init__.py
│   ├── main.py                 # FastAPI application
│   ├── api/
│   │   └── routes/
│   │       ├── health.py       # Health checks
│   │       ├── chat.py         # Chat endpoints
│   │       ├── businesses.py   # Business management
│   │       ├── products.py     # Product catalog
│   │       ├── analytics.py    # Analytics
│   │       └── webhooks.py     # Twilio webhooks
│   ├── core/
│   │   ├── config.py           # Configuration
│   │   ├── database.py         # Database setup
│   │   ├── security.py         # Auth & security
│   │   └── exceptions.py       # Custom exceptions
│   ├── models/
│   │   ├── base.py             # Base model
│   │   ├── user.py             # User model
│   │   ├── business.py         # Business model
│   │   ├── product.py          # Product model
│   │   ├── customer.py         # Customer model
│   │   └── conversation.py     # Conversation model
│   └── agents/
│       └── sales_agent.py      # AI sales agent
├── tests/
├── .env.example
├── requirements.txt
└── README.md
```

---

## 🌟 Built With Meta AI

SmartSales AI leverages **Meta's LLaMA** large language model for:

- **Natural Language Understanding**: Understanding customer queries in multiple languages
- **Response Generation**: Creating helpful, contextual responses
- **Intent Recognition**: Identifying what customers want
- **Multilingual Support**: Handling Nigerian languages including Pidgin, Yoruba, Hausa, and Igbo

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 👥 Team

**SmartSales AI Team** - Building the future of African commerce

---

## 🙏 Acknowledgments

- [Meta AI](https://ai.meta.com/) - LLaMA language model
- [Groq](https://groq.com/) - Fast AI inference
- [FastAPI](https://fastapi.tiangolo.com/) - Modern Python web framework
- [Twilio](https://www.twilio.com/) - WhatsApp Business API

---

<p align="center">
  <b>Made with ❤️ for Nigerian Businesses</b>
</p>
