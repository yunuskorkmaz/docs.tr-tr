---
title: İfade Yorumlama
description: İfade ağacının yapısını incelemek için kod yazmayı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146014"
---
# <a name="interpreting-expressions"></a>İfade Yorumlama

[Önceki -- İfadeleri Yürütme](expression-trees-execution.md)

Şimdi, bir *ifade ağacının*yapısını incelemek için bazı kodlar yazalım. İfade ağacındaki her düğüm, türetilen bir sınıfın nesnesi `Expression`olacaktır.

Bu tasarım, bir ifade ağacındaki tüm düğümleri ziyaret etmeyi nispeten yalın bir özyinelemeli işlem haline getirir. Genel strateji kök düğümden başlamak ve ne tür bir düğüm olduğunu belirlemektir.

Düğüm türünde çocuklar varsa, özyinelemeli olarak çocukları ziyaret edin. Her alt düğümde, kök düğümünde kullanılan işlemi tekrarlayın: türünü belirleyin ve türde çocuk varsa, her bir çocuğu ziyaret edin.

## <a name="examining-an-expression-with-no-children"></a>Çocuksuz Bir İfadeyi İnceleme
Çok basit bir ifade ağacında her düğüm ziyaret ederek başlayalım.
Burada sabit bir ifade oluşturur ve sonra özelliklerini inceler kod:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Bu aşağıdaki leri yazdırır:

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Şimdi, bu ifadeyi inceleyecek kodu yazalım ve bununla ilgili bazı önemli özellikleri yazalım. İşte o kod:

## <a name="examining-a-simple-addition-expression"></a>Basit Bir Ek İfadenin İncelenmesi

Bu bölüme girişten ek örnek ile başlayalım.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Atamanın sağ `var` tarafı örtülü olarak yazıldığı için bu ifade ağacını bildirmek için kullanmıyorum. Bu daha derinden anlamak için, [burada](implicitly-typed-lambda-expressions.md)okuyun .

Kök düğüm bir `LambdaExpression`. `=>` Operatörün sağ tarafında ilginç kodu almak için, bir çocuk bulmak gerekir `LambdaExpression`. Bunu bu bölümdeki tüm ifadelerle yapacağız. Üst düğüm, `LambdaExpression`'nin dönüş türünü bulmamıza yardımcı olur.

Bu ifadedeki her düğümü incelemek için, bir dizi düğümü özyinelemeli olarak ziyaret etmemiz gerekir. İşte basit bir ilk uygulama:

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

Bu örnek aşağıdaki çıktıyı yazdırır:

```output
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

Yukarıdaki kod örneğinde çok fazla tekrar göreceksiniz.
Bunu temizleyelim ve daha genel amaçlı bir ifade düğümü oluşturalım. Bu da özyinelemeli bir algoritma yazmamızı gerektirecek. Herhangi bir düğüm çocuk sahibi olabilecek bir tür olabilir.
Çocukları olan herhangi bir düğüm, bu çocukları ziyaret etmemizi ve düğümün ne olduğunu belirlememizi gerektirir. Ek işlemleri ziyaret etmek için özyinelemekullanan temizlenmiş sürüm aşağıda veda edilmiştir:

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

Bu algoritma, herhangi bir rasgele `LambdaExpression`ziyaret edebilirsiniz bir algoritmanın temelidir. Bir sürü delik vardır, yani oluşturduğum kod sadece karşılaşabileceği olası ifade ağacı düğümlerinin çok küçük bir örneğini arar. Ancak, hala ne üretir biraz öğrenebilirsiniz. (Yöntemdeki `Visitor.CreateFromExpression` varsayılan durum, yeni bir düğüm türüne rastlandığında hata konsoluna bir ileti yazdırır. Bu şekilde, yeni bir ifade türü eklemeyi bilirsiniz.)

Bu ziyaretçiyi yukarıda gösterilen ek ifadede çalıştırdığınızda, aşağıdaki çıktıyı alırsınız:

```output
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

Artık daha genel bir ziyaretçi uygulaması oluştursanız, çok daha farklı türde ifadeleri ziyaret edebilir ve işleyebilirsiniz.

## <a name="examining-an-addition-expression-with-many-levels"></a>Birçok Düzeyde Bir Ek İfadeyi İnceleme

Daha karmaşık bir örnek deneyelim, yine de düğüm türlerini yalnızca eklemeyle sınırlandıralım:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Bunu ziyaretçi algoritması üzerinde çalıştırmadan önce, çıktının ne olabileceğini bulmak için bir düşünce alıştırması deneyin. İşleticinin `+` bir *ikili işleç*olduğunu unutmayın: sol ve sağ operandları temsil eden iki çocuğu olmalıdır. Doğru olabilecek bir ağaç oluşturmanın birkaç olası yolu vardır:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

En umut verici vurgulamak için iki olası cevaplar içine ayrım görebilirsiniz. İlk *doğru bağdaştırıcı* ifadeler temsil eder. İkinci *sol bağdaştırıcı* ifadeleri temsil eder.
Bu iki biçimden her ikisinin de avantajı, biçimin herhangi bir rasgele ek ifade sayısına ölçeklendirmesidir.

Bu ifadeyi ziyaretçi aracılığıyla çalıştırarsanız, basit ek ifadesinin *birleştirici bırakıldığını*doğrulayan bu çıktıyı görürsünüz.

Bu örneği çalıştırmak ve tam ifade ağacını görmek için kaynak ifade ağacında bir değişiklik yapmam gerekiyordu. İfade ağacı tüm sabitleri içerdiğinde, ortaya çıkan ağaç `10`yalnızca . Derleyici tüm eklemeyi gerçekleştirir ve ifadeyi en basit biçimine indirir. İfadeye yalnızca bir değişken eklemek özgün ağacı görmek için yeterlidir:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Bu meblağ için bir ziyaretçi oluşturun ve bu çıktıyı göreceksiniz ziyaretçiçalıştırın:

```output
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

Ayrıca, diğer örneklerden herhangi birini ziyaretçi kodu üzerinden çalıştırabilir ve hangi ağacı temsil ettiğinizi görebilirsiniz. Yukarıdaki `sum3` ifadenin bir örneği (derleyicinin sabiti hesaplamasını önlemek için ek bir parametreyle birlikte):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

İşte ziyaretçinin çıktısı:

```output
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

Parantezlerin çıktının bir parçası olmadığını unutmayın. İfade ağacında giriş ifadesinde parantezi temsil eden düğüm yok. İfade ağacının yapısı, önceliği iletmek için gereken tüm bilgileri içerir.

## <a name="extending-from-this-sample"></a>Bu örnekten genişletme

Örnek sadece en ilkel ifade ağaçları ile ilgilidir. Bu bölümde gördüğünüz kod yalnızca sabit tamsayıları ve ikili `+` işleci işler. Son bir örnek olarak, daha karmaşık bir ifade işlemek için ziyaretçi güncelleştirelim. Bunun için işe yarayalım:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Bu kod matematiksel *faktöriyel* fonksiyon için olası bir uygulamayı temsil eder. Bu kodu yazma şeklim, Expressions'a lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki sınırlamasını vurgular. İlk olarak, ifade lambdas izin verilmez. Bu döngüler, bloklar, eğer / else ifadeleri ve C # ortak diğer kontrol yapıları kullanamazsınız anlamına gelir. İfadelerle sınırlıyım. İkincisi, aynı ifadeyi tekrartekrar söyleyemem.
Zaten bir delege olsaydı yapabilirdim, ama ifade ağacı şeklinde diyemem. İfade ağaçları [inşa](expression-trees-building.md) etme bölümünde bu sınırlamaları aşmak için teknikler öğreneceksiniz.

Bu ifadede, tüm bu tür düğümlerle karşılaşırsınız:

1. Eşit (ikili ifade)
2. Çarpma (ikili ifade)
3. Koşullu (? : ifade)
4. Yöntem Çağrı İfadesi (arama `Range()` ve `Aggregate()`)

Ziyaretçi algoritmasını değiştirmenin bir yolu, onu yürütmeye devam etmek ve yan `default` tümcenize her ulaştığınızda düğüm türünü yazmaktır. Birkaç yinelemeden sonra, olası düğümlerin her birini görmüş olacaksınız. O zaman ihtiyacın olan her şeye sahipsin. Sonuç şu şekilde olurdu:

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

ConditionalVisitor ve MethodCallVisitor bu iki düğüm leri işlemeyi:

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

Ve ifade ağacı için çıkış olacaktır:

```output
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

## <a name="extending-the-sample-library"></a>Örnek Kitaplığı Genişletme

Bu bölümdeki örnekler, bir ifade ağacındaki düğümleri ziyaret etmek ve incelemek için temel teknikleri gösterir. Bir ifade ağacındaki düğümleri ziyaret etme ve düğümlere erişme temel görevlerine odaklanmak için ihtiyaç duyabileceğiniz birçok eylem üzerinde parlattım.

İlk olarak, ziyaretçiler yalnızca toplamlı olan sabitleri işler. Sabit değerler başka sayısal türler olabilir ve C# dili bu türler arasındaki dönüşümleri ve promosyonları destekler. Bu kodun daha sağlam bir sürümü tüm bu yetenekleri yansıtacak.

Hatta son örnek olası düğüm türlerinin bir alt kümesi tanır.
Yine de başarısız olmasına neden olacak birçok ifadeleri besleyebilirsiniz.
.NET Standard adı <xref:System.Linq.Expressions.ExpressionVisitor> altında tam bir uygulama dahildir ve tüm olası düğüm türlerini işleyebilir.

Son olarak, bu makalede kullanılan kütüphane gösteri ve öğrenme için inşa edilmiştir. Optimize edilmiş değil. Yapıları çok net yapmak ve düğümleri ziyaret etmek ve orada ne olduğunu analiz etmek için kullanılan teknikleri vurgulamak için yazdım. Bir üretim uygulaması performansa benden daha fazla önem verirdi.

Bu sınırlamalar bile, iyi okuma ve ifade ağaçları anlamak algoritmaları yazma yolunda olmalıdır.

[Sonraki -- Bina İfadeleri](expression-trees-building.md)
