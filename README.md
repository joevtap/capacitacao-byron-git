# Capacitação Git

- Parte 1 - O que é Git?
    - O que é o Git?
        - É um sistema de controle de versão (VCS), o que permite que várias pessoas trabalhando em um mesmo projeto, por exemplo, compartilhem as alterações mais recentes no código fonte.
        - Permite a visualização de um histórico de modificações o que permite a restauração para pontos específicos ao longo do desenvolvimento de um software
        
    - O que é um repositório de código fonte?
        - É a pasta que contém o código que será versoniado com a ajuda do Git
        - Um repositório local pode ser criado com o comando `git init`
        
    - Comandos
        - `git status` → retorna o status do repositório atual
        - `git add` → adiciona arquivos que poderão ser **committed**
        
        ```bash
        # Definir sua identidade no repositorio local
        
        git config --local user.name "usename"
        git config --local user.email "email@email.com"
        ```
        
        - 
    
- Parte 2 - Iniciando os trabalhos
    - Comandos
        - `git add <file> or git add .` → adiciona um, ou vários, respectivamente, arquivos para serem committed, ou seja: faz com que o Git passe a tomar conta das alterações desses arquivos.
        - `git rm --cached <file>` → remove um arquivo do controle do Git
        - `git commit -m "mensagem"` → faz um commit para os arquivos recém adicionados ao controle do Git
        - `git log` → retorna o log de modificações no repositório
            - `git log --oneline` → mesma coisa, mas em uma linha
            - `git log -p` → retorna o log de maneira mais completa
    - O que é um commit?
        
        É uma alteração no código que recebe uma mensagem descritiva e que é enviada para o histórico de versão
        
    - Terminologia
        - HEAD → é o estado atual do código fonte
        - Working tree → é o local onde estão os arquivos armazenados e editados no repositório
        - Index → é o local onde o Git armazena o que será committed
    - Links úteis
        - [Git log cheatsheet](https://devhints.io/git-log)
    
    > Não dê commit em código que não funcione
    > 
    
    > Dê commit em pontos significativos do desenvolvimento
    > 
- Parte 3 - Compartilhando o trabalho
    - Um repositório remoto é um repositório externo que mantém as modificações no código fonte de um repositório local
    - Comandos
        - `git init --bare` → cria um repositório puro (que não armazena cópias de arquivos)
        - `git remote -v` → lista repositórios remotos
        - `git remote add <nome> <endereco>` → adiciona um novo repositório remoto
        - `git clone <endereco> <nome>` → clona um repositorio remoto para uma pasta com determinado nome
        - `git push <remote> <branch>`→ envia as alterações para o repositório remoto em determinada branch
        - `git push -u <remote> <branch>`→ envia as alterações para o repositório remoto em determinada branch. Define como padrao o remote e o branch, tornando possivel utilizar somente `git push`
        - `git pull <remote> <branch>` → puxa as alterações de um repositório remoto   em determinada branch
        - `git remote rename <old> <new>` → renomeia um repositório remoto
    - Github
        - Plataforma de repositorios de codigo Git
- Parte 4 - Trabalhando em equipe
    - Comandos
        - `git branch` → mostra os branches do repositório atual
        - `git branch <nome>` → cria um novo branch
        - `git checkout <nome>` → muda para o branch com determinado nome
        - `git checkout -b <nome>` → cria branch e muda pra ele
        - `git merge <branch>` → une um branch ao branch atual
        - `git rebase <branch>` → atualiza o branch atual com as informações de um determinado branch (rebaseia o branch atual)
        - `git log --graph` → exibe um log com gráfico da árvore de alterações
    - Conflitos
        
        ![Separado por ====== estão as alterações no branch atual e as alterações vindas do branch a ser combinado, basta escolher qual alteração deve permanecer e apagar o que for relacionado à outra alteração](Capacitac%CC%A7a%CC%83o%20Git%205ff21d188a49451791e7ee278bc4dea0/Untitled.png)
        
        Separado por ====== estão as alterações no branch atual e as alterações vindas do branch a ser combinado, basta escolher qual alteração deve permanecer e apagar o que for relacionado à outra alteração
        
        Depois basta usar `git add <file>` e `git commit` para atualizar o git de que o conflito foi solucionado e, então, terminar o merge
        
        > Lembre-se de sempre usar o `git pull` antes de fazer alterações no branch atual, isso evita conflitos
        > 
        
- Parte 5 - Manipulando versões
    - Comandos
        - `git checkout -- <file>` ou `git restore <file>` → desfaz alterações não stageadas
        - `git reset [HEAD|estado] <file>` ou `git restore --staged <file>` → desfaz alterações stageadas
        - `git revert <commit>` → reverte uma alteração committed
        - `git stash` → adiciona uma modificação a um estado de WIP (Work In Progress)
        - `git stash list` → lista as modificações WIP
        - `git stash apply <stash id>` → aplica alterações WIP
        - `git stash drop <stash id>` → descarta alterações WIP
        - `git stash pop` → aplica e descarta ultima alteração WIP
        - `git checkout <commit>` → navega para commit especifico
            - Quando se navega para um commit, ele fica desanexado da linha de desenvolvimento, para que as alterações tenham efeito é necessário criar um novo branch a partir do commit para o qual você navegou
        - `git switch <branch>` → é o checkout mas com outro nome
        - `git switch -c <novo-branch>` → cria e muda de branch, como o checkout mas novamente com outro nome
- Parte 6 - Gerando entregas
    - Comandos
        - `git diff <commit a>..<commit b>` → mostra a diferença entre dois commits
        - `git tag -a <nome> -m <mensagem>` → gera uma tag para o estado atual do repositorio com uma mensage
        - `git tag` → lista as tags
        - `git push <remote> <nome-da-tag>` → faz o push de uma tag para um repositório remoto