---
title: Bina İfade Ağaçları
description: İfade ağaçları oluşturma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146053"
---
# <a name="building-expression-trees"></a><span data-ttu-id="805b7-103">Bina İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="805b7-103">Building Expression Trees</span></span>

[<span data-ttu-id="805b7-104">Önceki -- İfadeleri Yorumlama</span><span class="sxs-lookup"><span data-stu-id="805b7-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="805b7-105">Şimdiye kadar gördüğünüz tüm ifade ağaçları C# derleyicisi tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="805b7-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="805b7-106">Yapmanız gereken tek şey bir veya benzer tür olarak yazılan bir `Expression<Func<T>>` değişkene atanan bir lambda ifadesi oluşturmaktı.</span><span class="sxs-lookup"><span data-stu-id="805b7-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="805b7-107">İfade ağacı oluşturmanın tek yolu bu değil.</span><span class="sxs-lookup"><span data-stu-id="805b7-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="805b7-108">Birçok senaryo için, çalışma zamanında bellekte bir ifade oluşturmanız gerektiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="805b7-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="805b7-109">Bina İfade Ağaçları bu ifade ağaçları değişmez olması ile karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="805b7-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="805b7-110">Değişmez olmak, ağacı yapraklardan köküne kadar oluşturmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="805b7-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="805b7-111">İfade ağaçları oluşturmak için kullanacağınız API'ler şu gerçeği yansıtır: Düğüm oluşturmak için kullanacağınız yöntemler tüm çocuklarını bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="805b7-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="805b7-112">Size teknikleri göstermek için birkaç örnek üzerinden yürüyelim.</span><span class="sxs-lookup"><span data-stu-id="805b7-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="805b7-113">Düğüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="805b7-113">Creating Nodes</span></span>

<span data-ttu-id="805b7-114">Göreceli olarak tekrar başlayalım.</span><span class="sxs-lookup"><span data-stu-id="805b7-114">Let's start relatively simply again.</span></span> <span data-ttu-id="805b7-115">Bu bölümlerboyunca üzerinde çalıştığım ek ifadeyi kullanacağız:</span><span class="sxs-lookup"><span data-stu-id="805b7-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="805b7-116">Bu ifade ağacı oluşturmak için, yaprak düğümleri inşa gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="805b7-117">Yaprak düğümleri sabittir, bu nedenle düğümleri oluşturmak için `Expression.Constant` yöntemi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="805b7-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="805b7-118">Ardından, ek ifadesini oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="805b7-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="805b7-119">Ek ifadeyi aldıktan sonra lambda ifadesini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="805b7-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="805b7-120">Bu çok basit bir lambda ifadesidir, çünkü hiçbir argüman içermez.</span><span class="sxs-lookup"><span data-stu-id="805b7-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="805b7-121">Bu bölümün ilerleyen bölümlerinde, bağımsız değişkenleri parametrelerle nasıl eşlediğinizi ve daha karmaşık ifadeler nasıl oluşturacağınızı göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="805b7-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="805b7-122">Bu kadar basit ifadeler için, tüm çağrıları tek bir deyimde birleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="805b7-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="805b7-123">Ağaç İnşa Etmek</span><span class="sxs-lookup"><span data-stu-id="805b7-123">Building a Tree</span></span>

<span data-ttu-id="805b7-124">Bu bellekte bir ifade ağacı oluşturmanın temelleridir.</span><span class="sxs-lookup"><span data-stu-id="805b7-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="805b7-125">Daha karmaşık ağaçlar genellikle daha fazla düğüm türleri ve ağaçta daha fazla düğüm anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="805b7-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="805b7-126">Bir örnek daha inceleyelim ve ifade ağaçları oluşturduğunuzda genellikle oluşturacağınız iki düğüm türü daha gösterelim: bağımsız değişken düğümleri ve yöntem çağrı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="805b7-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="805b7-127">Bu ifadeyi oluşturmak için bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="805b7-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="805b7-128">Parametre ifadeleri oluşturarak başlayacaksınız `x` ve: `y`</span><span class="sxs-lookup"><span data-stu-id="805b7-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="805b7-129">Çarpma ve ekleme ifadeleri oluşturma, daha önce gördüğünüz deseni izler:</span><span class="sxs-lookup"><span data-stu-id="805b7-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="805b7-130">Ardından, çağrı için bir yöntem arama ifadesi `Math.Sqrt`oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="805b7-131">Ve son olarak, bir lambda ifade içine yöntem arama koymak ve lambda ifade argümanlar tanımlamak için emin olun:</span><span class="sxs-lookup"><span data-stu-id="805b7-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="805b7-132">Bu daha karmaşık örnekte, genellikle ifade ağaçları oluşturmak için gereken birkaç teknik daha bakın.</span><span class="sxs-lookup"><span data-stu-id="805b7-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="805b7-133">İlk olarak, bunları kullanmadan önce parametreleri veya yerel değişkenleri temsil eden nesneleri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="805b7-134">Bu nesneleri oluşturduktan sonra, bunları istediğiniz yerde ifade ağacınızda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="805b7-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="805b7-135">İkinci olarak, bu yönteme erişmek için bir ifade `MethodInfo` ağacı oluşturabilmeniz için bir nesne oluşturmak için Yansıma API'lerinin bir alt kümesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="805b7-136">Kendinizi .NET Core platformunda bulunan Yansıma API'lerinin alt kümesiyle sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="805b7-137">Yine, bu teknikler diğer ifade ağaçları genişletecektir.</span><span class="sxs-lookup"><span data-stu-id="805b7-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="805b7-138">Derinlemesine Yapı Kodu</span><span class="sxs-lookup"><span data-stu-id="805b7-138">Building Code In Depth</span></span>

<span data-ttu-id="805b7-139">Bu API'leri kullanarak oluşturabilecekleriniz sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="805b7-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="805b7-140">Ancak, oluşturmak istediğiniz daha karmaşık ifade ağacı, kod yönetmek ve okumak için daha zor.</span><span class="sxs-lookup"><span data-stu-id="805b7-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="805b7-141">Bu kodun eşdeğeri olan bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="805b7-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="805b7-142">Yukarıda dikkat edin ben ifade ağacı inşa etmedi, ama sadece delege.</span><span class="sxs-lookup"><span data-stu-id="805b7-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="805b7-143">`Expression` Sınıfı kullanarak, ifade lambdas inşa edemez.</span><span class="sxs-lookup"><span data-stu-id="805b7-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="805b7-144">İşte aynı işlevselliği oluşturmak için gereken kod.</span><span class="sxs-lookup"><span data-stu-id="805b7-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="805b7-145">Bir `while` döngü oluşturmak için bir API olmaması, bunun yerine koşullu bir test içeren bir döngü ve döngüden çıkmak için bir etiket hedefi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="805b7-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

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

<span data-ttu-id="805b7-146">Faktöriyel işlev için ifade ağacı oluşturmak için kod biraz daha uzun, daha karmaşık, ve etiketler ilerler ve break ifadeleri ve günlük kodlama görevleri önlemek istiyorum diğer öğeleri ile delik deşik's.</span><span class="sxs-lookup"><span data-stu-id="805b7-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="805b7-147">Bu bölüm için, bu ifade ağacındaki her düğümü ziyaret etmek ve bu örnekte oluşturulan düğümler hakkında bilgi yazmak için ziyaretçi kodunu da güncelledim.</span><span class="sxs-lookup"><span data-stu-id="805b7-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="805b7-148">Örnek kodu dotnet/docs GitHub deposundan [görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/tree/master/csharp/expression-trees)</span><span class="sxs-lookup"><span data-stu-id="805b7-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="805b7-149">Örnekleri oluşturarak ve çalıştırarak kendiniz deneyin.</span><span class="sxs-lookup"><span data-stu-id="805b7-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="805b7-150">İndirme talimatları için [Örnekler ve Öğreticiler'e](../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="805b7-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="805b7-151">API'lerin incelenmesi</span><span class="sxs-lookup"><span data-stu-id="805b7-151">Examining the APIs</span></span>

<span data-ttu-id="805b7-152">İfade ağacı API'leri .NET Core'da gezinmek daha zor olanlardan bazılarıdır, ancak bu sorun değil.</span><span class="sxs-lookup"><span data-stu-id="805b7-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="805b7-153">Amaçları oldukça karmaşık bir girişimdir: çalışma zamanında kod üreten kod yazmak.</span><span class="sxs-lookup"><span data-stu-id="805b7-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="805b7-154">C# dilinde bulunan tüm kontrol yapılarını desteklemek ve API'lerin yüzey alanını makul olduğunca küçük tutmak arasında bir denge sağlamak için mutlaka karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="805b7-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="805b7-155">Bu denge, birçok denetim yapısının C# yapıları ile değil, derleyicinin bu üst düzey yapılardan oluşturduğu temel mantığı temsil eden yapılartarafından temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="805b7-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="805b7-156">Ayrıca, şu anda, doğrudan sınıf yöntemleri kullanılarak `Expression` oluşturulamayan C# ifadeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="805b7-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="805b7-157">Genel olarak, bunlar C# 5 ve C# 6'da eklenen en yeni işleçler ve ifadeler olacaktır.</span><span class="sxs-lookup"><span data-stu-id="805b7-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="805b7-158">(Örneğin, `async` ifadeler oluşturulamaz ve yeni `?.` işleç doğrudan oluşturulamaz.)</span><span class="sxs-lookup"><span data-stu-id="805b7-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="805b7-159">Sonraki -- İfadeleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="805b7-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
