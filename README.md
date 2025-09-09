# 🎉 Caça ao Tesouro Virtual - Convite de Aniversário

Um jogo interativo de caça ao tesouro com interface desktop para revelar convites de aniversário de forma divertida e envolvente.

## 🎮 Como Usar

1. **Abra o arquivo `index.html`** em qualquer navegador moderno
2. **Clique nos ícones** do desktop para procurar a pista secreta
3. **Encontre o ícone correto** para revelar a primeira pista
4. **Complete o mini-desafio** (drag & drop ou pergunta geek)
5. **Descubra o convite completo** com todos os detalhes do evento

### 🔗 Personalização por Convidado

Para criar experiências únicas para cada convidado, adicione um parâmetro `id` na URL:

```
index.html?id=joao
index.html?id=maria
index.html?id=pedro
```

Cada ID gerará uma disposição diferente dos ícones usando:
- **Seed determinístico**: Hash djb2 do ID do convidado
- **RNG Mulberry32**: Gerador de números pseudoaleatórios consistente
- **Shuffle determinístico**: Embaralhamento reproduzível dos ícones
- **Seleção aleatória**: Escolha determinística do ícone correto

## 🎮 Recursos Implementados

### ✅ Interface Desktop Fake
- Barra superior com título e relógio em tempo real
- Grade responsiva de ícones (4-6 colunas desktop, 3 tablet, 2 mobile)
- Design glassmorphism com gradiente dark
- Ícones SVG inline (sem dependências externas)

### ✅ Sistema de Jogo
- **Randomização por ID**: Cada convidado tem layout único via `?id=nome`
- **16 ícones diferentes**: Projetos, Logs, Fotos_2009, Confidencial, etc.
- **Contador de tentativas**: Acompanha progresso sem humilhar
- **Sistema de dicas**: 2 níveis após 30s (área + piscar)

### ✅ Revelação Progressiva
1. **Primeira pista**: Mostra data (29/10/2024)
2. **Mini-puzzle**: Drag & drop OU pergunta geek
3. **Convite final**: Data, hora, local + botões de ação

### ✅ Funcionalidades Avançadas
- **Persistência**: localStorage salva progresso
- **RSVP integrado**: WhatsApp, arquivo .ics, copiar detalhes
- **Easter eggs**: Digite "help" para terminal fake, clique 5x para confete
- **Acessibilidade**: Tab/Enter/Esc, aria-labels, foco visível
- **Som opcional**: Efeitos sonoros mutáveis

## 🔧 Uso Técnico

### Personalização por Convidado
```
index.html?id=joao
index.html?id=maria
index.html?id=pedro
```

Cada ID gera um layout único usando RNG seeded (Mulberry32).

### Estrutura do Arquivo
- **Arquivo único**: `index.html` (tudo inline)
- **Sem dependências**: Funciona offline
- **Compatibilidade**: Mobile-first, hit-area ≥ 44px
- **Fallback**: `<noscript>` mostra convite simples

## 🎨 Customização

### Alterar Informações do Evento
Edite as seguintes linhas no HTML:

```javascript
// Linha ~580 - Primeira revelação
'Você achou a pista! <br><br><strong>Data: 29/10/2024</strong>'

// Linha ~650 - Convite final
<p><strong>📅 Data:</strong> 29 de Outubro de 2024</p>
<p><strong>🕰️ Horário:</strong> 19:30</p>
<p><strong>📍 Local:</strong> [Local será informado em breve]</p>
```

### Adicionar Novos Ícones
Edite o array `ICONS` (linha ~120) adicionando:

```javascript
{ name: 'NovoIcone', svg: '<path d="..."/>', isCorrect: false }
```

## 🚀 Deploy

### GitHub Pages
1. Faça upload do `index.html` para repositório GitHub
2. Ative GitHub Pages nas configurações
3. Compartilhe o link: `https://usuario.github.io/repo/index.html?id=convidado`

### Hospedagem Simples
Qualquer servidor web estático serve o arquivo diretamente.

## 🎯 Próximos Passos (Opcional)

- [ ] Integração com banco PostgreSQL para analytics
- [ ] Sistema de convites por email automatizado
- [ ] Dashboard admin para acompanhar RSVPs
- [ ] Temas personalizáveis
- [ ] Mais mini-puzzles

## 🎊 Easter Eggs Inclusos

1. **Terminal**: Digite "help" para ver manual fake
2. **Confete**: Clique 5x no fundo para animação
3. **Sons**: Clique no ícone de som para mutar/desmutar
4. **Dicas**: Botão aparece após 30s de tentativas

## 🚀 **Benefícios das Melhorias**

- **Mais Robusto**: Código seguindo padrões estabelecidos
- **Determinístico**: Resultados previsíveis e reproduzíveis
- **Escalável**: Fácil adicionar novos ícones ou funcionalidades
- **Testável**: Sistema de IDs permite testes consistentes
- **Limpo**: Código mais organizado e comentado

## 🛠️ **Modo Desenvolvimento**

### Reset Durante Desenvolvimento

Para facilitar os testes durante o desenvolvimento, foi adicionado:

1. **Botão Reset Dev** (canto inferior esquerdo): Limpa o localStorage e reinicia o jogo
2. **Comentário no código**: Linha para descommentar e limpar automaticamente

```javascript
// DESENVOLVIMENTO: Limpar localStorage para testes
// localStorage.removeItem('solved'); // Descomente para resetar
```

### Para Produção

Antes de enviar para os convidados:
1. **Remover** o botão de reset dev do HTML
2. **Remover** os comentários de desenvolvimento
3. **Comentar** a linha de reset automático

O projeto agora segue exatamente a arquitetura do seu pseudocódigo, mantendo todas as funcionalidades originais mas com uma base técnica muito mais sólida! 🎉

---

**Desenvolvido com ❤️ para tornar convites inesquecíveis!**