---
title: "Yapı ifade ağaçları"
description: "İfade ağaçları oluşturma teknikleri hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c0d7bcf6e07f4a49e15e6f6f4e028eebfe82d8bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="building-expression-trees"></a><span data-ttu-id="06779-104">Yapı ifade ağaçları</span><span class="sxs-lookup"><span data-stu-id="06779-104">Building Expression Trees</span></span>

[<span data-ttu-id="06779-105">Önceki--İfadeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="06779-105">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="06779-106">Şu ana kadar gördüğünüz ifade ağaçları C# Derleyici tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="06779-106">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="06779-107">Tüm yapmanız gerekiyordu edildi olarak türünde bir değişkenden atandığı bir lambda ifadesi oluşturma bir `Expression<Func<T>>` veya bazı benzer türü.</span><span class="sxs-lookup"><span data-stu-id="06779-107">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="06779-108">Bir ifade ağacına oluşturmak için tek yolu değil.</span><span class="sxs-lookup"><span data-stu-id="06779-108">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="06779-109">Birçok senaryoları için bellek çalışma zamanında bir ifadede yapı gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06779-109">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="06779-110">İfade ağaçları oluşturma Bu ifade ağaçları değişmez gerçeğiyle karmaşık.</span><span class="sxs-lookup"><span data-stu-id="06779-110">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="06779-111">Kök kadar bırakır ağacından oluşturmalısınız olan değişmez anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06779-111">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="06779-112">İfade ağaçları oluşturmak için kullanmanız API'leri olgunun yansıtacak: bir düğüm oluşturmak için kullandığınız yöntemleri bağımsız olarak tüm alt öğelerini alın.</span><span class="sxs-lookup"><span data-stu-id="06779-112">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="06779-113">Şimdi teknikleri göstermek için birkaç örneklerle yol.</span><span class="sxs-lookup"><span data-stu-id="06779-113">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="06779-114">Düğümlerini oluşturma</span><span class="sxs-lookup"><span data-stu-id="06779-114">Creating Nodes</span></span>

<span data-ttu-id="06779-115">Görece basit başlayalım yeniden.</span><span class="sxs-lookup"><span data-stu-id="06779-115">Let's start relatively simply again.</span></span> <span data-ttu-id="06779-116">Bu bölümleri t ile çalışmakta Toplama ifadesi kullanacağız:</span><span class="sxs-lookup"><span data-stu-id="06779-116">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="06779-117">Bu ifade ağacına oluşturmak için ve yaprak düğümlerin oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06779-117">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="06779-118">Kullanabilmek için ve yaprak düğümlerin, sabittir `Expression.Constant` yöntemi düğümleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="06779-118">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="06779-119">Ardından, toplama ifadesi oluştur:</span><span class="sxs-lookup"><span data-stu-id="06779-119">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="06779-120">Toplama ifadesi getirdikten sonra lambda ifadesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="06779-120">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="06779-121">Bağımsız değişkenler içerdiğinden çok basit bir LambdaExpression budur.</span><span class="sxs-lookup"><span data-stu-id="06779-121">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="06779-122">Daha sonra bu bölümde, bağımsız değişkenler parametreleriyle eşleyin ve daha karmaşık ifadeleri oluşturmak nasıl görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="06779-122">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="06779-123">Bu bir basit ifadeler için tek bir deyimde tüm çağrılar birleştirmek:</span><span class="sxs-lookup"><span data-stu-id="06779-123">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="06779-124">Bir ağaç oluşturma</span><span class="sxs-lookup"><span data-stu-id="06779-124">Building a Tree</span></span>

<span data-ttu-id="06779-125">Bir ifade ağacına bellekte oluşturmanın temel olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="06779-125">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="06779-126">Daha karmaşık ağaçları genellikle daha fazla düğüm türleri ve daha fazla düğüm ağacında anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06779-126">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="06779-127">Şimdi aracılığıyla bir örnek daha çalıştırın ve ifade ağaçları oluşturduğunuzda, genellikle oluşturacaksınız iki daha fazla düğüm türleri göster: bağımsız değişken düğümleri ve yöntem çağrısı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="06779-127">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="06779-128">Şimdi bu deyim oluşturmak için bir ifade ağacına oluşturun:</span><span class="sxs-lookup"><span data-stu-id="06779-128">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="06779-129">Parametresi ifadelerine oluşturarak başlayacağız `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="06779-129">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="06779-130">Çarpma ve toplama ifadeleri oluşturma gördünüz deseni izler:</span><span class="sxs-lookup"><span data-stu-id="06779-130">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="06779-131">Ardından, bir yöntem çağrısı ifadesi çağrısı için oluşturmanız gerekir `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="06779-131">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="06779-132">Ve ardından son olarak, yöntem çağrısının bir lambda ifadesi yerleştirin ve bağımsız değişkenler lambda ifadesi tanımladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="06779-132">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="06779-133">Daha karmaşık Bu örnekte, genellikle ifade ağaçları oluşturmanız gerekir birkaç daha fazla teknikleri bakın.</span><span class="sxs-lookup"><span data-stu-id="06779-133">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="06779-134">İlk olarak, kullanmadan önce parametreleri veya yerel değişkenler temsil eden nesneler oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06779-134">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="06779-135">Bu nesneler oluşturduktan sonra ihtiyaç duyduğunuz her yerde bunları, ifade ağacına kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06779-135">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="06779-136">İkinci olarak, bir alt kümesini yansıma API'ları oluşturmak için kullanılacak ihtiyacınız bir `MethodInfo` o yöntemi erişimi için bir ifade ağacına oluşturabilmesi için nesne.</span><span class="sxs-lookup"><span data-stu-id="06779-136">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="06779-137">Kendiniz .NET Core platformda kullanılabilir yansıma API'leri alt sınırı, gerekir.</span><span class="sxs-lookup"><span data-stu-id="06779-137">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="06779-138">Yeniden, bu teknikler diğer ifade ağaçları uzatır.</span><span class="sxs-lookup"><span data-stu-id="06779-138">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="06779-139">Yapı kod derinliği:</span><span class="sxs-lookup"><span data-stu-id="06779-139">Building Code In Depth</span></span>

<span data-ttu-id="06779-140">Şunları yapabilirsiniz sınırlı değil bu API'leri kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06779-140">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="06779-141">Ancak, daha fazla kod okumak için ve yönetmek için zordur, oluşturmak istediğiniz ifade ağacına karmaşık.</span><span class="sxs-lookup"><span data-stu-id="06779-141">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="06779-142">Şimdi bu kodu eşdeğerdir bir ifade ağacına oluşturun:</span><span class="sxs-lookup"><span data-stu-id="06779-142">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="06779-143">Yukarıdaki ı ifade ağacına, ancak yalnızca temsilci yapı değil dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="06779-143">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="06779-144">Kullanarak `Expression` sınıfı, deyimi Lambda'lar oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="06779-144">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="06779-145">Aynı işlevselliği oluşturmak için gerekli kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="06779-145">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="06779-146">Derleme için bir API değil gerçeğiyle karmaşık bir `while` döngü, bunun yerine koşullu test ve dışında döngüsünü kesmek için bir etiket hedef içeren bir döngü yapı vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="06779-146">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="06779-147">Daha karmaşık, ifade ağacına Faktöriyel işlevi için yapı için kodu oldukça biraz daha uzun ve etiketleri ve sonu deyimleri ve diğer öğeleri önlemek için görevler kodlama bizim her gün içinde isteriz ile riddled.</span><span class="sxs-lookup"><span data-stu-id="06779-147">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="06779-148">Bu bölümde, t her düğüm bu ifade ağacına ziyaret edin ve bu örnekte oluşturulan düğümleri hakkında bilgi yazmak için ziyaretçi kod güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="06779-148">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="06779-149">Yapabilecekleriniz [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) dotnet/belgeler GitHub deposunda.</span><span class="sxs-lookup"><span data-stu-id="06779-149">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="06779-150">Kendiniz oluşturmak ve örnekleri çalıştırmak denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="06779-150">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="06779-151">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="06779-151">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="06779-152">API'ler inceleniyor</span><span class="sxs-lookup"><span data-stu-id="06779-152">Examining the APIs</span></span>

<span data-ttu-id="06779-153">İfade ağacına API'leri .NET Core gitmek daha zor bazıları, ancak sorun yoktur.</span><span class="sxs-lookup"><span data-stu-id="06779-153">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="06779-154">Bunların amaçla yerine karmaşık bir iş değil: çalışma zamanında kod oluşturur kod yazma.</span><span class="sxs-lookup"><span data-stu-id="06779-154">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="06779-155">Bunlar, mutlaka C# dilinde kullanılabilir tüm denetim yapıları destekleme ve API'ın yüzey alanını olabildiğince küçük makul tutma arasında bir denge sağlamak karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="06779-155">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="06779-156">Bu Bakiye birçok denetim yapıları kendi C# yapılarını tarafından değil, ancak bu daha yüksek düzeyli yapıları derleyici oluşturur temel mantığını temsil eden yapılar tarafından temsil edilen anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="06779-156">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="06779-157">Ayrıca, şu anda vardır kullanarak doğrudan oluşturulamıyor C# ifadeleri `Expression` sınıfı yöntemlerinin.</span><span class="sxs-lookup"><span data-stu-id="06779-157">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="06779-158">Genel olarak, bu yeni işleçler ve ifadeler C# 5 ve C# 6'da eklenmiş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="06779-158">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="06779-159">(Örneğin, `async` ifadeleri yerleşik olamaz ve yeni `?.` işleci doğrudan oluşturulamıyor.)</span><span class="sxs-lookup"><span data-stu-id="06779-159">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="06779-160">Sonraki--İfadeleri çevirme</span><span class="sxs-lookup"><span data-stu-id="06779-160">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
