# 🎵 OST Discovery & Archive Platform

> Uma plataforma moderna para descoberta, catalogação e preservação de trilhas sonoras de videogames, combinando tecnologias modernas com inteligência artificial para criar a experiência definitiva para entusiastas de Video Game Music.

[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)](https://golang.org/)
[![React](https://img.shields.io/badge/React-18+-61DAFB?style=flat&logo=react)](https://reactjs.org/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-336791?style=flat&logo=postgresql)](https://postgresql.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-6.0+-47A248?style=flat&logo=mongodb)](https://mongodb.com/)
[![Docker](https://img.shields.io/badge/Docker-24+-2496ED?style=flat&logo=docker)](https://docker.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## 🌟 **Visão Geral**

O **OST Discovery Platform** é uma aplicação fullstack que revolutiona como os fãs de videogames descobrem, organizam e preservam trilhas sonoras. Combinando um catálogo moderno com funcionalidades de arquivo histórico, a plataforma oferece:

- **🔍 Identificação de Áudio**: Upload uma música e descubra de qual jogo ela é
- **🤖 Recomendações Inteligentes**: IA que aprende seus gostos musicais
- **📚 Arquivo Histórico**: Timeline evolutiva da música em videogames
- **🎵 Playlists Inteligentes**: Criação automática baseada em mood e gênero
- **👥 Comunidade**: Reviews, ratings e playlists colaborativas
- **🔄 Comparação de Versões**: 8-bit vs remix vs orquestral side-by-side

## 🏗️ **Arquitetura**

### **Stack Tecnológico**
- **Backend**: Go 1.21+ (Microserviços)
- **Frontend**: React 18+ + TypeScript + Tailwind CSS
- **Bancos**: PostgreSQL (dados estruturados) + MongoDB (logs/IA)
- **Infraestrutura**: Docker + Docker Compose
- **IA/ML**: Python (integração via APIs) + TensorFlow/PyTorch
- **Processamento de Áudio**: Chromaprint + Librosa
- **Search**: Elasticsearch
- **Cache**: Redis
- **Gateway**: Nginx

### **Microserviços**
```
├── api-gateway/          # Roteamento e rate limiting
├── auth-service/         # Autenticação e autorização
├── catalog-service/      # Catálogo de jogos e trilhas
├── audio-service/        # Upload e processamento de áudio
├── ml-service/          # Recomendações e análise por IA
├── search-service/      # Busca avançada
├── playlist-service/    # Gerenciamento de playlists
├── user-service/        # Perfis e preferências
├── notification-service/# Notificações real-time
└── archive-service/     # Preservação e versionamento
```

## 🚀 **Funcionalidades Principais**

### **Descoberta e Identificação**
- Upload de áudio para identificação automática
- Fingerprinting avançado com alta precisão
- Busca por similaridade musical
- Integração com YouTube, Spotify e SoundCloud

### **Catálogo Inteligente**
- Database abrangente de OST's organizada por jogo, compositor, era
- Metadados ricos: BPM, tonalidade, mood, gênero
- Tags colaborativas da comunidade
- Histórico de versões e remasters

### **Arquivo e Preservação**
- Timeline interativa da evolução musical dos games
- Comparação lado-a-lado de diferentes versões
- Preservação de trilhas raras e perdidas
- Documentação histórica e cultural

### **Experiência Social**
- Sistema de reviews e ratings
- Playlists colaborativas
- Comentários com timestamps
- Achievements e gamificação

### **IA e Machine Learning**
- Recomendações personalizadas baseadas em listening behavior
- Análise automática de mood e energia
- Classificação inteligente de gêneros
- Upscaling de áudio retro

## 🛠️ **Setup de Desenvolvimento**

### **Pré-requisitos**
- Docker & Docker Compose
- Go 1.21+
- Node.js 18+
- Python 3.9+ (para ML services)

### **Instalação Rápida**

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/ost-discovery-platform.git
cd ost-discovery-platform

# Setup do ambiente
cp .env.example .env
# Edite o .env com suas configurações

# Inicie os serviços
docker-compose up -d

# Setup do frontend
cd frontend
npm install
npm run dev

# Setup dos microserviços (em terminais separados)
cd backend/auth-service && go run main.go
cd backend/catalog-service && go run main.go
# ... outros serviços
```

### **Estrutura do Projeto**
```
ost-discovery-platform/
├── backend/
│   ├── api-gateway/
│   ├── auth-service/
│   ├── catalog-service/
│   ├── audio-service/
│   ├── ml-service/
│   └── shared/              # Código compartilhado
├── frontend/
│   ├── src/
│   ├── public/
│   └── package.json
├── ml/                      # Python ML services
├── infrastructure/
│   ├── docker/
│   ├── kubernetes/
│   └── scripts/
├── docs/                    # Documentação técnica
├── data/                    # Seeds e fixtures
└── docker-compose.yml
```

## 📊 **Banco de Dados**

### **PostgreSQL Schema**
```sql
-- Principais entidades
games (id, name, year, platform, genre, developer, publisher)
composers (id, name, bio, birth_year, country)
tracks (id, game_id, name, duration, composer_id, audio_features)
users (id, username, email, preferences, created_at)
playlists (id, user_id, name, description, is_public)
```

### **MongoDB Collections**
```javascript
// Dados de IA e logs
audio_fingerprints: { track_id, fingerprint_data, algorithm }
ml_recommendations: { user_id, tracks, algorithm, timestamp }
user_behavior_logs: { user_id, action, metadata, timestamp }
audio_analysis: { track_id, bpm, key, mood, energy }
```

## 🤖 **APIs e Integrações**

### **APIs Internas**
- `GET /api/v1/tracks` - Lista trilhas com filtros
- `POST /api/v1/audio/identify` - Identifica áudio por upload
- `GET /api/v1/recommendations/{user_id}` - Recomendações personalizadas
- `POST /api/v1/playlists` - Cria playlist
- `GET /api/v1/archive/timeline` - Timeline histórica

### **APIs Externas**
- **Spotify Web API**: Integração de playlists
- **YouTube Data API**: Links para vídeos
- **Last.fm API**: Metadados musicais
- **MusicBrainz**: Informações de artistas

## 🧪 **Testes**

```bash
# Testes do backend
cd backend
go test ./...

# Testes do frontend
cd frontend
npm test

# Testes de integração
docker-compose -f docker-compose.test.yml up
```

## 📈 **Monitoramento**

- **Métricas**: Prometheus + Grafana
- **Logs**: ELK Stack (Elasticsearch, Logstash, Kibana)
- **APM**: Jaeger para tracing
- **Health Checks**: Endpoints `/health` em todos os serviços

## 🤝 **Contribuição**

1. Fork o projeto
2. Crie uma feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

Veja [CONTRIBUTING.md](CONTRIBUTING.md) para guidelines detalhadas.

## 📄 **Licença**

Este projeto está licenciado sob a MIT License - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 🙏 **Agradecimentos**

- **ostdb**: Inspiração e referência para estruturação de dados
- **OverClocked ReMix**: Comunidade e conteúdo de qualidade
- **Chromaprint/AcoustID**: Tecnologia de fingerprinting
- **Comunidade ost**: Por manter viva a paixão pela música de videogames

## 📞 **Contato**

- **Desenvolvedor**: [Seu Nome](https://github.com/seu-usuario)
- **Email**: seu.email@exemplo.com
- **LinkedIn**: [Seu LinkedIn](https://linkedin.com/in/seu-perfil)
- **Portfolio**: [Seu Site](https://seu-site.com)

---

**⭐ Se este projeto te ajudou ou te inspirou, deixe uma estrela no repositório!**

### 🎮 **Para a Comunidade Gamer**
*"A música dos videogames merece ser preservada, descoberta e celebrada. Este é nosso tributo aos compositores que criaram as trilhas sonoras da nossa infância e continuam inspirando novas gerações."*
