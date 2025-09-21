# KarshikaMitra - AI-Powered Chatbot

A comprehensive, full-stack AI chatbot application built with Next.js 14, TypeScript, and modern AI models. This project integrates multiple AI providers and provides a seamless chat experience with advanced features.

## 🚀 Features

### Core Functionality
- **Multi-Model AI Support**: Integration with OpenAI GPT-4o, Claude 3.5 Sonnet, Google Gemini, and local models
- **Real-time Chat Interface**: Modern, responsive chat UI with typing indicators and message history
- **User Authentication**: Secure user registration and login with JWT tokens
- **Conversation Management**: Create, edit, and manage multiple chat conversations
- **Advanced Settings**: Customizable AI model parameters (temperature, max tokens, context window)
- **System Prompts**: Pre-built and custom system prompts for different use cases

### Technical Features
- **TypeScript**: Full type safety throughout the application
- **Modern UI**: Built with TailwindCSS and responsive design
- **State Management**: Zustand for efficient state management
- **Database Integration**: PostgreSQL with Prisma ORM
- **API Routes**: RESTful API with Next.js App Router
- **Real-time Updates**: Live chat functionality
- **File Upload**: Support for file attachments (planned)
- **Voice Input**: Voice-to-text capabilities (planned)

## 🛠️ Technology Stack

### Frontend
- **Next.js 14** with App Router
- **React 18** with TypeScript
- **TailwindCSS** for styling
- **Zustand** for state management
- **TanStack Query** for data fetching
- **Framer Motion** for animations
- **React Hook Form** with Zod validation

### Backend
- **Next.js API Routes** for backend functionality
- **Prisma ORM** for database operations
- **PostgreSQL** as the primary database
- **JWT** for authentication
- **bcryptjs** for password hashing

### AI Integration
- **OpenAI API** (GPT-4o, GPT-4o-mini)
- **Anthropic Claude** (3.5 Sonnet)
- **Google Gemini** (Pro)
- **Local Models** via Ollama (planned)

## 📦 Installation

### Prerequisites
- Node.js 18+ 
- PostgreSQL database
- OpenAI API key (or other AI model API keys)

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd karshikamitra-chatbot
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp env.example .env.local
   ```
   
   Update `.env.local` with your configuration:
   ```env
   OPENAI_API_KEY=your_openai_api_key_here
   DATABASE_URL=postgresql://username:password@localhost:5432/karshikamitra_chatbot
   JWT_SECRET=your_jwt_secret_key_here
   NEXTAUTH_SECRET=your_nextauth_secret_here
   NEXTAUTH_URL=http://localhost:3000
   ```

4. **Set up the database**
   ```bash
   npx prisma generate
   npx prisma db push
   ```

5. **Run the development server**
   ```bash
   npm run dev
   ```

6. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## 🏗️ Project Structure

```
src/
├── app/                    # Next.js App Router
│   ├── api/               # API routes
│   │   ├── auth/          # Authentication endpoints
│   │   └── chat/          # Chat functionality
│   ├── globals.css        # Global styles
│   ├── layout.tsx         # Root layout
│   └── page.tsx           # Home page
├── components/            # React components
│   ├── auth/              # Authentication components
│   ├── chat/              # Chat interface components
│   ├── layout/            # Layout components
│   └── ui/                # Reusable UI components
├── hooks/                 # Custom React hooks
├── lib/                   # Utility functions and configurations
├── store/                 # Zustand stores
├── types/                 # TypeScript type definitions
└── utils/                 # Helper functions
```

## 🔧 Configuration

### AI Model Configuration

The application supports multiple AI models with different capabilities:

- **GPT-4o**: Most capable model for complex tasks
- **GPT-4o-mini**: Faster and more cost-effective
- **Claude 3.5 Sonnet**: Advanced reasoning and analysis
- **Gemini Pro**: Google's most capable model
- **Local Models**: Privacy-focused local inference

### Database Schema

The application uses PostgreSQL with the following main entities:

- **Users**: User accounts and authentication
- **Conversations**: Chat conversation containers
- **Messages**: Individual chat messages
- **ConversationSettings**: AI model configuration per conversation
- **SystemPrompts**: Pre-built and custom system prompts
- **AIModels**: Available AI model configurations

## 🚀 Deployment

### Production Setup

1. **Environment Variables**
   Set up production environment variables:
   ```env
   DATABASE_URL=postgresql://username:password@your-production-db:5432/karshikamitra_chatbot
   OPENAI_API_KEY=your_production_openai_key
   JWT_SECRET=your_production_jwt_secret
   NEXTAUTH_SECRET=your_production_nextauth_secret
   NEXTAUTH_URL=https://your-domain.com
   ```

2. **Database Migration**
   ```bash
   npx prisma db push
   ```

3. **Build and Deploy**
   ```bash
   npm run build
   npm start
   ```

### Docker Deployment

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
```

## 🧪 Testing

### Running Tests

```bash
# Unit tests
npm test

# E2E tests
npm run test:e2e

# Type checking
npm run type-check

# Linting
npm run lint
```

### Test Coverage

The project includes comprehensive testing:

- **Unit Tests**: Component and utility function testing
- **Integration Tests**: API endpoint testing
- **E2E Tests**: Full user workflow testing
- **Type Safety**: TypeScript strict mode

## 📚 API Documentation

### Authentication Endpoints

- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/verify` - Token verification

### Chat Endpoints

- `POST /api/chat` - Send message and get AI response

### Request/Response Examples

**Send Message:**
```json
POST /api/chat
{
  "message": "Hello, how are you?",
  "conversationId": "conv_123",
  "settings": {
    "model": "gpt-4o",
    "temperature": 0.7,
    "maxTokens": 1000
  }
}
```

**Response:**
```json
{
  "message": {
    "id": "msg_456",
    "content": "Hello! I'm doing well, thank you for asking...",
    "role": "assistant",
    "timestamp": "2024-01-01T12:00:00Z",
    "conversationId": "conv_123",
    "metadata": {
      "model": "gpt-4o",
      "tokens": 150,
      "processingTime": 1200
    }
  },
  "conversationId": "conv_123",
  "usage": {
    "promptTokens": 20,
    "completionTokens": 130,
    "totalTokens": 150
  }
}
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- OpenAI for providing the GPT models
- Anthropic for Claude models
- Google for Gemini models
- The Next.js team for the amazing framework
- The React community for excellent libraries and tools

## 📞 Support

For support, email support@karshikamitra.com or join our Discord community.

---

Built with ❤️ by the KarshikaMitra Team
