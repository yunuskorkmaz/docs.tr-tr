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
# <a name="interpreting-expressions"></a><span data-ttu-id="f44a0-103">İfade yorumlama</span><span class="sxs-lookup"><span data-stu-id="f44a0-103">Interpreting Expressions</span></span>

[<span data-ttu-id="f44a0-104">Önceki--İfade yürütme</span><span class="sxs-lookup"><span data-stu-id="f44a0-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="f44a0-105">Şimdi, yapısını incelemek için biraz kod yazalım bir *ifade ağacı*.</span><span class="sxs-lookup"><span data-stu-id="f44a0-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="f44a0-106">Türetilen bir sınıfın bir nesnesi bir ifade ağacı kümedeki her düğüm olacaktır `Expression`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="f44a0-107">Bu tasarım, bir ifade ağacı bir göreceli olarak doğrudan iletme özyinelemeli işlemi tüm düğümlerin ziyaret yapar.</span><span class="sxs-lookup"><span data-stu-id="f44a0-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="f44a0-108">Genel kök düğümünde başlatmak ve ne tür bir düğümü olduğu belirlemek için stratejisidir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="f44a0-109">Düğüm türü, alt öğe varsa, yinelemeli olarak alt ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="f44a0-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="f44a0-110">Her alt düğümü kök düğümde kullanılan işlemi tekrarlayın: türünü belirlemeye ve alt türü varsa, her alt ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="f44a0-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="f44a0-111">Alt öğe ile bir ifade İnceleme</span><span class="sxs-lookup"><span data-stu-id="f44a0-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="f44a0-112">Her bir çok basit bir ifade ağacı düğümünde bağlanarak başlayalım.</span><span class="sxs-lookup"><span data-stu-id="f44a0-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="f44a0-113">Sabit bir ifade oluşturur ve ardından özelliklerini inceler kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f44a0-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="f44a0-114">Aşağıdaki yazdırır:</span><span class="sxs-lookup"><span data-stu-id="f44a0-114">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="f44a0-115">Şimdi, bu ifadeyi inceleyin ve bu konuda bazı önemli özellikleri yazma kod yazalım.</span><span class="sxs-lookup"><span data-stu-id="f44a0-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="f44a0-116">Bu kod şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f44a0-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="f44a0-117">Basit bir toplama ifadesi İnceleme</span><span class="sxs-lookup"><span data-stu-id="f44a0-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="f44a0-118">Bu bölümde giriş toplama örnekten başlayalım.</span><span class="sxs-lookup"><span data-stu-id="f44a0-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="f44a0-119">Değil kullanıyorum `var` ataması sağ tarafında örtük mümkün değildir, çünkü gibi bu ifade ağacı bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="f44a0-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="f44a0-120">Bu daha derin bir şekilde anlamak için okuma [burada](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f44a0-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="f44a0-121">Kök düğüm bir `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="f44a0-122">Sağ tarafta ilginç kod ürününü `=>` işleci, bir alt öğeleri bulmak için ihtiyacınız `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="f44a0-123">Bu bölümdeki tüm ifadeler ile bunu.</span><span class="sxs-lookup"><span data-stu-id="f44a0-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="f44a0-124">Üst düğümün dönüş türünü bulmamıza yardımcı `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="f44a0-125">Her düğüm bu ifade incelemek için yinelemeli olarak düğüm sayısı inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="f44a0-126">Basit bir ilk uygulama şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="f44a0-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="f44a0-127">Bu örnek aşağıdaki çıkışı yazdırır:</span><span class="sxs-lookup"><span data-stu-id="f44a0-127">This sample prints the following output:</span></span>

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

<span data-ttu-id="f44a0-128">Yukarıdaki kod örneğinde yineleme çok fazla fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="f44a0-129">Şimdi, temizleme ve daha genel amaçlı bir derleme ifade düğümü ziyaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f44a0-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="f44a0-130">Bir önyinelemeli algoritmanız yazma bırakmamızı zordur.</span><span class="sxs-lookup"><span data-stu-id="f44a0-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="f44a0-131">Herhangi bir düğümün alt öğeleri olabilir bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="f44a0-132">Alt öğelere sahip herhangi bir düğüm alt ziyaret edin ve o düğümde belirlemek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="f44a0-133">İşte Temizlenen toplama işlemleri ziyaret etmek için özyineleme yararlanan sürüm:</span><span class="sxs-lookup"><span data-stu-id="f44a0-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="f44a0-134">Bu algoritma herhangi bir rastgele ziyaret edebileceği bir algoritma temelidir `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="f44a0-135">Yani kod yalnızca oluşturduğum olası ayarlar, karşılaşabileceğiniz ifade ağacı düğümlerinin çok küçük bir örnek için görünür, çok sayıda açıkları vardır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="f44a0-136">Ancak, yine de bir bit bu üretir öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="f44a0-137">(Varsayılan durumda `Visitor.CreateFromExpression` yöntemi yeni bir düğüm türü ile karşılaşıldığında bir ileti hata konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="f44a0-138">Bu şekilde, yeni bir ifade türü eklemek için bildiğiniz.)</span><span class="sxs-lookup"><span data-stu-id="f44a0-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="f44a0-139">Yukarıda gösterilen ek ifade üzerinde bu ziyaretçi çalıştırdığınızda, aşağıdaki çıkışı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="f44a0-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="f44a0-140">Daha genel bir ziyaretçi uygulaması oluşturduğunuza göre ziyaret edin ve çok daha farklı türde ifadeler işlem.</span><span class="sxs-lookup"><span data-stu-id="f44a0-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="f44a0-141">Birçok düzeyine sahip bir toplama ifadesi İnceleme</span><span class="sxs-lookup"><span data-stu-id="f44a0-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="f44a0-142">Şimdi daha karmaşık bir örnek deneyin, ancak hala düğüm türü için yalnızca toplama sınırla:</span><span class="sxs-lookup"><span data-stu-id="f44a0-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="f44a0-143">Bu ziyaretçi algoritmasına çalıştırmadan önce çıkış gerçekleştirmekte zorlanabilecek kullanıma çalışmak için bir düşünce alıştırma deneyin.</span><span class="sxs-lookup"><span data-stu-id="f44a0-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="f44a0-144">Unutmayın `+` işleci, bir *ikili işleç*: iki alt, sol ve sağ işlenen temsil eden olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="f44a0-145">Doğru bir ağaç oluşturmak için olası birkaç yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="f44a0-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="f44a0-146">En olası vurgulamak için iki olası yanıt içine ayrımı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="f44a0-147">İlk temsil *sağdan birleşir* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="f44a0-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="f44a0-148">İkinci temsil *ilişkilendirilebilir sol* ifadeler.</span><span class="sxs-lookup"><span data-stu-id="f44a0-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="f44a0-149">Her iki bu iki biçim biçimi ek ifadeleri rastgele dilediğiniz sayıda ölçeklendirir avantajlarındandır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="f44a0-150">Bu ifade ziyaretçi yoluyla çalıştırırsanız, bu Bu çıktı, basit bir toplama ifadesi olduğu doğrulanıyor görürsünüz *ilişkilendirilebilir sol*.</span><span class="sxs-lookup"><span data-stu-id="f44a0-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="f44a0-151">Bu örneği çalıştırmak ve tam ifade ağacı görmek için ı kaynak ifade ağacına değişiklik yapmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="f44a0-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="f44a0-152">İfade ağacı, tüm sabit içeriyorsa, sonuç ağacı yalnızca sabit değerini içeren `10`.</span><span class="sxs-lookup"><span data-stu-id="f44a0-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="f44a0-153">Derleyici, tüm ek gerçekleştirir ve en basit haliyle ifade azaltır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="f44a0-154">Bir değişkeni ifade yalnızca ekleme, özgün ağaç görmek yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="f44a0-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="f44a0-155">Bir ziyaretçi için bu toplam oluşturun ve ziyaretçi çalıştırmak, bu Çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="f44a0-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="f44a0-156">Ayrıca, diğer örneklerden birini ziyaretçi kodda çalıştırma ve temsil ettiği hangi ağaç görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="f44a0-157">İşte bir örnek `sum3` yukarıda bir ifade (ile ek bir parametre, derleyici sabiti bilgi işlem gelen önlemek için):</span><span class="sxs-lookup"><span data-stu-id="f44a0-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="f44a0-158">Ziyaretçi çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f44a0-158">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="f44a0-159">Parantezler çıkış parçası olmadığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f44a0-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="f44a0-160">Parantez içinde giriş ifadesi temsil eden düğümler ifade ağacında yoktur.</span><span class="sxs-lookup"><span data-stu-id="f44a0-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="f44a0-161">İfade ağacı yapısını önceliği iletişim kurmak gerekli tüm bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="f44a0-162">Bu örnekten genişletme</span><span class="sxs-lookup"><span data-stu-id="f44a0-162">Extending from this sample</span></span>

<span data-ttu-id="f44a0-163">Örnek yalnızca en ilkel ifade ağaçları ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="f44a0-164">Bu bölümde görülen kodu yalnızca sabit tamsayı ve ikili işler `+` işleci.</span><span class="sxs-lookup"><span data-stu-id="f44a0-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="f44a0-165">Son örnek, daha karmaşık bir ifadeyi işlemek için ziyaretçi güncelleştirelim.</span><span class="sxs-lookup"><span data-stu-id="f44a0-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="f44a0-166">Bunun için işe olalım:</span><span class="sxs-lookup"><span data-stu-id="f44a0-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="f44a0-167">Bu kod için matematiksel bir olası uygulama temsil eden *faktöriyelini* işlevi.</span><span class="sxs-lookup"><span data-stu-id="f44a0-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="f44a0-168">Bu kod yazılan şekilde ifade ağaçları ifadeleri lambda ifadeleri atayarak oluşturmanın iki sınırlamaları vurgular.</span><span class="sxs-lookup"><span data-stu-id="f44a0-168">The way I've written this code highlights two limitiations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="f44a0-169">İlk olarak, deyim lambdaları izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f44a0-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="f44a0-170">Anlamı miyim blokları, döngüleri kullanamazsınız, / else ifadeleri ve diğer denetim yapıları C# ' de ortak.</span><span class="sxs-lookup"><span data-stu-id="f44a0-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="f44a0-171">İfadeler için faturalamayı ortağıyım.</span><span class="sxs-lookup"><span data-stu-id="f44a0-171">I'm limited to using expressions.</span></span> <span data-ttu-id="f44a0-172">İkinci olarak, yinelemeli olarak çağrısı aynı ifadede bağlanamıyorum.</span><span class="sxs-lookup"><span data-stu-id="f44a0-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="f44a0-173">Ben sanki zaten bir temsilci, ancak kendi ifade ağaç biçiminde çağrılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="f44a0-174">Bölümünde [ifade ağaçları oluşturma](expression-trees-building.md) bu sınırlamaların üstesinden gelmek için tekniklerini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f44a0-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="f44a0-175">Bu ifade, her türden düğümleri karşılaşacağınız:</span><span class="sxs-lookup"><span data-stu-id="f44a0-175">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="f44a0-176">Eşittir (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="f44a0-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="f44a0-177">Çarpma (ikili ifade)</span><span class="sxs-lookup"><span data-stu-id="f44a0-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="f44a0-178">Koşullu (?</span><span class="sxs-lookup"><span data-stu-id="f44a0-178">Conditional (the ?</span></span> <span data-ttu-id="f44a0-179">: ifade)</span><span class="sxs-lookup"><span data-stu-id="f44a0-179">: expression)</span></span>
4. <span data-ttu-id="f44a0-180">Yöntem çağrısı ifadesi (çağırma `Range()` ve `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="f44a0-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="f44a0-181">Ziyaretçi algoritması değiştirmek için bir yoludur yürütme tutun ve ulaştığınız zaman her düğüm türü yazmak için `default` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f44a0-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="f44a0-182">Birkaç yinelemenin ardından olası düğümlerinin her biri görülür.</span><span class="sxs-lookup"><span data-stu-id="f44a0-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="f44a0-183">Daha sonra ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-183">Then, you have all you need.</span></span> <span data-ttu-id="f44a0-184">Sonuç aşağıdakine benzer olacaktır:</span><span class="sxs-lookup"><span data-stu-id="f44a0-184">The result would be something like this:</span></span>

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

<span data-ttu-id="f44a0-185">Bu iki düğüm ConditionalVisitor ve MethodCallVisitor İşle:</span><span class="sxs-lookup"><span data-stu-id="f44a0-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="f44a0-186">Ve ifade ağacı için çıktı aşağıdaki gibi olur:</span><span class="sxs-lookup"><span data-stu-id="f44a0-186">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="f44a0-187">Örnek kitaplığını genişletme</span><span class="sxs-lookup"><span data-stu-id="f44a0-187">Extending the Sample Library</span></span>

<span data-ttu-id="f44a0-188">Bu bölümdeki örnekler ziyaret edin ve bir ifade ağacı düğümler incelemek için çekirdek teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="f44a0-189">Ziyaret edin ve bir ifade ağacı düğümler erişim temel görevler üzerinde yoğunlaşmak için ihtiyacınız olabilecek birçok eylemi üzerinden glossed.</span><span class="sxs-lookup"><span data-stu-id="f44a0-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="f44a0-190">İlk olarak, ziyaretçi yalnızca ise tamsayı sabitleri işleyin.</span><span class="sxs-lookup"><span data-stu-id="f44a0-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="f44a0-191">Herhangi bir sayısal tür sabit değerler olabilir ve dönüştürmeler ve promosyonlar bu türler arasında C# dili destekler.</span><span class="sxs-lookup"><span data-stu-id="f44a0-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="f44a0-192">Bu kod daha sağlam bir sürümü, tüm bu özellikler yansıtma.</span><span class="sxs-lookup"><span data-stu-id="f44a0-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="f44a0-193">Bile son örnek, bir alt kümesini olası düğüm türleri tanır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="f44a0-194">Yine de başarısız olmasına neden olacak çok sayıda ifadeleri besleyebilecek.</span><span class="sxs-lookup"><span data-stu-id="f44a0-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="f44a0-195">.NET Standard'da adı altında tam bir uygulamaya dahil <xref:System.Linq.Expressions.ExpressionVisitor> ve tüm olası düğüm türleri işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="f44a0-196">Son olarak, bu makaledeki kullandım kitaplığı, tanıtım ve öğrenme için oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f44a0-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="f44a0-197">Bu duruma getirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="f44a0-197">It's not optimized.</span></span> <span data-ttu-id="f44a0-198">Yapıları olmak için çok kullanılan ve teknikler vurgulamak için düğümleri ziyaret edin ve ne olduğunu çözümlemek için kullanılan yazdığım.</span><span class="sxs-lookup"><span data-stu-id="f44a0-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="f44a0-199">Bir üretim uygulamanız sahibim çok daha fazla performans dikkat.</span><span class="sxs-lookup"><span data-stu-id="f44a0-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="f44a0-200">Bu kısıtlamalarla bile okumanız ve anlamanız ifade ağaçları algoritmalar yazma iyi yolunuzu üzerinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f44a0-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="f44a0-201">Sonraki--İfade oluşturma</span><span class="sxs-lookup"><span data-stu-id="f44a0-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
