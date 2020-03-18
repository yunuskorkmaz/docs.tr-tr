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
# <a name="interpreting-expressions"></a><span data-ttu-id="9b48f-103">İfade Yorumlama</span><span class="sxs-lookup"><span data-stu-id="9b48f-103">Interpreting Expressions</span></span>

[<span data-ttu-id="9b48f-104">Önceki -- İfadeleri Yürütme</span><span class="sxs-lookup"><span data-stu-id="9b48f-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="9b48f-105">Şimdi, bir *ifade ağacının*yapısını incelemek için bazı kodlar yazalım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="9b48f-106">İfade ağacındaki her düğüm, türetilen bir sınıfın nesnesi `Expression`olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="9b48f-107">Bu tasarım, bir ifade ağacındaki tüm düğümleri ziyaret etmeyi nispeten yalın bir özyinelemeli işlem haline getirir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="9b48f-108">Genel strateji kök düğümden başlamak ve ne tür bir düğüm olduğunu belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="9b48f-109">Düğüm türünde çocuklar varsa, özyinelemeli olarak çocukları ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="9b48f-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="9b48f-110">Her alt düğümde, kök düğümünde kullanılan işlemi tekrarlayın: türünü belirleyin ve türde çocuk varsa, her bir çocuğu ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="9b48f-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="9b48f-111">Çocuksuz Bir İfadeyi İnceleme</span><span class="sxs-lookup"><span data-stu-id="9b48f-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="9b48f-112">Çok basit bir ifade ağacında her düğüm ziyaret ederek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="9b48f-113">Burada sabit bir ifade oluşturur ve sonra özelliklerini inceler kod:</span><span class="sxs-lookup"><span data-stu-id="9b48f-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="9b48f-114">Bu aşağıdaki leri yazdırır:</span><span class="sxs-lookup"><span data-stu-id="9b48f-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="9b48f-115">Şimdi, bu ifadeyi inceleyecek kodu yazalım ve bununla ilgili bazı önemli özellikleri yazalım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="9b48f-116">İşte o kod:</span><span class="sxs-lookup"><span data-stu-id="9b48f-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="9b48f-117">Basit Bir Ek İfadenin İncelenmesi</span><span class="sxs-lookup"><span data-stu-id="9b48f-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="9b48f-118">Bu bölüme girişten ek örnek ile başlayalım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="9b48f-119">Atamanın sağ `var` tarafı örtülü olarak yazıldığı için bu ifade ağacını bildirmek için kullanmıyorum.</span><span class="sxs-lookup"><span data-stu-id="9b48f-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="9b48f-120">Bu daha derinden anlamak için, [burada](implicitly-typed-lambda-expressions.md)okuyun .</span><span class="sxs-lookup"><span data-stu-id="9b48f-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="9b48f-121">Kök düğüm bir `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="9b48f-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="9b48f-122">`=>` Operatörün sağ tarafında ilginç kodu almak için, bir çocuk bulmak gerekir `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="9b48f-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="9b48f-123">Bunu bu bölümdeki tüm ifadelerle yapacağız.</span><span class="sxs-lookup"><span data-stu-id="9b48f-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="9b48f-124">Üst düğüm, `LambdaExpression`'nin dönüş türünü bulmamıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9b48f-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="9b48f-125">Bu ifadedeki her düğümü incelemek için, bir dizi düğümü özyinelemeli olarak ziyaret etmemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="9b48f-126">İşte basit bir ilk uygulama:</span><span class="sxs-lookup"><span data-stu-id="9b48f-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="9b48f-127">Bu örnek aşağıdaki çıktıyı yazdırır:</span><span class="sxs-lookup"><span data-stu-id="9b48f-127">This sample prints the following output:</span></span>

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

<span data-ttu-id="9b48f-128">Yukarıdaki kod örneğinde çok fazla tekrar göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="9b48f-129">Bunu temizleyelim ve daha genel amaçlı bir ifade düğümü oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="9b48f-130">Bu da özyinelemeli bir algoritma yazmamızı gerektirecek.</span><span class="sxs-lookup"><span data-stu-id="9b48f-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="9b48f-131">Herhangi bir düğüm çocuk sahibi olabilecek bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="9b48f-132">Çocukları olan herhangi bir düğüm, bu çocukları ziyaret etmemizi ve düğümün ne olduğunu belirlememizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="9b48f-133">Ek işlemleri ziyaret etmek için özyinelemekullanan temizlenmiş sürüm aşağıda veda edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9b48f-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="9b48f-134">Bu algoritma, herhangi bir rasgele `LambdaExpression`ziyaret edebilirsiniz bir algoritmanın temelidir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="9b48f-135">Bir sürü delik vardır, yani oluşturduğum kod sadece karşılaşabileceği olası ifade ağacı düğümlerinin çok küçük bir örneğini arar.</span><span class="sxs-lookup"><span data-stu-id="9b48f-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="9b48f-136">Ancak, hala ne üretir biraz öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="9b48f-137">(Yöntemdeki `Visitor.CreateFromExpression` varsayılan durum, yeni bir düğüm türüne rastlandığında hata konsoluna bir ileti yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="9b48f-138">Bu şekilde, yeni bir ifade türü eklemeyi bilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="9b48f-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="9b48f-139">Bu ziyaretçiyi yukarıda gösterilen ek ifadede çalıştırdığınızda, aşağıdaki çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="9b48f-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="9b48f-140">Artık daha genel bir ziyaretçi uygulaması oluştursanız, çok daha farklı türde ifadeleri ziyaret edebilir ve işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="9b48f-141">Birçok Düzeyde Bir Ek İfadeyi İnceleme</span><span class="sxs-lookup"><span data-stu-id="9b48f-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="9b48f-142">Daha karmaşık bir örnek deneyelim, yine de düğüm türlerini yalnızca eklemeyle sınırlandıralım:</span><span class="sxs-lookup"><span data-stu-id="9b48f-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="9b48f-143">Bunu ziyaretçi algoritması üzerinde çalıştırmadan önce, çıktının ne olabileceğini bulmak için bir düşünce alıştırması deneyin.</span><span class="sxs-lookup"><span data-stu-id="9b48f-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="9b48f-144">İşleticinin `+` bir *ikili işleç*olduğunu unutmayın: sol ve sağ operandları temsil eden iki çocuğu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="9b48f-145">Doğru olabilecek bir ağaç oluşturmanın birkaç olası yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="9b48f-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="9b48f-146">En umut verici vurgulamak için iki olası cevaplar içine ayrım görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="9b48f-147">İlk *doğru bağdaştırıcı* ifadeler temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9b48f-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="9b48f-148">İkinci *sol bağdaştırıcı* ifadeleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9b48f-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="9b48f-149">Bu iki biçimden her ikisinin de avantajı, biçimin herhangi bir rasgele ek ifade sayısına ölçeklendirmesidir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="9b48f-150">Bu ifadeyi ziyaretçi aracılığıyla çalıştırarsanız, basit ek ifadesinin *birleştirici bırakıldığını*doğrulayan bu çıktıyı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="9b48f-151">Bu örneği çalıştırmak ve tam ifade ağacını görmek için kaynak ifade ağacında bir değişiklik yapmam gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="9b48f-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="9b48f-152">İfade ağacı tüm sabitleri içerdiğinde, ortaya çıkan ağaç `10`yalnızca .</span><span class="sxs-lookup"><span data-stu-id="9b48f-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="9b48f-153">Derleyici tüm eklemeyi gerçekleştirir ve ifadeyi en basit biçimine indirir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="9b48f-154">İfadeye yalnızca bir değişken eklemek özgün ağacı görmek için yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="9b48f-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="9b48f-155">Bu meblağ için bir ziyaretçi oluşturun ve bu çıktıyı göreceksiniz ziyaretçiçalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9b48f-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="9b48f-156">Ayrıca, diğer örneklerden herhangi birini ziyaretçi kodu üzerinden çalıştırabilir ve hangi ağacı temsil ettiğinizi görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="9b48f-157">Yukarıdaki `sum3` ifadenin bir örneği (derleyicinin sabiti hesaplamasını önlemek için ek bir parametreyle birlikte):</span><span class="sxs-lookup"><span data-stu-id="9b48f-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="9b48f-158">İşte ziyaretçinin çıktısı:</span><span class="sxs-lookup"><span data-stu-id="9b48f-158">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="9b48f-159">Parantezlerin çıktının bir parçası olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9b48f-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="9b48f-160">İfade ağacında giriş ifadesinde parantezi temsil eden düğüm yok.</span><span class="sxs-lookup"><span data-stu-id="9b48f-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="9b48f-161">İfade ağacının yapısı, önceliği iletmek için gereken tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="9b48f-162">Bu örnekten genişletme</span><span class="sxs-lookup"><span data-stu-id="9b48f-162">Extending from this sample</span></span>

<span data-ttu-id="9b48f-163">Örnek sadece en ilkel ifade ağaçları ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="9b48f-164">Bu bölümde gördüğünüz kod yalnızca sabit tamsayıları ve ikili `+` işleci işler.</span><span class="sxs-lookup"><span data-stu-id="9b48f-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="9b48f-165">Son bir örnek olarak, daha karmaşık bir ifade işlemek için ziyaretçi güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="9b48f-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="9b48f-166">Bunun için işe yarayalım:</span><span class="sxs-lookup"><span data-stu-id="9b48f-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="9b48f-167">Bu kod matematiksel *faktöriyel* fonksiyon için olası bir uygulamayı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9b48f-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="9b48f-168">Bu kodu yazma şeklim, Expressions'a lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki sınırlamasını vurgular.</span><span class="sxs-lookup"><span data-stu-id="9b48f-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="9b48f-169">İlk olarak, ifade lambdas izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9b48f-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="9b48f-170">Bu döngüler, bloklar, eğer / else ifadeleri ve C # ortak diğer kontrol yapıları kullanamazsınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="9b48f-171">İfadelerle sınırlıyım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-171">I'm limited to using expressions.</span></span> <span data-ttu-id="9b48f-172">İkincisi, aynı ifadeyi tekrartekrar söyleyemem.</span><span class="sxs-lookup"><span data-stu-id="9b48f-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="9b48f-173">Zaten bir delege olsaydı yapabilirdim, ama ifade ağacı şeklinde diyemem.</span><span class="sxs-lookup"><span data-stu-id="9b48f-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="9b48f-174">İfade ağaçları [inşa](expression-trees-building.md) etme bölümünde bu sınırlamaları aşmak için teknikler öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="9b48f-175">Bu ifadede, tüm bu tür düğümlerle karşılaşırsınız:</span><span class="sxs-lookup"><span data-stu-id="9b48f-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="9b48f-176">Eşit (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="9b48f-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="9b48f-177">Çarpma (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="9b48f-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="9b48f-178">Koşullu (?</span><span class="sxs-lookup"><span data-stu-id="9b48f-178">Conditional (the ?</span></span> <span data-ttu-id="9b48f-179">: ifade)</span><span class="sxs-lookup"><span data-stu-id="9b48f-179">: expression)</span></span>
4. <span data-ttu-id="9b48f-180">Yöntem Çağrı İfadesi (arama `Range()` ve `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="9b48f-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="9b48f-181">Ziyaretçi algoritmasını değiştirmenin bir yolu, onu yürütmeye devam etmek ve yan `default` tümcenize her ulaştığınızda düğüm türünü yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="9b48f-182">Birkaç yinelemeden sonra, olası düğümlerin her birini görmüş olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="9b48f-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="9b48f-183">O zaman ihtiyacın olan her şeye sahipsin.</span><span class="sxs-lookup"><span data-stu-id="9b48f-183">Then, you have all you need.</span></span> <span data-ttu-id="9b48f-184">Sonuç şu şekilde olurdu:</span><span class="sxs-lookup"><span data-stu-id="9b48f-184">The result would be something like this:</span></span>

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

<span data-ttu-id="9b48f-185">ConditionalVisitor ve MethodCallVisitor bu iki düğüm leri işlemeyi:</span><span class="sxs-lookup"><span data-stu-id="9b48f-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="9b48f-186">Ve ifade ağacı için çıkış olacaktır:</span><span class="sxs-lookup"><span data-stu-id="9b48f-186">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="9b48f-187">Örnek Kitaplığı Genişletme</span><span class="sxs-lookup"><span data-stu-id="9b48f-187">Extending the Sample Library</span></span>

<span data-ttu-id="9b48f-188">Bu bölümdeki örnekler, bir ifade ağacındaki düğümleri ziyaret etmek ve incelemek için temel teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="9b48f-189">Bir ifade ağacındaki düğümleri ziyaret etme ve düğümlere erişme temel görevlerine odaklanmak için ihtiyaç duyabileceğiniz birçok eylem üzerinde parlattım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="9b48f-190">İlk olarak, ziyaretçiler yalnızca toplamlı olan sabitleri işler.</span><span class="sxs-lookup"><span data-stu-id="9b48f-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="9b48f-191">Sabit değerler başka sayısal türler olabilir ve C# dili bu türler arasındaki dönüşümleri ve promosyonları destekler.</span><span class="sxs-lookup"><span data-stu-id="9b48f-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="9b48f-192">Bu kodun daha sağlam bir sürümü tüm bu yetenekleri yansıtacak.</span><span class="sxs-lookup"><span data-stu-id="9b48f-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="9b48f-193">Hatta son örnek olası düğüm türlerinin bir alt kümesi tanır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="9b48f-194">Yine de başarısız olmasına neden olacak birçok ifadeleri besleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b48f-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="9b48f-195">.NET Standard adı <xref:System.Linq.Expressions.ExpressionVisitor> altında tam bir uygulama dahildir ve tüm olası düğüm türlerini işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="9b48f-196">Son olarak, bu makalede kullanılan kütüphane gösteri ve öğrenme için inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9b48f-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="9b48f-197">Optimize edilmiş değil.</span><span class="sxs-lookup"><span data-stu-id="9b48f-197">It's not optimized.</span></span> <span data-ttu-id="9b48f-198">Yapıları çok net yapmak ve düğümleri ziyaret etmek ve orada ne olduğunu analiz etmek için kullanılan teknikleri vurgulamak için yazdım.</span><span class="sxs-lookup"><span data-stu-id="9b48f-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="9b48f-199">Bir üretim uygulaması performansa benden daha fazla önem verirdi.</span><span class="sxs-lookup"><span data-stu-id="9b48f-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="9b48f-200">Bu sınırlamalar bile, iyi okuma ve ifade ağaçları anlamak algoritmaları yazma yolunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9b48f-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="9b48f-201">Sonraki -- Bina İfadeleri</span><span class="sxs-lookup"><span data-stu-id="9b48f-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
