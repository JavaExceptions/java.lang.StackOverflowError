java.lang.StackOverflowError
============================

  StackOverflowError - Este caso de erro pode ser gerado por algum problema entre a JVM e SO. Um caso típico é o erro de estouro de pilha. Esse tipo de erro pode ocorrer caso a aplicação utilize algum tipo de loop infinito ou uma recursividade muito profunda. O tamanho da pilha alocada pela JVM durante a criação de uma thread java é de 1024KB (1mb) em um sistema Linux x64. É possível alterar esse valor para mais ou para menos a depender da necessidade da aplicação. O parâmetro da JVM -Xss:<n>k altera o valor da pilha, sendo que <n> é um valor inteiro.


Gerando o thread dumps da JVM em tempo de runtime manualmente:

  $ jstack -F -l <PID> > /tmp/jvm_thread.dump

  O formato texto pode ser aberto com as ferramentas: jVisualVM (JDK), Samurai [ref:1], TDA - Thread Dump Analyzer [ref:2], IBM Thread Analizer [ref:1] ou qualquer outro profiler Java que reconheça dump de threads Java.

  [1] http://yusuke.homeip.net/samurai/en/samurai.jar 
  [2] https://java.net/projects/tda

  Para o dump de threads é importante conhecer um pouco sobre a execução de threads na plataforma Java: sincronização, pilha de execução, thread monitor, thread status (WAINTING, RUNNING, BLOCKED, etc). Com a ferramenta certa e com um pouco de paciência é possível chegar a tão desejada causa raiz do problema: nome da classe, nome do método, nome da biblioteca ou até mesmo a linha de código que causa ou influência o crash do processo Java.

NOTAS:

    É necessário que a versão e arquitetura do JDK utilizado na análise dump seja idêntica à JVM utilizada pelo servidor de aplicação onde o erro ocorreu.
    Para que o comando gcore (invocado pela JVM após o evento de erro) funcione é necessário que o pacote gdb (A GNU source-level debugger for C, C++, Fortran and other languages) esteja devidamente instalado no Sistema Operacional.
    O procedimento acima causam o travamento das threads (equivalente ao efeito Stop The World do FullGC). Portanto utilize com cautela em ambiente de produção!

