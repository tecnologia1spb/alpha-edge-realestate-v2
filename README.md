# 🏢 Alpha Edge Real Estate Dashboard v1.3.0

> Dashboard Avançado de Análise de Portfólio Imobiliário com IA

Sistema completo de gestão e análise de performance de shopping centers, desenvolvido com **React TypeScript** + **Tremor UI** + **Supabase**, featuring **insights automáticos com Inteligência Artificial**.

## ✨ Features Principais

### 📊 Dashboards Modernos
- **Overview Dashboard**: KPIs consolidados + Alpha Intelligence Signals
- **Dashboard Financeiro**: NOI, fluxo de caixa, indicadores de performance  
- **Dashboard de Inadimplência**: Análise de risco + estratégias de recovery
- **Dashboard Orçamentário**: Controle de execução + análise de fornecedores

### 🤖 Inteligência Artificial Integrada
- **Framework AVA** (@antv/ava): Insights automáticos em português
- **Detecção automática** de tendências, anomalias e correlações
- **Recomendações inteligentes** baseadas em padrões históricos
- **Confidence scoring** para validação de insights

### ⚡ Performance & UX
- **Web Workers** para cálculos não-bloqueantes
- **Tremor UI v3.18.7** (biblioteca Vercel) para gráficos financeiros
- **Design responsivo** mobile-first
- **Formatação brasileira** completa (R$, datas, porcentagens)

## 🛠️ Tech Stack

- **Frontend**: React 18, TypeScript, Vite
- **UI Library**: Tremor UI v3.18.7 (Vercel)
- **Styling**: Tailwind CSS v4 + Custom Theme
- **Database**: Supabase (PostgreSQL)
- **State Management**: TanStack Query v5
- **Validation**: Zod + React Hook Form
- **Build Tool**: Vite with SWC
- **Quality**: ESLint + Husky + Lint-staged

## 🗂️ Estrutura do Projeto

```
src/
├── components/
│   ├── ui/            # Tremor UI components customizados
│   │   ├── KpiCard.tsx         # 3 variants (default, mini, comparative)
│   │   ├── ChartCard.tsx       # Wrapper universal para gráficos
│   │   ├── CategoryBarCard.tsx # Progress bars financeiros
│   │   └── FinancialTooltip.tsx# Tooltips contextuais brasileiros
│   ├── Dashboard/     # Views principais dos dashboards
│   └── Layout/        # Navbar, Sidebar, Navigation
├── hooks/             # Custom React hooks
│   ├── useFinancialData.ts    # Dados Supabase + validação
│   ├── useFinancialAnalytics.ts # Web Worker integration
│   └── useFinancialInsights.ts # AVA AI insights
├── workers/           # Web Workers para performance
│   └── analytics.worker.ts    # Cálculos financeiros pesados
├── lib/              # Utilities & helpers
│   ├── formatters.ts         # Formatação brasileira
│   ├── utils.ts             # Tremor + helpers
│   └── errorTracking.ts     # Sistema de logs
└── integrations/supabase/   # Cliente e tipos Supabase
```

## 🗄️ Integração Supabase

### Configuração
```env
VITE_SUPABASE_URL=https://vdhxtlnadjejyyydmlit.supabase.co
VITE_SUPABASE_ANON_KEY=sua_chave_anonima
```

### Tabelas Ativas
- **faturamento** (3,513 registros): Receitas por locatário/shopping
- **inadimplencia** (10,791 registros): Análise de risco e cobrança
- **movimentacoes_financeiras** (1,030 registros): Fluxo de caixa
- **Pagamento_Empreendedor** (1,131 registros): Despesas operacionais

### Performance Otimizada
- Cache inteligente React Query (5min)
- Validação Zod automática
- Retry com backoff exponencial
- Processamento em Web Workers

## 🚀 Getting Started

### Pré-requisitos
- Node.js 18+
- npm ou yarn
- Conta Supabase (opcional para demo)

### Instalação

```bash
# Clone o repositório
git clone https://github.com/tecnologia1spb/alpha-edge-realestate-v2.git
cd alpha-edge-realestate-v2

# Instalar dependências
npm install

# Configurar ambiente (opcional)
cp .env.example .env.local
# Editar .env.local com suas credenciais Supabase

# Iniciar desenvolvimento
npm run dev
```

### Scripts Disponíveis

```bash
npm run dev          # Servidor desenvolvimento (porta 8080)
npm run build        # Build produção
npm run build:dev    # Build desenvolvimento
npm run lint         # Análise ESLint
npm run lint:fix     # Correção automática ESLint
npm run validate:imports # Validar imports de ícones
npm run preview      # Preview do build
```

## 📊 Componentes Principais

### KpiCard - Cards de KPI Financeiro
```tsx
// Padrão com gráfico
<KpiCard 
  titulo="Receita Total" 
  valor={2450000} 
  variacao={12.5}
  formato="moeda-compacta"
  icone={DollarSign}
  cor="blue"
/>

// Mini (compacta)
<MiniKpiCard titulo="NOI" valor={89500} formato="moeda" />

// Comparativa
<ComparativeKpiCard 
  titulo="Performance"
  valorAtual={1250000}
  valorAnterior={1100000}
/>
```

### ChartCard - Wrapper Universal
```tsx
<ChartCard 
  titulo="Receitas vs Despesas"
  subtitulo="Análise mensal"
  altura="lg"
  onExport={exportarDados}
  onFullscreen={expandir}
>
  <AreaChart data={dados} ... />
</ChartCard>
```

### Formatadores Brasileiros
```tsx
import { formatarMoeda, formatarData, formatarVariacao } from '@/lib/formatters';

formatarMoeda(1234567.89)        // "R$ 1.234.567,89"
formatarMoedaCompacta(1234567)   // "R$ 1.2M"  
formatarData('2025-01-15')       // "15/01/2025"
formatarVariacao(12.5)           // { texto: "+12.5%", tipo: "positivo" }
```

## 🤖 Sistema de Insights com IA

### Framework AVA Integrado
O dashboard utiliza o **@antv/ava** para gerar insights automáticos:

```typescript
// Configuração AVA para finanças brasileiras
const FINANCIAL_AVA_CONFIG = {
  language: 'pt-BR',
  currency: 'BRL',
  measures: ['valortotalfaturado', 'inadimplencia', 'noi'],
  dimensions: ['shopping', 'locatario', 'categoria'],
  insightTypes: ['trend', 'outlier', 'correlation', 'seasonality']
}
```

### Tipos de Insights Detectados
- **Tendências**: Crescimento/decrescimento em métricas
- **Anomalias**: Valores fora do padrão esperado  
- **Correlações**: Relações entre variáveis financeiras
- **Sazonalidade**: Padrões temporais identificados
- **Previsões**: Pontos de mudança pela IA

## 📈 Métricas de Qualidade

### Código
- **18,427 linhas** de código TypeScript
- **155 erros ESLint** (melhoria de 75%)
- **100% cobertura TypeScript** 
- **28 warnings** React Hooks otimizados

### Performance
- **< 2s** tempo de carregamento inicial
- **Web Workers** para cálculos não-bloqueantes
- **5min cache** React Query otimizado
- **Mobile-first** responsive design

### Acessibilidade
- **100% português brasileiro** localizado
- **Keyboard navigation** suportado
- **Screen reader** friendly
- **High contrast** color scheme

## 🔧 Configuração Avançada

### Tremor UI Customization
```typescript
// tailwind.config.ts
theme: {
  extend: {
    colors: {
      tremor: {
        positive: '#10b981',  // Verde financeiro
        negative: '#ef4444',  // Vermelho alertas
        warning: '#f59e0b'    // Âmbar atenção
      }
    }
  }
}
```

### Web Workers Configuration
```typescript
// vite.config.ts
worker: {
  format: 'es',
  plugins: [react()]
}
```

## 🌟 Roadmap

### v1.4.0 - Expansão Analytics
- [ ] Modelos preditivos avançados
- [ ] Integração Monte Carlo simulation
- [ ] Dashboard de Geo Intelligence
- [ ] Otimização de portfólio MPT

### v1.5.0 - Enterprise Features
- [ ] Multi-tenancy support
- [ ] Advanced RLS policies
- [ ] Custom branding
- [ ] API REST endpoints

### v2.0.0 - AI/ML Integration
- [ ] TensorFlow.js integration
- [ ] Real-time anomaly detection
- [ ] Automated reporting
- [ ] Voice interfaces

## 👥 Contribuindo

1. **Fork** o projeto
2. **Crie** sua feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. **Push** para a branch (`git push origin feature/AmazingFeature`)
5. **Abra** um Pull Request

### Padrões de Código
- **ESLint** configuration enforced
- **Prettier** formatting
- **Conventional Commits** format
- **TypeScript strict** mode
- **React Hooks** best practices

## 📄 Licença

Este projeto está sob a licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes.

## 🙏 Agradecimentos

- **Tremor UI** pela biblioteca de componentes financeiros
- **Supabase** pela infraestrutura de dados
- **Ant Design** pelo framework AVA de insights
- **Vercel** pelo hosting e deployment
- **Claude Code** pela assistência no desenvolvimento

---

<div align="center">

**🏢 Alpha Edge Real Estate Dashboard**

*Transformando dados em insights acionáveis para o mercado imobiliário*

[🚀 Demo](https://alpha-edge-realestate-v2.vercel.app) • [📚 Docs](https://github.com/tecnologia1spb/alpha-edge-realestate-v2/wiki) • [🐛 Issues](https://github.com/tecnologia1spb/alpha-edge-realestate-v2/issues)

</div>