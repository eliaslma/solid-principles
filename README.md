

#### S - Princípio da Responsabilidade Única (Single Responsibility Principle)

O que é? Esse princípio afirma que uma classe deve ter apenas uma razão para mudar, ou seja, deve ter uma única responsabilidade.

Para que serve? Isso ajuda a manter o código mais coeso, facilitando a manutenção e reduzindo o impacto de mudanças.

Exemplo em PHP:

```php
// Classe com múltiplas responsabilidades ❌
class Mailer {
    public function getUserEmailAddress($user) {
    
    }
    
    public function sendMail($emailAddress) {
        // Envia e-mail
    }
}

// Classe com unica responsabilidade ✅
class Mailer {
    public function sendMail($emailAddress) {
        // Envia e-mail
    }
}
```

#### O - Princípio do Aberto/Fechado (Open/Closed Principle)

O que é? Esse princípio diz que as entidades (classes, módulos, funções, etc.) devem estar abertas para extensão, mas fechadas para modificação.

Para que serve? Isso promove um código mais estável e reutilizável, permitindo adicionar novos comportamentos sem alterar o código existente.

Exemplo em PHP:

```php
// Interface para processar pagamentos
interface Pagamento {
    public function processar();
}

// Implementação para pagamento com cartão
class PagamentoCartao implements Pagamento {
    public function processar() {
        // Lógica para processar pagamento com cartão
    }
}

// Implementação para pagamento com boleto
class PagamentoBoleto implements Pagamento {
    public function processar() {
        // Lógica para processar pagamento com boleto
    }
}
```
### L - Princípio da Substituição de Liskov (Liskov Substitution Principle)

O que é? Esse princípio estabelece que objetos de uma classe base devem poder ser substituídos por objetos de suas classes derivadas sem afetar o comportamento do programa.

Para que serve? Isso garante a consistência e integridade do sistema quando substituímos objetos, evitando efeitos colaterais inesperados.

Exemplo em PHP:

```php
class Generic {
    public function setGeneric() {
        // Lógica para set da classe pai
    }
}

// Classe derivada de Generic
class AlternativeGeneric implements Generic {
   
    public function setGeneric() {
        // Lógica específica para o metodo set da classe Alternativa
    }
}

```
#### I - Princípio da Segregação de Interface (Interface Segregation Principle)
O que é? Esse princípio afirma que uma classe não deve ser forçada a implementar interfaces que não utiliza.

Para que serve? Isso evita a criação de interfaces monolíticas e garante que as classes tenham apenas os métodos necessários para seu funcionamento.

Exemplo em PHP:

```php
// Exemplo de classe incorreta ❌
 interface Animal {
     void comer();
     void dormir();
     void voar();
 }

Class Cachorro implements Animal{ 
  // herda todos os metodos, mas o cachorro nao voa! ❌
}

/*-----------------------------------------------------*/

// Exemplo de classe correta ✅
interface Animal{
  void comer();
  void dormir();
}

Class Ave implements Animal{
    // herda todos os metodos
    void voar();
}

Class Cachorro implements Animal{
// herda todos os metodos corretos ✅
}

Class Pombinha implements Aves {
// herda todos os metodos corretos ✅
}


```

#### D - Princípio da Inversão de Dependência (Dependency Inversion Principle)
O que é? Esse princípio defende que os módulos de alto nível não devem depender dos módulos de baixo nível, mas sim de abstrações. Além disso, abstrações não devem depender de detalhes, mas sim de outras abstrações.

Para que serve? Isso facilita a troca de implementações, promove o reuso e reduz acoplamento.

Exemplo em PHP:

```php
// Interface para serviço de envio de e-mail
interface Mailer {
    public function send($destinatario, $assunto, $mensagem);
}

// Classe de alto nível que depende da interface ✅
class Notifier {
    private $mailer;
    
    public function __construct(Mailer $mailer) {
        $this->mailer = $mailer;
    }
    
    public function notificarUsuario($usuario) {
        // Envia email de notificacao
        $this->mailer->send($usuario->email, 'Notificação', 'Você tem uma nova mensagem.');
    }
}
```
Esses princípios ajudam a criar código mais robusto, flexível e fácil de manter.

In ☕ We Trust
