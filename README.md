# Mô Saboaria — Gestão Artesanal

Aplicativo web responsivo para acompanhar produtos, estoque, movimentações financeiras e fornecedores. O projeto utiliza HTML5, CSS3 e JavaScript moderno, sem etapa de compilação.

## Executar no VS Code

1. Extraia o ZIP para uma pasta.
2. Abra a pasta no Visual Studio Code.
3. Instale a extensão **Live Server**.
4. Clique com o botão direito em `index.html` e escolha **Open with Live Server**.
5. Não abra o HTML diretamente pelo protocolo `file://`, pois o navegador pode bloquear o carregamento do `data.json`.

Alternativa: no terminal dentro da pasta, execute `python -m http.server 8000` e acesse `http://localhost:8000`.

## Módulos

- **Visão geral:** indicadores, receitas e despesas concluídas, valor estimado do estoque, gráficos e alertas.
- **Produtos e estoque:** cadastro, edição, exclusão, custo unitário, quantidade mínima e histórico de movimentações.
- **Movimentações:** entradas e despesas financeiras, pesquisa, edição, exclusão e exportação CSV.
- **Fornecedores:** cadastro e listagem.
- **Relatórios:** análise de despesas e evolução mensal; exportação para PDF pelo diálogo de impressão do navegador.
- **Dados e backup:** exportação/importação JSON, CSV e restauração da base inicial.
- **Tema claro/escuro:** alternância no topo, com preferência salva no navegador.
- **Instalável e com cache offline:** manifesto PWA e service worker armazenam os arquivos da interface após a primeira abertura em servidor local/HTTPS.

## Dados importados

O `data.json` contém uma cópia inicial normalizada dos dados das planilhas anexadas. Produtos vêm da aba de inventário da planilha de estoque; as seis despesas preenchidas vêm da aba `SAÍDAS` da planilha financeira; os fornecedores vêm da aba `FORNECEDORES`. A aba `MOVIMENTAÇÃO` não contém receitas preenchidas, então não foram inventadas receitas.

A planilha de estoque possui registros e fórmulas de controle mais amplos do que o formato simples do aplicativo. Este projeto importa os dados mestres relevantes e não mantém vínculo ativo com os arquivos Excel. Os nomes com erros ortográficos evidentes no cadastro inicial foram corrigidos para exibição; confira a origem se precisar preservar a grafia literal da planilha.

## Persistência e limites

- As alterações são salvas no `localStorage` do navegador e perfil atual; não sincronizam entre computadores.
- Use a área **Dados e backup** para exportar uma cópia regularmente.
- A movimentação de estoque é separada das movimentações financeiras para evitar que uma transferência interna seja contabilizada como receita/despesa.
- O PDF é gerado por uma página de impressão; no diálogo do navegador, selecione **Salvar como PDF**.
- O modo offline depende de uma primeira abertura com o servidor ativo; atualizações do app podem exigir recarregar a página.
- Esta versão não tem autenticação, API ou banco de dados remoto. Para operação multiusuário, será necessário implementar backend, banco de dados, login, permissões, backups automáticos e validação centralizada.

## Arquivos

- `index.html` — estrutura do aplicativo
- `styles.css` — interface, responsividade e temas
- `app.js` — lógica, validações e relatórios
- `data.json` — base inicial importada
- `logo-mo.png` — versão otimizada da marca para a interface
