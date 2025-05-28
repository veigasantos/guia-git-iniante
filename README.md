# Guia GIT para iniantes
Guia Completo de Comandos Git para Iniciantes

# Guia Completo de Comandos Git para Iniciantes

## 1. Configuração Inicial

### Configurar identidade (obrigatório antes do primeiro commit)
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seu.email@exemplo.com"
```

### Configurações opcionais mas recomendadas
```bash
# Definir editor padrão
git config --global core.editor "code"  # Para VS Code
git config --global core.editor "nano"  # Para Nano

# Configurar cores no terminal
git config --global color.ui auto

# Verificar todas as configurações
git config --list
```

## 2. Criando um Repositório

### Inicializar um novo repositório local
```bash
git init
```

### Clonar um repositório existente
```bash
git clone https://github.com/usuario/repositorio.git
git clone https://github.com/usuario/repositorio.git nome-pasta  # Especificar nome da pasta
```

## 3. Estados dos Arquivos e Área de Staging

### Verificar status dos arquivos
```bash
git status           # Status completo
git status -s        # Status resumido
```

### Adicionar arquivos à área de staging
```bash
git add arquivo.txt              # Adicionar arquivo específico
git add pasta/                   # Adicionar toda a pasta
git add .                        # Adicionar todos os arquivos modificados
git add -A                       # Adicionar todos os arquivos (incluindo deletados)
git add *.js                     # Adicionar todos os arquivos .js
```

### Remover arquivos da área de staging
```bash
git reset arquivo.txt            # Remove arquivo específico do staging
git reset                        # Remove todos os arquivos do staging
```

## 4. Commits

### Fazer commit
```bash
git commit -m "Mensagem do commit"
git commit -am "Mensagem"        # Adiciona e comita arquivos já rastreados
git commit                       # Abre editor para mensagem longa
```

### Modificar o último commit
```bash
git commit --amend -m "Nova mensagem"    # Alterar mensagem
git commit --amend                       # Adicionar arquivos ao último commit
```

## 5. Visualizando Histórico

### Ver histórico de commits
```bash
git log                          # Histórico completo
git log --oneline               # Uma linha por commit
git log --graph                 # Visualização gráfica
git log --graph --oneline       # Gráfico resumido
git log -n 5                    # Últimos 5 commits
git log --author="Nome"         # Commits de um autor específico
```

### Ver diferenças
```bash
git diff                        # Diferenças não commitadas
git diff --staged              # Diferenças na área de staging
git diff HEAD~1                # Diferenças com commit anterior
git diff arquivo.txt           # Diferenças de arquivo específico
```

## 6. Branches (Ramificações)

### Listar branches
```bash
git branch                      # Branches locais
git branch -r                   # Branches remotos
git branch -a                   # Todos os branches
```

### Criar e trocar de branch
```bash
git branch nome-branch          # Criar novo branch
git checkout nome-branch        # Trocar para branch
git checkout -b nome-branch     # Criar e trocar para novo branch
git switch nome-branch          # Trocar branch (comando mais novo)
git switch -c nome-branch       # Criar e trocar (comando mais novo)
```

### Deletar branch
```bash
git branch -d nome-branch       # Deletar branch (seguro)
git branch -D nome-branch       # Forçar deleção
```

## 7. Merge e Rebase

### Fazer merge
```bash
git checkout main               # Ir para branch principal
git merge nome-branch           # Fazer merge do branch
```

### Fazer rebase
```bash
git checkout nome-branch
git rebase main                 # Rebase do branch atual com main
```

### Resolver conflitos
```bash
# Após resolver conflitos manualmente:
git add .
git commit                      # Para merge
git rebase --continue          # Para rebase
```

## 8. Repositórios Remotos

### Adicionar repositório remoto
```bash
git remote add origin https://github.com/usuario/repositorio.git
```

### Listar repositórios remotos
```bash
git remote -v
```

### Enviar alterações (push)
```bash
git push origin main            # Enviar branch main
git push origin nome-branch     # Enviar branch específico
git push -u origin main         # Primeira vez (define upstream)
git push                        # Após definir upstream
```

### Baixar alterações (pull/fetch)
```bash
git pull origin main            # Baixar e fazer merge
git fetch origin               # Baixar sem fazer merge
git pull                       # Baixar do upstream configurado
```

## 9. Comandos de Recuperação

### Desfazer alterações
```bash
git checkout -- arquivo.txt    # Descartar alterações não commitadas
git checkout .                 # Descartar todas as alterações
git restore arquivo.txt        # Comando mais novo para restaurar arquivo
git restore .                  # Restaurar todos os arquivos
```

### Reverter commits
```bash
git revert HEAD                # Reverter último commit
git revert abc1234             # Reverter commit específico
```

### Reset (usar com cuidado)
```bash
git reset --soft HEAD~1        # Desfaz commit, mantém alterações no staging
git reset --mixed HEAD~1       # Desfaz commit e staging (padrão)
git reset --hard HEAD~1        # Desfaz tudo (PERIGOSO)
```

## 10. Trabalhando com Arquivos

### Ignorar arquivos (.gitignore)
```bash
# Criar arquivo .gitignore na raiz do projeto
echo "node_modules/" >> .gitignore
echo "*.log" >> .gitignore
echo ".env" >> .gitignore
```

### Remover arquivos do Git
```bash
git rm arquivo.txt             # Remove arquivo e do Git
git rm --cached arquivo.txt    # Remove do Git mas mantém no disco
```

### Renomear/mover arquivos
```bash
git mv arquivo-antigo.txt arquivo-novo.txt
```

## 11. Comandos Úteis para Iniciantes

### Verificar qual branch está ativo
```bash
git branch --show-current
```

### Limpar arquivos não rastreados
```bash
git clean -n                   # Mostra o que seria removido
git clean -f                   # Remove arquivos não rastreados
git clean -fd                  # Remove arquivos e pastas
```

### Salvar trabalho temporariamente
```bash
git stash                      # Salvar alterações temporariamente
git stash pop                  # Recuperar alterações salvas
git stash list                 # Listar stashes
git stash drop                 # Deletar último stash
```

## 12. Fluxo de Trabalho Básico

### Fluxo típico para trabalhar em um projeto:

1. **Clonar ou inicializar repositório**
   ```bash
   git clone URL-DO-REPOSITORIO
   # ou
   git init
   ```

2. **Verificar status e fazer alterações**
   ```bash
   git status
   # Editar arquivos...
   ```

3. **Adicionar alterações ao staging**
   ```bash
   git add .
   ```

4. **Fazer commit**
   ```bash
   git commit -m "Descrição das alterações"
   ```

5. **Enviar para repositório remoto**
   ```bash
   git push origin main
   ```

## 13. Comandos de Emergência

### Se algo deu errado:
```bash
git status                     # Ver o que está acontecendo
git log --oneline              # Ver histórico recente
git reflog                     # Ver todas as ações recentes
```

### Voltar para um estado seguro:
```bash
git checkout main              # Voltar para branch principal
git pull                       # Atualizar com versão remota
```

## Dicas Importantes

- **Sempre fazer `git status` antes de qualquer operação**
- **Fazer commits pequenos e frequentes com mensagens descritivas**
- **Nunca fazer `git reset --hard` sem ter certeza**
- **Sempre fazer `git pull` antes de `git push`**
- **Usar branches para features novas**
- **Configurar `.gitignore` no início do projeto**

## Mensagens de Commit Recomendadas

- `feat: adiciona nova funcionalidade`
- `fix: corrige bug na função X`
- `docs: atualiza documentação`
- `style: ajusta formatação do código`
- `refactor: reorganiza estrutura do código`
- `test: adiciona testes para função Y`
