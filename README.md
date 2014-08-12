java.lang.StackOverflowError
============================

StackOverflowError - Este caso de erro pode ser gerado por algum problema entre a JVM e SO. Um caso típico é o erro de estouro de pilha. Esse tipo de erro pode ocorrer caso a aplicação utilize algum tipo de loop infinito ou uma recursividade muito profunda. O tamanho da pilha alocada pela JVM durante a criação de uma thread java é de 1024KB (1mb) em um sistema Linux x64. É possível alterar esse valor para mais ou para menos a depender da necessidade da aplicação. O parâmetro da JVM -Xss:<n>k altera o valor da pilha, sendo que <n> é um valor inteiro.




NOTAS:

    o arquivo de dump no formato hprof pode ser aberto com os utilizatários jVisualvm (fornecido pelo JDK) ou Eclipse Memory Analizer (MAT).  É necessário que a versão e arquitetura do JDK utilizado na análise dump seja idêntica à JVM utilizada pelo servidor de aplicação onde o erro ocorreu.
    Para que o comando gcore (invocado pela JVM após o evento de erro) funcione é necessário que o pacote gdb (A GNU source-level debugger for C, C++, Fortran and other languages) esteja devidamente instalado no Sistema Operacional.

