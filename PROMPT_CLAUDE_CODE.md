# Contexto do projeto — Site Pré-COP31 Carbono Azul e Zonas Úmidas

Cole o texto abaixo como primeira mensagem no Claude Code, dentro da pasta onde estão os arquivos do site (`index.html`, `wetlands-event-site.html`).

---

## PROMPT

Estou continuando o desenvolvimento de um site estático bilíngue (PT/EN) para um evento científico internacional Pré-COP31: **"1ª Conferência de Co-benefícios do Carbono Azul e Zonas Úmidas / 1st Blue Carbon & Wetlands Co-benefits Conference"**, 6–8 de novembro de 2026, Bragança, Pará, Brasil.

### Arquivos do projeto
- `index.html` — cópia de deploy para o Cloudflare Pages. Precisa estar na raiz do repositório.
- `wetlands-event-site.html` — arquivo-fonte original. **Deve ser mantido idêntico ao `index.html`** sempre que um editar o outro.

Esses dois arquivos são tudo o que existe no site até agora. Antes de qualquer mudança, leia ambos para entender a estrutura atual.

> ⚠️ `projetos.html` foi excluído — cada projeto agora tem um link direto para seu próprio site externo.

### Sistema de design
- Fonte: Georgia (serif) para corpo, Arial (sans-serif) para textos técnicos/labels.
- Variáveis CSS no `:root`: `--green-deep`, `--green-mid`, `--green-light`, `--green-pale`, `--gold`, `--gold-light`, `--ocean`, `--ocean-light`, `--earth`, `--cream`, `--white`, `--text-dark`, `--text-mid`, `--text-light`, `--shadow`.
- Bilíngue via atributo `data-lang="pt"` / `data-lang="en"` em `<span>`, controlado por classes `body.lang-pt` / `body.lang-en` e função JS `setLang(lang)`.
- **Atenção:** `<span data-lang>` NÃO funciona dentro de `<option>` de `<select>` — navegadores ignoram CSS ali. Para dropdowns bilíngues, usar `data-pt`/`data-en` como atributos do `<option>` e atualizar via JS dentro de `setLang()` (já implementado nos formulários de submissão).

### Conteúdo implementado
- Hero com imagem de costa de manguezal; título "Carbono Azul" / "Blue Carbon".
- Seção Sobre, seção Programa (3 dias de mesas temáticas).
- Seção Objetivos Científicos (6 objetivos numerados, fundo verde escuro) — posicionada antes do Programa.
- Seção Projetos com cards individuais e links externos:
  - Wetlands Project → `https://coastalwetlandrestoration.org`
  - Wetlands Co-benefits → site em construção (sem link)
  - Beyond Carbon → `https://www.belmontforum.org/`
  - Mangues da Amazônia → `https://manguesdaamazonia.ufpa.br`
- Seção Local do Evento (`id="local"`) com mapa OpenStreetMap de Bragança, fotos e cards informativos sobre gastronomia, manguezais e hospedagem.
- Seção Inscrições com formulário de registro e formulário de submissão de trabalhos (apenas pôster A0 e apresentação oral; idiomas PT/EN; prazo de notificação 20 set 2026).
- Comitê Organizador (`id="participar"`):
  - Direção Científica: Carolina Bueno (Unicamp/UCSC), Adina Paytan (UCSC), Prof. Dr. Marcus Emanuel Barroncas Fernandes (UFPA)
  - Coordenação Geral Científica: Clarice Araujo (UFRJ/Fiocruz), Dra. Anelize Bahniuk Rumbelsperger (Depto. Geologia, UFPR)
  - Direção de Comunicação e Organização Geral: Gabriella Luz — PMP · Gestão de Projetos · Comunicação · Eventos, California, USA
  - Contato: `info@cobenefitsconference.com`
- Seção de Apoio/Realização com logos (ICMBio, The Nature Conservancy, Pajé Cultural, Belmont Forum).
- Footer com copyright "1st Blue Carbon & Wetlands Co-benefits Conference · Unicamp · UFPA · UCSC".

### Logos — estado atual
- **Inline SVGs** (sem dependência externa): Comissão Europeia, ICMBio, The Nature Conservancy
- **Wikimedia CDN** (funcionando): PNUMA/UNEP, FAPESP, IBGE, Bandeira EU
- **Wix CDN** (funcionando): Pajé Cultural
- **URLs com fallback para pill de texto**: Unicamp, UFPA, UC Santa Cruz, Fiocruz (podem não carregar em localhost mas devem funcionar no deploy)

### Pendências conhecidas
- Valores de inscrição: ainda "a definir" / "TBD".
- Formulários: integração com Tally.so ainda não configurada (atualmente são formulários HTML estáticos).
- Pagamento: integração com Mercado Pago (Pix) ainda não implementada.
- Domínio: em processo de registro. Candidato: `cobenefitsconference.com`.

### Deploy — Cloudflare Pages
O site é publicado via **Cloudflare Pages** conectado a um repositório Git (GitHub ou GitLab).

**Passos para primeiro deploy:**
1. Criar repositório Git na pasta do projeto (se ainda não existir):
   ```bash
   git init
   git add index.html wetlands-event-site.html PROMPT_CLAUDE_CODE.md
   git commit -m "first commit"
   ```
2. Criar repositório remoto no GitHub e fazer push:
   ```bash
   git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
   git push -u origin main
   ```
3. No painel do Cloudflare Pages: **Create a project → Connect to Git → selecionar o repositório**
   - Framework preset: `None`
   - Build command: *(deixar vazio)*
   - Build output directory: `/` (raiz)
4. Cloudflare detecta o `index.html` na raiz e publica automaticamente.

**Para atualizações futuras:** qualquer `git push` dispara um novo deploy automaticamente em ~1 minuto.

**Regra importante:** sempre que `index.html` mudar, `wetlands-event-site.html` deve ser atualizado também — os dois devem estar sempre idênticos. Usar `cp index.html wetlands-event-site.html` (ou o inverso) após cada edição.

### O que preciso agora
[Descreva aqui a tarefa específica — por exemplo: "fazer o primeiro deploy no Cloudflare Pages", "integrar formulários com Tally.so", "adicionar seção de patrocinadores", etc.]
