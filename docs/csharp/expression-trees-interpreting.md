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
# <a name="interpreting-expressions"></a><span data-ttu-id="d5383-104">İfadeler yorumlama</span><span class="sxs-lookup"><span data-stu-id="d5383-104">Interpreting Expressions</span></span>

[<span data-ttu-id="d5383-105">Önceki--İfadeleri yürütme</span><span class="sxs-lookup"><span data-stu-id="d5383-105">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="d5383-106">Şimdi, yapısını incelemek için biraz kod yazalım bir *ifade ağacına*.</span><span class="sxs-lookup"><span data-stu-id="d5383-106">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="d5383-107">Bir ifade ağacına kümedeki her düğüm türetildiği sınıfın bir nesnesi olacak `Expression`.</span><span class="sxs-lookup"><span data-stu-id="d5383-107">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="d5383-108">Bu tasarım, bir ifade ağacına göreceli olarak doğrudan iletme özyinelemeli işlemi tüm düğümlerin ziyaret yapar.</span><span class="sxs-lookup"><span data-stu-id="d5383-108">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="d5383-109">Kök düğümde başlatın ve onu ne tür bir düğüm olup olmadığını belirlemek için genel stratejidir bakın.</span><span class="sxs-lookup"><span data-stu-id="d5383-109">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="d5383-110">Düğüm türü alt öğe varsa, yinelemeli olarak alt ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="d5383-110">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="d5383-111">Her alt düğümde kök düğümde kullanılan işlemi tekrarlayın: türünü belirlemek ve türü alt öğe varsa, her alt ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="d5383-111">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="d5383-112">Bir alt öğesi ile ifadesi inceleniyor</span><span class="sxs-lookup"><span data-stu-id="d5383-112">Examining an Expression with No Children</span></span>
<span data-ttu-id="d5383-113">Her düğüm çok basit ifade ağacına ziyaret ederek başlayalım.</span><span class="sxs-lookup"><span data-stu-id="d5383-113">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="d5383-114">Bir sabit ifadesine oluşturan ve özelliklerini inceler kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d5383-114">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="d5383-115">Aşağıdakileri yazdırılır:</span><span class="sxs-lookup"><span data-stu-id="d5383-115">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="d5383-116">Şimdi, bu deyim inceleyin ve bazı önemli özellikleri hakkında yazma kod yazalım.</span><span class="sxs-lookup"><span data-stu-id="d5383-116">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="d5383-117">Bu kod aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="d5383-117">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="d5383-118">Basit bir toplama ifadesi inceleniyor</span><span class="sxs-lookup"><span data-stu-id="d5383-118">Examining a simple Addition Expression</span></span>

<span data-ttu-id="d5383-119">Bu bölümde giriş toplama örnekten ile başlayalım tıklatın.</span><span class="sxs-lookup"><span data-stu-id="d5383-119">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="d5383-120">Değil kullanıyorum `var` atama sağında örtülü olarak yazılan mümkün değildir, çünkü gibi bu ifade ağacına bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="d5383-120">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="d5383-121">Bu daha kapsamlı anlamak için okuyun [burada](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d5383-121">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="d5383-122">Kök düğüm bir `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="d5383-122">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="d5383-123">Sağ tarafta ilginç kodu alabilmek için `=>` işleci, gereken alt öğelerinin bulmak `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="d5383-123">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="d5383-124">Bu bölümdeki tüm ifadelerle bunu.</span><span class="sxs-lookup"><span data-stu-id="d5383-124">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="d5383-125">Üst düğüm dönüş türünü Bul yardımcı `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="d5383-125">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="d5383-126">Her düğüm bu ifadede incelemek için yinelemeli olarak düğüm sayısını inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="d5383-126">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="d5383-127">Basit bir ilk uygulama şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d5383-127">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="d5383-128">Bu örnek aşağıdaki çıkış baskı:</span><span class="sxs-lookup"><span data-stu-id="d5383-128">This sample prints the following output:</span></span>

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

<span data-ttu-id="d5383-129">Yukarıdaki kod örneğinde yineleme çok fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d5383-129">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="d5383-130">Şimdi, temizleme ve daha genel amaçlı yapı ifade düğümü ziyaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d5383-130">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="d5383-131">Bize bir özyinelemeli algoritması yazmak gerektirecek şekilde geçiyor.</span><span class="sxs-lookup"><span data-stu-id="d5383-131">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="d5383-132">Herhangi bir düğümün alt öğeleri olabilir bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5383-132">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="d5383-133">Alt öğe olan herhangi bir düğümün bu alt ziyaret edin ve o düğümü belirlemek için bize gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d5383-133">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="d5383-134">İşte Temizlenen toplama işlemleri ziyaret etmek için özyineleme yararlanan sürüm:</span><span class="sxs-lookup"><span data-stu-id="d5383-134">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="d5383-135">Bu algoritma herhangi rastgele ziyaret edebileceği bir algoritma temelini `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="d5383-135">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="d5383-136">Çok sayıda delik vardır, yani kod yalnızca oluşturduğum için çok küçük bir örnek, karşılaşabileceğiniz ifade ağaç düğümleri olası kümelerinin arar.</span><span class="sxs-lookup"><span data-stu-id="d5383-136">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="d5383-137">Ancak, yine bir bit bu üretir öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5383-137">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="d5383-138">(Varsayılan durumda `Visitor.CreateFromExpression` yöntemi yeni düğüm türü karşılaşıldığında bir ileti hata konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d5383-138">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="d5383-139">Bu şekilde, yeni ifade türünü eklemek için bilmeniz.)</span><span class="sxs-lookup"><span data-stu-id="d5383-139">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="d5383-140">Yukarıda gösterilen Toplama ifadesi bu ziyaretçi çalıştırdığınızda, aşağıdaki çıkış alın:</span><span class="sxs-lookup"><span data-stu-id="d5383-140">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="d5383-141">Daha fazla genel bir ziyaretçi uygulaması oluşturduğunuza göre ziyaret edin ve çok daha farklı türde ifadeler işlem.</span><span class="sxs-lookup"><span data-stu-id="d5383-141">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="d5383-142">Birçok düzeylerine sahip bir toplama ifadesi inceleniyor</span><span class="sxs-lookup"><span data-stu-id="d5383-142">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="d5383-143">Şimdi daha karmaşık bir örnek deneyin, ancak yine de yalnızca eklenmesi için düğüm türleri sınırla:</span><span class="sxs-lookup"><span data-stu-id="d5383-143">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="d5383-144">Bu ziyaretçi algoritmasına çalıştırmadan önce bir düşünce alıştırma ne çıkış olabilir çıkışı çalışmaya deneyin.</span><span class="sxs-lookup"><span data-stu-id="d5383-144">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="d5383-145">Unutmayın `+` işlecidir bir *ikili işleç*: iki alt, sol ve sağ işlenen temsil eden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5383-145">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="d5383-146">Doğru bir ağaç oluşturmak için olası birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="d5383-146">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="d5383-147">Ayırma en taahhüdü vurgulamak için iki olası yanıt içine görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5383-147">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="d5383-148">İlk temsil *sağa ilişkilendirilebilir* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="d5383-148">The first represents *right associative* expressions.</span></span> <span data-ttu-id="d5383-149">İkinci temsil *ilişkilendirilebilir sol* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="d5383-149">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="d5383-150">Bu iki biçim her ikisi de avantajlarından biçimi toplama ifadelerin rasgele herhangi bir sayı ölçeklendirir birisidir.</span><span class="sxs-lookup"><span data-stu-id="d5383-150">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="d5383-151">Bu ifade ziyaretçi yoluyla çalıştırırsanız, bu Bu çıktı, basit Toplama ifadesi doğrulama görürsünüz *ilişkilendirilebilir sol*.</span><span class="sxs-lookup"><span data-stu-id="d5383-151">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="d5383-152">Bu örneği çalıştırmak ve tam ifade ağacına görmek için ı kaynağı deyim ağacına bir değişiklik gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="d5383-152">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="d5383-153">İfade ağacına tüm sabit içeriyorsa, sonuçta elde edilen ağaç yalnızca sabit değerini içeren `10`.</span><span class="sxs-lookup"><span data-stu-id="d5383-153">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="d5383-154">Derleyici tüm ek gerçekleştirir ve en basit biçimiyle ifade azaltır.</span><span class="sxs-lookup"><span data-stu-id="d5383-154">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="d5383-155">Yalnızca ifade bir değişken eklemek, özgün ağaç görmek yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="d5383-155">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="d5383-156">Bir ziyaretçi için bu toplam oluşturun ve ziyaretçi çalıştırmak, bu çıktı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="d5383-156">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="d5383-157">Ayrıca, herhangi diğer örnekleri ziyaretçi kodda çalıştırma ve temsil ettiği hangi ağaç bakın.</span><span class="sxs-lookup"><span data-stu-id="d5383-157">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="d5383-158">Bir örneği burada verilmiştir `sum3` ifadesiyle yukarıda (sabiti computing derleyiciye önlemek için ek bir parametre):</span><span class="sxs-lookup"><span data-stu-id="d5383-158">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="d5383-159">Ziyaretçi çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d5383-159">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="d5383-160">Parantez çıkış parçası olmayan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="d5383-160">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="d5383-161">Giriş ifadesi parantezlerde temsil eden düğümleri ifade ağacında yoktur.</span><span class="sxs-lookup"><span data-stu-id="d5383-161">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="d5383-162">İfade ağaç yapısını öncelik iletişim kurmak gerekli tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="d5383-162">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="d5383-163">Bu örnekten genişletme</span><span class="sxs-lookup"><span data-stu-id="d5383-163">Extending from this sample</span></span>

<span data-ttu-id="d5383-164">Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="d5383-164">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="d5383-165">Bu bölümde görülen kod yalnızca sabit tamsayılar ve ikili işleme `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="d5383-165">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="d5383-166">Son bir örnek olarak, daha karmaşık bir ifade işlemek için ziyaretçi şimdi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="d5383-166">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="d5383-167">Bunun çalışması olalım:</span><span class="sxs-lookup"><span data-stu-id="d5383-167">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="d5383-168">Bu kod matematiksel için bir olası uygulamasını temsil eder *faktöriyelini* işlevi.</span><span class="sxs-lookup"><span data-stu-id="d5383-168">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="d5383-169">Bu kod yazılmış şekilde ifadeleri için lambda ifadeleri atayarak ifade ağaçları oluşturmanın iki limitiations vurgular.</span><span class="sxs-lookup"><span data-stu-id="d5383-169">The way I've written this code highlights two limitiations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="d5383-170">İlk olarak, deyimi Lambda'lar izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="d5383-170">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="d5383-171">Anlamına ı blokları, döngüleri kullanamazsınız, / else ifadeleri ve diğer denetim yapıları C# ' ta ortak.</span><span class="sxs-lookup"><span data-stu-id="d5383-171">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="d5383-172">I ifadeleri kullanmayla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5383-172">I'm limited to using expressions.</span></span> <span data-ttu-id="d5383-173">İkinci olarak, yinelemeli olarak çağrı aynı ifadeye bağlanamıyorum.</span><span class="sxs-lookup"><span data-stu-id="d5383-173">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="d5383-174">I sanki zaten bir temsilci, ancak kendi ifade ağaç biçiminde çağrılamıyor verebilir.</span><span class="sxs-lookup"><span data-stu-id="d5383-174">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="d5383-175">Bölümünde [ifade ağaçlar derleyen](expression-trees-building.md) bu sınırlamaların üstesinden gelmek için tekniklerini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d5383-175">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="d5383-176">Bu ifadede düğümleri her türlü karşılaşacağınız:</span><span class="sxs-lookup"><span data-stu-id="d5383-176">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="d5383-177">Eşittir (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="d5383-177">Equal (binary expression)</span></span>
2. <span data-ttu-id="d5383-178">Çarp (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="d5383-178">Multiply (binary expression)</span></span>
3. <span data-ttu-id="d5383-179">Koşullu (?</span><span class="sxs-lookup"><span data-stu-id="d5383-179">Conditional (the ?</span></span> <span data-ttu-id="d5383-180">: ifade)</span><span class="sxs-lookup"><span data-stu-id="d5383-180">: expression)</span></span>
4. <span data-ttu-id="d5383-181">Yöntem çağrısı ifade (çağırma `Range()` ve `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="d5383-181">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="d5383-182">Ziyaretçi algoritmayı değiştirmek için bir yoldur, yürütülmekte tutmak ve ulaşana her zaman düğüm türü yazmak için `default` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d5383-182">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="d5383-183">Birkaç yinelemeden sonra olası düğümlerinin her biri görülür.</span><span class="sxs-lookup"><span data-stu-id="d5383-183">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="d5383-184">Daha sonra tüm yapmanız gereken sağlayın.</span><span class="sxs-lookup"><span data-stu-id="d5383-184">Then, you have all you need.</span></span> <span data-ttu-id="d5383-185">Sonuç şöyle olacaktır:</span><span class="sxs-lookup"><span data-stu-id="d5383-185">The result would be something like this:</span></span>

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

<span data-ttu-id="d5383-186">ConditionalVisitor ve MethodCallVisitor iki düğümleri işlem:</span><span class="sxs-lookup"><span data-stu-id="d5383-186">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="d5383-187">Ve ifade ağacına çıktı şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="d5383-187">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="d5383-188">Örnek kitaplığını genişletme</span><span class="sxs-lookup"><span data-stu-id="d5383-188">Extending the Sample Library</span></span>

<span data-ttu-id="d5383-189">Bu bölümdeki örnekler ziyaret edin ve bir ifade ağacına düğümler incelemek için çekirdek teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5383-189">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="d5383-190">Ziyaret eden ve bir ifade ağacına düğümler erişim çekirdek görevlerde yoğunlaşmak için gerekebilecek birçok Eylemler üzerinden glossed.</span><span class="sxs-lookup"><span data-stu-id="d5383-190">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="d5383-191">İlk olarak, ziyaretçi yalnızca tamsayı olduğunu sabitleri işleyin.</span><span class="sxs-lookup"><span data-stu-id="d5383-191">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="d5383-192">Sabit değerler herhangi bir sayısal tür olabilir ve dönüşümler ve bu türleri arasındaki promosyonlar C# dili destekler.</span><span class="sxs-lookup"><span data-stu-id="d5383-192">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="d5383-193">Bu kodu daha sağlam bir sürümü bu olanaklarına yansıtma.</span><span class="sxs-lookup"><span data-stu-id="d5383-193">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="d5383-194">Bile son örnek bir alt olası düğüm türü tanır.</span><span class="sxs-lookup"><span data-stu-id="d5383-194">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="d5383-195">Yine başarısız olmasına neden olacak birçok ifadeleri besleyebilecek.</span><span class="sxs-lookup"><span data-stu-id="d5383-195">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="d5383-196">Tam bir uygulamaya .NET standart adı altında yer aldığı [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) ve tüm olası düğüm türleri işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="d5383-196">A full implementation is included in the .NET Standard under the name [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) and can handle all the possible node types.</span></span>

<span data-ttu-id="d5383-197">Son olarak, bu makalede kullanılan kitaplığı tanıtım ve öğrenme için yapılmıştı.</span><span class="sxs-lookup"><span data-stu-id="d5383-197">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="d5383-198">Bunu getirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="d5383-198">It's not optimized.</span></span> <span data-ttu-id="d5383-199">I yapıları olmak için açıkça, teknikler vurgulamak için düğümleri ziyaret edin ve ne olduğunu analiz etmek için kullanılır ve yazıldı.</span><span class="sxs-lookup"><span data-stu-id="d5383-199">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="d5383-200">Bir üretim uygulaması g'den daha fazla performans dikkat edilmesi.</span><span class="sxs-lookup"><span data-stu-id="d5383-200">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="d5383-201">Bu kısıtlamalarla bile okuduğunuzdan ve anladığınızdan ifade ağaçları algoritmaları yazma iyi yolunuzu üzerinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5383-201">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="d5383-202">Sonraki--İfade oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5383-202">Next -- Building Expressions</span></span>](expression-trees-building.md)
