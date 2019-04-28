---
title: Yapı ifade ağaçları
description: İfade ağaçları oluşturmaya yönelik teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646604"
---
# <a name="building-expression-trees"></a><span data-ttu-id="a44de-103">Yapı ifade ağaçları</span><span class="sxs-lookup"><span data-stu-id="a44de-103">Building Expression Trees</span></span>

[<span data-ttu-id="a44de-104">Önceki--İfade yorumlama</span><span class="sxs-lookup"><span data-stu-id="a44de-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="a44de-105">Görmüş kadarki tüm ifade ağaçları tarafından oluşturulan C# derleyici.</span><span class="sxs-lookup"><span data-stu-id="a44de-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="a44de-106">Tüm yapmanız gerekiyordu edildi olarak yazılmış bir değişkene atanmış bir lambda ifadesi oluşturma bir `Expression<Func<T>>` veya benzer bir tür.</span><span class="sxs-lookup"><span data-stu-id="a44de-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="a44de-107">İfade ağacı oluşturmak için tek yolu değil.</span><span class="sxs-lookup"><span data-stu-id="a44de-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="a44de-108">Birçok senaryo için çalışma zamanında bellekte bir ifade oluşturmak gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44de-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="a44de-109">Bu ifade ağaçları sabittir olgusu karmaşık ifade ağaçları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a44de-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="a44de-110">Kök kadar leaves ağacından derlemelidir olan sabit anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a44de-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="a44de-111">İfade ağaçları oluşturmak için kullanacağınız API'leri bu olgu yansıtır: Bir düğüm oluşturmak için kullanacağınız yöntemleri, bağımsız tüm alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="a44de-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="a44de-112">Teknikleri göstermek için bazı örnekler atalım.</span><span class="sxs-lookup"><span data-stu-id="a44de-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="a44de-113">Düğümler oluşturma</span><span class="sxs-lookup"><span data-stu-id="a44de-113">Creating Nodes</span></span>

<span data-ttu-id="a44de-114">Görece basit başlayalım yeniden.</span><span class="sxs-lookup"><span data-stu-id="a44de-114">Let's start relatively simply again.</span></span> <span data-ttu-id="a44de-115">Bu bölümleri miyim ile çalışmalar ek ifade kullanacağız:</span><span class="sxs-lookup"><span data-stu-id="a44de-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="a44de-116">Bu ifade ağacını oluşturmanın için yaprak düğümleri oluşturmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a44de-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="a44de-117">Kullanabileceğiniz sabitleri ve yaprak düğümlerin olduğundan `Expression.Constant` düğümleri oluşturma yöntemi:</span><span class="sxs-lookup"><span data-stu-id="a44de-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="a44de-118">Ardından, ek ifade oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="a44de-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="a44de-119">Ek ifade başladıktan sonra lambda ifadesi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a44de-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="a44de-120">Bağımsız değişken içeren çok basit bir lambda ifadesi, olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a44de-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="a44de-121">Daha sonra bu bölümde, parametreler için bağımsız değişken eşleme ve daha karmaşık ifadeleri oluşturmak nasıl göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a44de-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="a44de-122">Bu bir basit ifadeler için tek bir deyimde tüm çağırıyor Birleştir:</span><span class="sxs-lookup"><span data-stu-id="a44de-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="a44de-123">Bir ağaç oluşturma</span><span class="sxs-lookup"><span data-stu-id="a44de-123">Building a Tree</span></span>

<span data-ttu-id="a44de-124">Bellekte bir ifade ağacı oluşturma hakkındaki temel bilgileri olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a44de-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="a44de-125">Daha karmaşık ağaçlar genellikle daha fazla düğüm türleri ve daha fazla düğüm ağaçta anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a44de-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="a44de-126">Şimdi aracılığıyla daha fazla örneği çalıştırmak ve ifade ağaçları oluşturduğunuzda, genellikle oluşturacağınız iki daha fazla düğüm türleri göster: bağımsız değişken düğümleri ve yöntem çağrısı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="a44de-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="a44de-127">Bu ifade oluşturmak için bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="a44de-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="a44de-128">Parametresi ifadelerine için oluşturarak başlayacağız `x` ve `y`:</span><span class="sxs-lookup"><span data-stu-id="a44de-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="a44de-129">Çarpma ve ayrıca ifadeleri oluşturma gördünüz deseni izler:</span><span class="sxs-lookup"><span data-stu-id="a44de-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="a44de-130">Ardından, bir yöntem çağrısı ifadesi için yapılan çağrının oluşturmak için ihtiyacınız `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="a44de-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="a44de-131">Ve son olarak, yöntem çağrısının bir lambda ifadesine yerleştirin, lambda ifadesine bağımsız değişkenler tanımladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="a44de-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="a44de-132">Bu daha karmaşık bir örnekte, ifade ağacı oluşturmak için genellikle gereken birkaç daha fazla teknikleri bakın.</span><span class="sxs-lookup"><span data-stu-id="a44de-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="a44de-133">İlk olarak, kullanmadan önce parametrelerin veya yerel değişkenleri temsil eden nesneleri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a44de-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="a44de-134">Bu nesneler oluşturduktan sonra istediğiniz yerden onları, ifade ağacında kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44de-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="a44de-135">İkinci olarak, yansıma API kümesini oluşturmak için kullanılacak ihtiyacınız bir `MethodInfo` bu yönteme erişmek için bir ifade ağacı oluşturabilmesi nesne.</span><span class="sxs-lookup"><span data-stu-id="a44de-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="a44de-136">Kendiniz bir .NET Core platformda kullanılabilir yansıma API'lerden alt sınırı, gerekir.</span><span class="sxs-lookup"><span data-stu-id="a44de-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="a44de-137">Yeniden, bu teknikler diğer ifade ağaçlarına genişletilir.</span><span class="sxs-lookup"><span data-stu-id="a44de-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="a44de-138">Derinlemesine kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="a44de-138">Building Code In Depth</span></span>

<span data-ttu-id="a44de-139">Şunları yapabilirsiniz sınırlı olmayan bu API'leri kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a44de-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="a44de-140">Ancak, daha zordur yönetmek ve okuma için kodudur, oluşturmak istediğiniz bir ifade ağacı çok karmaşık.</span><span class="sxs-lookup"><span data-stu-id="a44de-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="a44de-141">Bu kod eşdeğerdir bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="a44de-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="a44de-142">Yukarıda miyim ifade ağacı, ancak yalnızca temsilci derlenmedi, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a44de-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="a44de-143">Kullanarak `Expression` sınıfı, deyim lambdaları oluşturamıyor.</span><span class="sxs-lookup"><span data-stu-id="a44de-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="a44de-144">Aynı işlevselliği oluşturmak için gereken kod aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="a44de-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="a44de-145">Bir API oluşturmak için hiç olgusu karmaşık bir `while` döngü, bunun yerine bir koşul testi ve etiket hedefi döngüden içeren bir döngü oluşturmak için ihtiyacınız.</span><span class="sxs-lookup"><span data-stu-id="a44de-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="a44de-146">İfade ağacı Faktöriyel işlevi oluşturmak için kodu daha karmaşık, oldukça biraz daha uzun ve etiketleri kesme deyimleri ve diğer öğeleri önlemek için kodlama görevleri, her gün içinde istiyoruz riddled.</span><span class="sxs-lookup"><span data-stu-id="a44de-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="a44de-147">Bu bölüm için miyim ziyaretçi kod, her düğüm bu ifade ağacı ziyaret edin ve bu örnekte oluşturulan düğümleri hakkında bilgi yazmak için de güncelleştirdik.</span><span class="sxs-lookup"><span data-stu-id="a44de-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="a44de-148">Yapabilecekleriniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) dotnet/docs GitHub deposunda bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a44de-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="a44de-149">Oluşturma ve örnekleri çalıştırmaya kendiniz denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="a44de-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="a44de-150">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a44de-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="a44de-151">API'leri İnceleme</span><span class="sxs-lookup"><span data-stu-id="a44de-151">Examining the APIs</span></span>

<span data-ttu-id="a44de-152">İfade ağacı API'leri de .NET Core giderek daha zor bazıları, ancak, bir sakınca yoktur.</span><span class="sxs-lookup"><span data-stu-id="a44de-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="a44de-153">Bunların amacı yerine karmaşık bir iştir: çalışma zamanında kodu oluşturan kod yazma.</span><span class="sxs-lookup"><span data-stu-id="a44de-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="a44de-154">Kullanılabilir tüm denetim yapıları destekleyen arasında bir denge sağlamak mutlaka karmaşık oldukları C# dil ve yüzey alanını olabildiğince küçük API'leri gibi makul tutma.</span><span class="sxs-lookup"><span data-stu-id="a44de-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="a44de-155">Birçok denetim yapıları tarafından temsil edilen bu dengeyi anlamına gelir, C# oluşturur, ancak bu daha yüksek bir düzeyinden derleyici oluşturan temel mantığı göstermek yapıları tarafından oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a44de-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="a44de-156">Ayrıca, şu anda vardır C# kullanarak doğrudan oluşturulamıyor ifadeleri `Expression` sınıfı yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="a44de-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="a44de-157">Genel olarak, bunlar yeni işleçleri olacaktır ve ifadeleri eklenen içinde C# 5 ve C# 6.</span><span class="sxs-lookup"><span data-stu-id="a44de-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="a44de-158">(Örneğin, `async` ifadeleri yerleşik olamaz ve yeni `?.` işleci doğrudan oluşturulamıyor.)</span><span class="sxs-lookup"><span data-stu-id="a44de-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="a44de-159">Sonraki--İfade çevirme</span><span class="sxs-lookup"><span data-stu-id="a44de-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
