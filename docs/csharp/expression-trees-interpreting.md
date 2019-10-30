---
title: İfade Yorumlama
description: Bir ifade ağacının yapısını incelemek için kod yazmayı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 34434a633d866b82da3da713aaecc218c7d35124
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036902"
---
# <a name="interpreting-expressions"></a>İfade Yorumlama

[Önceki--Ifadeler yürütülüyor](expression-trees-execution.md)

Şimdi bir *ifade ağacının*yapısını incelemek için bazı kodlar yazalım. Bir ifade ağacındaki her düğüm, `Expression`türetilen bir sınıfın nesnesi olur.

Bu tasarım, bir ifade ağacındaki tüm düğümleri görece düz ileri özyinelemeli bir işlem olarak ziyaret etmenizi sağlar. Genel strateji, kök düğümde başlamak ve ne tür bir düğüm olduğunu belirlemektir.

Düğüm türünün alt öğeleri varsa, yinelemeli olarak alt öğeleri ziyaret edin. Her alt düğümde, kök düğümde kullanılan işlemi yineleyin: türü belirleme ve türün alt öğeleri varsa, alt öğelerin her birini ziyaret edin.

## <a name="examining-an-expression-with-no-children"></a>Alt öğe Içermeyen bir Ifadeyi İnceleme
Her düğümü çok basit bir ifade ağacında ziyaret ederek başlayalım.
Sabit bir ifade oluşturan ve sonra özelliklerini incelediği kod aşağıda verilmiştir:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Bu işlem şunları yazdırır:

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Şimdi, bu ifadeyi inceleyecek ve ilgili bazı önemli özellikleri yazacak olan kodu yazalım. Bu kod şu şekildedir:

## <a name="examining-a-simple-addition-expression"></a>Basit bir toplama Ifadesi İnceleme

Bu bölüme giriş bölümünde ek örnekle başlayalım.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Atamanın sağ tarafı örtük olarak yazıldığından, bu ifade ağacını bildirmek için `var` kullanmıyorum. Daha derin anlamak için [buradan](implicitly-typed-lambda-expressions.md)okuyun.

Kök düğüm bir `LambdaExpression`. `=>` işlecinin sağ tarafında ilginç kod almak için `LambdaExpression`alt öğelerinden birini bulmanız gerekir. Bu bölümdeki tüm ifadelerle bunu yapacağız. Üst düğüm `LambdaExpression`dönüş türünü bulmamıza yardımcı olur.

Bu ifadedeki her bir düğümü incelemek için, bir dizi düğümü yinelemeli olarak ziyaret etmemiz gerekir. Basit bir ilk uygulama aşağıda verilmiştir:

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

Yukarıdaki kod örneğinde çok fazla yineleme olduğunu fark edeceksiniz.
Bunu temizleyelim ve daha genel amaçlı bir ifade düğümü ziyaretçisi oluşturalım. Bu, özyinelemeli bir algoritma yazmamızı gerektireceğiz. Herhangi bir düğüm, alt öğelerine sahip olabilecek bir türde olabilir.
Alt öğeleri olan herhangi bir düğüm, bu alt öğeleri ziyaret etmemizi ve bu düğümün ne olduğunu belirlemenizi ister. Ek işlemleri ziyaret eden özyineleme kullanan temizlenmiş bir sürüm aşağıda verilmiştir:

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

Bu algoritma, herhangi bir rastgele `LambdaExpression`ziyaret edebildikleri bir algoritmanın temelini oluşturur. Oluşturduğum kodun yalnızca, karşılaşabileceği ifade ağacı düğümlerinin çok küçük bir örneğine bakabilmesini sağlayan çok sayıda delik vardır. Bununla birlikte, ne kadar çok şey ürettiğini de öğrenirsiniz. (`Visitor.CreateFromExpression` yönteminde varsayılan durum, yeni bir düğüm türüyle karşılaşıldığında hata konsoluna bir ileti yazdırır. Bu şekilde, yeni bir ifade türü eklemeyi bilirsiniz.)

Yukarıda gösterilen ekleme ifadesinde bu ziyaretçisini çalıştırdığınızda aşağıdaki çıktıyı alırsınız:

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

Artık daha genel bir ziyaretçi uygulamasına sahip olduğunuza göre, daha birçok farklı tür ifadeyi ziyaret edebilir ve işleyebilirsiniz.

## <a name="examining-an-addition-expression-with-many-levels"></a>Birçok düzey içeren bir toplama Ifadesi inceleniyor

Daha karmaşık bir örnek deneyelim, ancak yine de düğüm türlerini yalnızca ekleme ile sınırlandıralım:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Bunu ziyaretçi algoritmasında çalıştırmadan önce, çıktının ne kadar olabileceğini öğrenmek için düşündüyü deneyin. `+` işlecinin bir *ikili işleç*olduğunu unutmayın: sol ve sağ işlenenleri temsil eden iki alt öğesi olmalıdır. Doğru olabilecek bir ağaç oluşturmak için birkaç olası yol vardır:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

En fazla taahhüdün vurgulanmasını sağlamak için ayrımı iki olası yanıt halinde görebilirsiniz. İlki, *doğru ilişkilendirilebilir* ifadeleri temsil eder. İkincisi *sol ilişkilendirilebilir* ifadeleri temsil eder.
Bu iki biçimin her ikisi de, biçimin rastgele herhangi bir dizi ek ifadeye ölçeklenmesinin avantajına sahiptir. 

Bu ifadeyi ziyaretçi aracılığıyla çalıştırırsanız, bu çıktıyı görürsünüz ve basit toplama ifadesinin *ilişkilendirilebilir*olduğunu doğrulayın. 

Bu örneği çalıştırmak ve tam ifade ağacına bakmak için kaynak ifade ağacında bir değişiklik yapmam gerekiyordu. İfade ağacı tüm sabitleri içerdiğinde, ortaya çıkan ağaç yalnızca `10`sabit değerini içerir. Derleyici tüm ekleme işlemini gerçekleştirir ve ifadeyi en basit biçimine düşürür. Özgün ağacı görmek için ifadede yalnızca bir değişken eklemek yeterlidir:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Bu Sum için bir ziyaretçi oluşturun ve ziyaretçi çalıştırın bu çıktıyı görürsünüz:

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

Diğer örneklerden herhangi birini ziyaretçi kodu aracılığıyla da çalıştırabilir ve hangi ağacın temsil ettiğini görebilirsiniz. Yukarıdaki `sum3` ifadeye bir örnektir (derleyicinin sabiti bilgi işlem yapmasını engellemek için ek bir parametre ile):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Ziyaretçinin çıkışı şöyledir:

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

Ayraçların çıktının parçası olmadığına dikkat edin. İfade ağacında giriş ifadesindeki ayraçları temsil eden hiçbir düğüm yok. İfade ağacının yapısı, önceliği iletmek için gereken tüm bilgileri içerir.

## <a name="extending-from-this-sample"></a>Bu örnekten genişletme

Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir. Bu bölümde gördüğünüz kod yalnızca sabit tamsayıları ve ikili `+` işlecini işler. Son bir örnek olarak, ziyaretçisini daha karmaşık bir ifadeyi işleyecek şekilde güncelleştirelim. Bunun için bu işi yapalim:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Bu kod matematik *çarpınımı* işlevi için olası bir uygulamayı temsil eder. Bu kodu yazdığım şekilde, deyimlere lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki sınırlaması vurgulanmıştır. İlk olarak, ifade lambdaları kullanılamaz. Bu, içindeki C#döngüleri, blokları, if/else deyimlerini ve diğer denetim yapılarını kullanmıyorum anlamına gelir. İfadeleri kullanma sınırlıyorum. İkinci olarak aynı ifadeyi özyinelemeli olarak çağıramıyorum.
Ben zaten bir temsilciyiysem, ancak ifade ağaç biçiminde çağıramıyorum. [İfade ağaçları oluşturma](expression-trees-building.md) bölümünde bu sınırlamaları aşmaya yönelik teknikler öğreneceksiniz.

Bu ifadede, tüm bu türlerin düğümleri ile karşılaşırsınız:

1. Eşittir (ikili ifade)
2. Çarp (ikili ifade)
3. Koşullu (? ifadesini
4. Yöntem çağrısı Ifadesi (`Range()` ve `Aggregate()`çağırma)

Ziyaretçi algoritmasını değiştirmek için bir yol, yürütmeyi sürdürmek ve `default` yan tümcesine her ulaşışınızda düğüm türünü yazmaktır. Birkaç yinelemeden sonra potansiyel düğümlerin her birini gördünüz. Ardından, ihtiyacınız olan her şey vardır. Sonuç şuna benzer olacaktır:

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

ConditionalVisitor ve MethodCallVisitor bu iki düğümü işler:

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

Ve ifade ağacı için çıkış şu şekilde olur:

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

## <a name="extending-the-sample-library"></a>Örnek kitaplığı genişletme

Bu bölümdeki örneklerde, bir ifade ağacındaki düğümleri ziyaret etmek ve incelemek için temel teknikler gösterilmektedir. Bir ifade ağacındaki düğümleri ziyaret ederek ve bunlara erişen temel görevlere odaklanmak için ihtiyacınız olabilecek çok sayıda eylemi glossed. 

Birincisi, ziyaretçiler yalnızca tamsayı olan sabitleri işler. Sabit değerler başka herhangi bir sayısal tür olabilir ve dil, C# bu türler arasındaki dönüşümleri ve yükseltmeleri destekler. Bu kodun daha sağlam bir sürümü tüm bu özellikleri yansıtır.

Son örnek bile olası düğüm türlerinin bir alt kümesini tanır.
Yine de, başarısız olmasına neden olacak çok sayıda ifade akışı yapabilirsiniz.
Tam bir uygulama .NET Standard <xref:System.Linq.Expressions.ExpressionVisitor> adı altında bulunur ve tüm olası düğüm türlerini işleyebilir.

Son olarak, bu makalede kullandığım kitaplık tanıtım ve öğrenme için oluşturulmuştur. En iyi duruma getirilmemiştir. Bu yapıyı, yapıları çok açık hale getirmek ve düğümleri ziyaret etmek ve ne olduğunu çözümlemek için kullanılan teknikleri vurgulamak için yazdım. Bir üretim uygulamasının performanstan daha fazla dikkat edin.

Bu sınırlamalara rağmen, ifade ağaçlarını okuyan ve anlayan algoritmalar yazmak için size iyi bir yol olmalıdır.

[Next--Ifadeleri oluşturma](expression-trees-building.md)
