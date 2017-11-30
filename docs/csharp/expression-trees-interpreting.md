---
title: "İfadeler yorumlama"
description: "Bir ifade ağacına yapısını incelemek için kod yazma öğrenin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: e7c5f7404546c6f3812fc5cc3d0320c77816634d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-expressions"></a>İfadeler yorumlama

[Önceki--İfadeleri yürütme](expression-trees-execution.md)

Şimdi, yapısını incelemek için biraz kod yazalım bir *ifade ağacına*. Bir ifade ağacına kümedeki her düğüm türetildiği sınıfın bir nesnesi olacak `Expression`.

Bu tasarım, bir ifade ağacına göreceli olarak doğrudan iletme özyinelemeli işlemi tüm düğümlerin ziyaret yapar. Kök düğümde başlatın ve onu ne tür bir düğüm olup olmadığını belirlemek için genel stratejidir bakın.

Düğüm türü alt öğe varsa, yinelemeli olarak alt ziyaret edin. Her alt düğümde kök düğümde kullanılan işlemi tekrarlayın: türünü belirlemek ve türü alt öğe varsa, her alt ziyaret edin.

## <a name="examining-an-expression-with-no-children"></a>Bir alt öğesi ile ifadesi inceleniyor
Her düğüm çok basit ifade ağacına ziyaret ederek başlayalım.
Bir sabit ifadesine oluşturan ve özelliklerini inceler kod aşağıdaki gibidir:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Aşağıdakileri yazdırılır:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Şimdi, bu deyim inceleyin ve bazı önemli özellikleri hakkında yazma kod yazalım. Bu kod aşağıdadır:

## <a name="examining-a-simple-addition-expression"></a>Basit bir toplama ifadesi inceleniyor

Bu bölümde giriş toplama örnekten ile başlayalım tıklatın.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Değil kullanıyorum `var` atama sağında örtülü olarak yazılan mümkün değildir, çünkü gibi bu ifade ağacına bildirmek için. Bu daha kapsamlı anlamak için okuyun [burada](implicitly-typed-lambda-expressions.md).

Kök düğüm bir `LambdaExpression`. Sağ tarafta ilginç kodu alabilmek için `=>` işleci, gereken alt öğelerinin bulmak `LambdaExpression`. Bu bölümdeki tüm ifadelerle bunu. Üst düğüm dönüş türünü Bul yardımcı `LambdaExpression`.

Her düğüm bu ifadede incelemek için yinelemeli olarak düğüm sayısını inceleyeceğiz. Basit bir ilk uygulama şöyledir:

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

Bu örnek aşağıdaki çıkış baskı:

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

Yukarıdaki kod örneğinde yineleme çok fark edeceksiniz.
Şimdi, temizleme ve daha genel amaçlı yapı ifade düğümü ziyaretçisi. Bize bir özyinelemeli algoritması yazmak gerektirecek şekilde geçiyor. Herhangi bir düğümün alt öğeleri olabilir bir tür olabilir.
Alt öğe olan herhangi bir düğümün bu alt ziyaret edin ve o düğümü belirlemek için bize gerektirir. İşte Temizlenen toplama işlemleri ziyaret etmek için özyineleme yararlanan sürüm:

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

Bu algoritma herhangi rastgele ziyaret edebileceği bir algoritma temelini `LambdaExpression`. Çok sayıda delik vardır, yani kod yalnızca oluşturduğum için çok küçük bir örnek, karşılaşabileceğiniz ifade ağaç düğümleri olası kümelerinin arar. Ancak, yine bir bit bu üretir öğrenebilirsiniz. (Varsayılan durumda `Visitor.CreateFromExpression` yöntemi yeni düğüm türü karşılaşıldığında bir ileti hata konsola yazdırır. Bu şekilde, yeni ifade türünü eklemek için bilmeniz.)

Yukarıda gösterilen Toplama ifadesi bu ziyaretçi çalıştırdığınızda, aşağıdaki çıkış alın:

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

Daha fazla genel bir ziyaretçi uygulaması oluşturduğunuza göre ziyaret edin ve çok daha farklı türde ifadeler işlem.

## <a name="examining-an-addition-expression-with-many-levels"></a>Birçok düzeylerine sahip bir toplama ifadesi inceleniyor

Şimdi daha karmaşık bir örnek deneyin, ancak yine de yalnızca eklenmesi için düğüm türleri sınırla:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Bu ziyaretçi algoritmasına çalıştırmadan önce bir düşünce alıştırma ne çıkış olabilir çıkışı çalışmaya deneyin. Unutmayın `+` işlecidir bir *ikili işleç*: iki alt, sol ve sağ işlenen temsil eden olması gerekir. Doğru bir ağaç oluşturmak için olası birkaç yolu vardır:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Ayırma en taahhüdü vurgulamak için iki olası yanıt içine görebilirsiniz. İlk temsil *sağa ilişkilendirilebilir* ifadeler. İkinci temsil *ilişkilendirilebilir sol* ifadeler.
Bu iki biçim her ikisi de avantajlarından biçimi toplama ifadelerin rasgele herhangi bir sayı ölçeklendirir birisidir. 

Bu ifade ziyaretçi yoluyla çalıştırırsanız, bu Bu çıktı, basit Toplama ifadesi doğrulama görürsünüz *ilişkilendirilebilir sol*. 

Bu örneği çalıştırmak ve tam ifade ağacına görmek için ı kaynağı deyim ağacına bir değişiklik gerekiyordu. İfade ağacına tüm sabit içeriyorsa, sonuçta elde edilen ağaç yalnızca sabit değerini içeren `10`. Derleyici tüm ek gerçekleştirir ve en basit biçimiyle ifade azaltır. Yalnızca ifade bir değişken eklemek, özgün ağaç görmek yeterlidir:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Bir ziyaretçi için bu toplam oluşturun ve ziyaretçi çalıştırmak, bu çıktı görürsünüz:

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

Ayrıca, herhangi diğer örnekleri ziyaretçi kodda çalıştırma ve temsil ettiği hangi ağaç bakın. Bir örneği burada verilmiştir `sum3` ifadesiyle yukarıda (sabiti computing derleyiciye önlemek için ek bir parametre):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Ziyaretçi çıktısı şöyledir:

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

Parantez çıkış parçası olmayan dikkat edin. Giriş ifadesi parantezlerde temsil eden düğümleri ifade ağacında yoktur. İfade ağaç yapısını öncelik iletişim kurmak gerekli tüm bilgileri içerir.

## <a name="extending-from-this-sample"></a>Bu örnekten genişletme

Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir. Bu bölümde görülen kod yalnızca sabit tamsayılar ve ikili işleme `+` işleci. Son bir örnek olarak, daha karmaşık bir ifade işlemek için ziyaretçi şimdi güncelleştirin. Bunun çalışması olalım:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Bu kod matematiksel için bir olası uygulamasını temsil eder *faktöriyelini* işlevi. Bu kod yazılmış şekilde ifadeleri için lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki limitiations vurgular. İlk olarak, deyimi Lambda'lar izin verilmiyor. Anlamına ı blokları, döngüleri kullanamazsınız, / else ifadeleri ve diğer denetim yapıları C# ' ta ortak. I ifadeleri kullanmayla sınırlıdır. İkinci olarak, yinelemeli olarak çağrı aynı ifadeye bağlanamıyorum.
I sanki zaten bir temsilci, ancak kendi ifade ağaç biçiminde çağrılamıyor verebilir. Bölümünde [ifade ağaçlar derleyen](expression-trees-building.md) bu sınırlamaların üstesinden gelmek için tekniklerini öğreneceksiniz.


Bu ifadede düğümleri her türlü karşılaşacağınız:
1. Eşittir (ikili ifade)
2. Çarp (ikili ifade)
3. Koşullu (? : ifade)
4. Yöntem çağrısı ifade (çağırma `Range()` ve `Aggregate()`)

Ziyaretçi algoritmayı değiştirmek için bir yoldur, yürütülmekte tutmak ve ulaşana her zaman düğüm türü yazmak için `default` yan tümcesi. Birkaç yinelemeden sonra olası düğümlerinin her biri görülür. Daha sonra tüm yapmanız gereken sağlayın. Sonuç şöyle olacaktır:

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

ConditionalVisitor ve MethodCallVisitor iki düğümleri işlem:

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

Ve ifade ağacına çıktı şöyle olur:

```
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a>Örnek kitaplığını genişletme

Bu bölümdeki örnekler ziyaret edin ve bir ifade ağacına düğümler incelemek için çekirdek teknikleri gösterir. Ziyaret eden ve bir ifade ağacına düğümler erişim çekirdek görevlerde yoğunlaşmak için gerekebilecek birçok Eylemler üzerinden glossed. 

İlk olarak, ziyaretçi yalnızca tamsayı olduğunu sabitleri işleyin. Sabit değerler herhangi bir sayısal tür olabilir ve dönüşümler ve bu türleri arasındaki promosyonlar C# dili destekler. Bu kodu daha sağlam bir sürümü bu olanaklarına yansıtma.

Bile son örnek bir alt olası düğüm türü tanır.
Yine başarısız olmasına neden olacak birçok ifadeleri besleyebilecek.
Tam bir uygulamaya .NET standart adı altında yer aldığı [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) ve tüm olası düğüm türleri işleyebilir.

Son olarak, bu makalede kullanılan kitaplığı tanıtım ve öğrenme için yapılmıştı. Bunu getirilmemiştir. I yapıları olmak için açıkça, teknikler vurgulamak için düğümleri ziyaret edin ve ne olduğunu analiz etmek için kullanılır ve yazıldı. Bir üretim uygulaması g'den daha fazla performans dikkat edilmesi.

Bu kısıtlamalarla bile okuduğunuzdan ve anladığınızdan ifade ağaçları algoritmaları yazma iyi yolunuzu üzerinde olmalıdır.

[Sonraki--İfade oluşturma](expression-trees-building.md)
