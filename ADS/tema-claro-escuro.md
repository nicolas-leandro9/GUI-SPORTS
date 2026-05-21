# 🌙☀️ Tema Claro / Escuro — Gui Sports

Guia para adicionar o toggle de tema em **todas as páginas** do site.

---

## 1. CSS — Variáveis de tema

Cole isto dentro do `<style>` de cada página (ou no `styles.css` global):

```css

```

---

## 2. HTML — Tag `<html>` e botão no header

**Passo 1:** Adicione `data-theme="dark"` na tag de abertura `<html>`:

```html
<html lang="pt-BR" data-theme="dark">
```

**Passo 2:** Adicione o botão dentro do `.icons` no header (antes de fechar a `<div class="icons">`):

```html
<button class="theme-toggle" onclick="toggleTheme()" id="themeBtn">☀️ Claro</button>
```

Ficará assim no header completo:

```html
<div class="icons" style="display:flex; align-items:center;">
    <span>🔍</span>
    <a href="conta_dashboard.html"><span>👤</span></a>
    <a href="carrinho.html" style="color:#fff; text-decoration:none"><span>🛒</span></a>
    <button class="theme-toggle" onclick="toggleTheme()" id="themeBtn">☀️ Claro</button>
</div>
```

---

## 3. JavaScript — Cole antes de fechar o `</body>`

```html
<script>
    // Aplica o tema salvo ao carregar a página
    const savedTheme = localStorage.getItem('guisports-theme') || 'dark';
    document.documentElement.setAttribute('data-theme', savedTheme);
    document.getElementById('themeBtn').textContent =
        savedTheme === 'dark' ? '☀️ Claro' : '🌙 Escuro';

    function toggleTheme() {
        const current = document.documentElement.getAttribute('data-theme');
        const next = current === 'dark' ? 'light' : 'dark';
        document.documentElement.setAttribute('data-theme', next);
        localStorage.setItem('guisports-theme', next);
        document.getElementById('themeBtn').textContent =
            next === 'dark' ? '☀️ Claro' : '🌙 Escuro';
    }
</script>
```

> O tema é salvo no `localStorage` do navegador — ou seja, se o usuário trocar para claro em uma página, todas as outras já vão abrir no tema claro também. ✅

---

## 4. Substituir cores fixas por variáveis

Nos elementos que usam cores fixas (`#111`, `#1a1a1a`, `#fff`, `#000`, etc.), substitua pelas variáveis para que respondam ao tema:

| Antes (fixo)       | Depois (variável)        |
|--------------------|--------------------------|
| `background: #111` | `background: var(--bg)`  |
| `background: #1a1a1a` | `background: var(--bg-card)` |
| `color: #fff`      | `color: var(--text)`     |
| `color: #bbb`      | `color: var(--text-muted)` |
| `border: #2a2a2a`  | `border-color: var(--border-color)` |
| `background: #000` *(header)* | `background: var(--header-bg)` |

---

## 5. Checklist por página

Adicione estes 4 itens em cada página:

- [ ] `data-theme="dark"` na tag `<html>`
- [ ] Variáveis CSS de tema no `<style>` ou `styles.css`
- [ ] Botão `.theme-toggle` com `id="themeBtn"` no header
- [ ] Script de toggle antes de fechar `</body>`

---

## Páginas já implementadas

| Página | Status |
|--------|--------|
| `sobre.html` | ✅ Implementado |
| `contato.html` | ✅ Implementado |
| `pagina_principal.html` | ⏳ Adicionar conforme guia |
| `roupas.html` | ⏳ Adicionar conforme guia |
| `calcados.html` | ⏳ Adicionar conforme guia |
| `carrinho.html` | ⏳ Adicionar conforme guia |
| `login.html` | ⏳ Adicionar conforme guia |
