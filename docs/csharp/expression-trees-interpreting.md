---
title: İfade yorumlama
description: İfade ağacı yapısını incelemek için kod yazmayı öğrenin.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 95fbb021aeeb9f2f4eb36f664f9fe904d1d52453
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506425"
---
# <a name="interpreting-expressions"></a>İfade yorumlama

[Önceki--İfade yürütme](expression-trees-execution.md)

Şimdi, yapısını incelemek için biraz kod yazalım bir *ifade ağacı*. Türetilen bir sınıfın bir nesnesi bir ifade ağacı kümedeki her düğüm olacaktır `Expression`.

Bu tasarım, bir ifade ağacı bir göreceli olarak doğrudan iletme özyinelemeli işlemi tüm düğümlerin ziyaret yapar. Genel kök düğümünde başlatmak ve ne tür bir düğümü olduğu belirlemek için stratejisidir.

Düğüm türü, alt öğe varsa, yinelemeli olarak alt ziyaret edin. Her alt düğümü kök düğümde kullanılan işlemi tekrarlayın: türünü belirlemeye ve alt türü varsa, her alt ziyaret edin.

## <a name="examining-an-expression-with-no-children"></a>Alt öğe ile bir ifade İnceleme
Her bir çok basit bir ifade ağacı düğümünde bağlanarak başlayalım.
Sabit bir ifade oluşturur ve ardından özelliklerini inceler kod aşağıdaki gibidir:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Aşağıdaki yazdırır:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Şimdi, bu ifadeyi inceleyin ve bu konuda bazı önemli özellikleri yazma kod yazalım. Bu kod şu şekildedir:

## <a name="examining-a-simple-addition-expression"></a>Basit bir toplama ifadesi İnceleme

Bu bölümde giriş toplama örnekten başlayalım.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Değil kullanıyorum `var` ataması sağ tarafında örtük mümkün değildir, çünkü gibi bu ifade ağacı bildirmek için. Bu daha derin bir şekilde anlamak için okuma [burada](implicitly-typed-lambda-expressions.md).

Kök düğüm bir `LambdaExpression`. Sağ tarafta ilginç kod ürününü `=>` işleci, bir alt öğeleri bulmak için ihtiyacınız `LambdaExpression`. Bu bölümdeki tüm ifadeler ile bunu. Üst düğümün dönüş türünü bulmamıza yardımcı `LambdaExpression`.

Her düğüm bu ifade incelemek için yinelemeli olarak düğüm sayısı inceleyeceğiz. Basit bir ilk uygulama şu şekildedir:

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

Bu örnek aşağıdaki çıkışı yazdırır:

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

Yukarıdaki kod örneğinde yineleme çok fazla fark edeceksiniz.
Şimdi, temizleme ve daha genel amaçlı bir derleme ifade düğümü ziyaretçisi. Bir önyinelemeli algoritmanız yazma bırakmamızı zordur. Herhangi bir düğümün alt öğeleri olabilir bir tür olabilir.
Alt öğelere sahip herhangi bir düğüm alt ziyaret edin ve o düğümde belirlemek gerektirir. İşte Temizlenen toplama işlemleri ziyaret etmek için özyineleme yararlanan sürüm:

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

Bu algoritma herhangi bir rastgele ziyaret edebileceği bir algoritma temelidir `LambdaExpression`. Yani kod yalnızca oluşturduğum olası ayarlar, karşılaşabileceğiniz ifade ağacı düğümlerinin çok küçük bir örnek için görünür, çok sayıda açıkları vardır. Ancak, yine de bir bit bu üretir öğrenebilirsiniz. (Varsayılan durumda `Visitor.CreateFromExpression` yöntemi yeni bir düğüm türü ile karşılaşıldığında bir ileti hata konsola yazdırır. Bu şekilde, yeni bir ifade türü eklemek için bildiğiniz.)

Yukarıda gösterilen ek ifade üzerinde bu ziyaretçi çalıştırdığınızda, aşağıdaki çıkışı alırsınız:

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

Daha genel bir ziyaretçi uygulaması oluşturduğunuza göre ziyaret edin ve çok daha farklı türde ifadeler işlem.

## <a name="examining-an-addition-expression-with-many-levels"></a>Birçok düzeyine sahip bir toplama ifadesi İnceleme

Şimdi daha karmaşık bir örnek deneyin, ancak hala düğüm türü için yalnızca toplama sınırla:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Bu ziyaretçi algoritmasına çalıştırmadan önce çıkış gerçekleştirmekte zorlanabilecek kullanıma çalışmak için bir düşünce alıştırma deneyin. Unutmayın `+` işleci, bir *ikili işleç*: iki alt, sol ve sağ işlenen temsil eden olması gerekir. Doğru bir ağaç oluşturmak için olası birkaç yolu vardır:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

En olası vurgulamak için iki olası yanıt içine ayrımı görebilirsiniz. İlk temsil *sağdan birleşir* ifadeler. İkinci temsil *ilişkilendirilebilir sol* ifadeler.
Her iki bu iki biçim biçimi ek ifadeleri rastgele dilediğiniz sayıda ölçeklendirir avantajlarındandır. 

Bu ifade ziyaretçi yoluyla çalıştırırsanız, bu Bu çıktı, basit bir toplama ifadesi olduğu doğrulanıyor görürsünüz *ilişkilendirilebilir sol*. 

Bu örneği çalıştırmak ve tam ifade ağacı görmek için ı kaynak ifade ağacına değişiklik yapmanız gerekiyordu. İfade ağacı, tüm sabit içeriyorsa, sonuç ağacı yalnızca sabit değerini içeren `10`. Derleyici, tüm ek gerçekleştirir ve en basit haliyle ifade azaltır. Bir değişkeni ifade yalnızca ekleme, özgün ağaç görmek yeterlidir:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Bir ziyaretçi için bu toplam oluşturun ve ziyaretçi çalıştırmak, bu Çıktıyı görürsünüz:

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

Ayrıca, diğer örneklerden birini ziyaretçi kodda çalıştırma ve temsil ettiği hangi ağaç görebilirsiniz. İşte bir örnek `sum3` yukarıda bir ifade (ile ek bir parametre, derleyici sabiti bilgi işlem gelen önlemek için):

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

Parantezler çıkış parçası olmadığına dikkat edin. Parantez içinde giriş ifadesi temsil eden düğümler ifade ağacında yoktur. İfade ağacı yapısını önceliği iletişim kurmak gerekli tüm bilgileri içerir.

## <a name="extending-from-this-sample"></a>Bu örnekten genişletme

Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir. Bu bölümde görülen kodu yalnızca sabit tamsayı ve ikili işler `+` işleci. Son örnek, daha karmaşık bir ifadeyi işlemek için ziyaretçi güncelleştirelim. Bunun için işe olalım:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Bu kod için matematiksel bir olası uygulama temsil eden *faktöriyelini* işlevi. Bu kod yazılan şekilde ifade ağaçları ifadeleri lambda ifadeleri atayarak oluşturmanın iki sınırlamaları vurgular. İlk olarak, deyim lambdaları izin verilmez. Anlamı miyim blokları, döngüleri kullanamazsınız, / else ifadeleri ve diğer denetim yapıları C# ' de ortak. İfadeler için faturalamayı ortağıyım. İkinci olarak, yinelemeli olarak çağrısı aynı ifadede bağlanamıyorum.
Ben sanki zaten bir temsilci, ancak kendi ifade ağaç biçiminde çağrılamıyor olabilir. Bölümünde [ifade ağaçları oluşturma](expression-trees-building.md) bu sınırlamaların üstesinden gelmek için tekniklerini öğreneceksiniz.


Bu ifade, her türden düğümleri karşılaşacağınız:
1. Eşittir (ikili ifade)
2. Çarpma (ikili ifade)
3. Koşullu (? : ifade)
4. Yöntem çağrısı ifadesi (çağırma `Range()` ve `Aggregate()`)

Ziyaretçi algoritması değiştirmek için bir yoludur yürütme tutun ve ulaştığınız zaman her düğüm türü yazmak için `default` yan tümcesi. Birkaç yinelemenin ardından olası düğümlerinin her biri görülür. Daha sonra ihtiyacınız vardır. Sonuç aşağıdakine benzer olacaktır:

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

Bu iki düğüm ConditionalVisitor ve MethodCallVisitor İşle:

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

Ve ifade ağacı için çıktı aşağıdaki gibi olur:

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

Bu bölümdeki örnekler ziyaret edin ve bir ifade ağacı düğümler incelemek için çekirdek teknikleri gösterir. Ziyaret edin ve bir ifade ağacı düğümler erişim temel görevler üzerinde yoğunlaşmak için ihtiyacınız olabilecek birçok eylemi üzerinden glossed. 

İlk olarak, ziyaretçi yalnızca ise tamsayı sabitleri işleyin. Herhangi bir sayısal tür sabit değerler olabilir ve dönüştürmeler ve promosyonlar bu türler arasında C# dili destekler. Bu kod daha sağlam bir sürümü, tüm bu özellikler yansıtma.

Bile son örnek, bir alt kümesini olası düğüm türleri tanır.
Yine de başarısız olmasına neden olacak çok sayıda ifadeleri besleyebilecek.
.NET Standard'da adı altında tam bir uygulamaya dahil <xref:System.Linq.Expressions.ExpressionVisitor> ve tüm olası düğüm türleri işleyebilir.

Son olarak, bu makaledeki kullandım kitaplığı, tanıtım ve öğrenme için oluşturulmuştur. Bu duruma getirilmemiştir. Yapıları olmak için çok kullanılan ve teknikler vurgulamak için düğümleri ziyaret edin ve ne olduğunu çözümlemek için kullanılan yazdığım. Bir üretim uygulamanız sahibim çok daha fazla performans dikkat.

Bu kısıtlamalarla bile okumanız ve anlamanız ifade ağaçları algoritmalar yazma iyi yolunuzu üzerinde olmalıdır.

[Sonraki--İfade oluşturma](expression-trees-building.md)
