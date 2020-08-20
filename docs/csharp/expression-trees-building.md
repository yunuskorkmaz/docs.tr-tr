---
title: Ifade ağaçları oluşturma
description: İfade ağaçları oluşturma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c153ca2c75738571c81057364390f489d2decb05
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656156"
---
# <a name="building-expression-trees"></a><span data-ttu-id="b6bc7-103">Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6bc7-103">Building Expression Trees</span></span>

[<span data-ttu-id="b6bc7-104">Önceki--Ifadeleri yorumlama</span><span class="sxs-lookup"><span data-stu-id="b6bc7-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="b6bc7-105">Şimdiye kadar gördüğünüz tüm ifade ağaçları C# derleyicisi tarafından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="b6bc7-106">Tek yapmanız gereken, veya benzer bir tür olarak yazılmış bir değişkene atanan bir lambda ifadesi oluşturmaktır `Expression<Func<T>>` .</span><span class="sxs-lookup"><span data-stu-id="b6bc7-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="b6bc7-107">Bu, bir ifade ağacı oluşturmanın tek yolu değildir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="b6bc7-108">Birçok senaryoda, çalışma zamanında bellekte bir ifade oluşturmanız gerektiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="b6bc7-109">Ifade ağaçları oluşturma, bu ifade ağaçlarının sabit olması olgusuna göre karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="b6bc7-110">Sabit olması, ağacın köke kadar olan yaprakları oluşturmanız gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="b6bc7-111">İfade ağaçları oluşturmak için kullanacağınız API 'Ler bu olguyu yansıtır: bir düğüm oluşturmak için kullanacağınız Yöntemler tüm alt öğelerini bağımsız değişken olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="b6bc7-112">Aşağıda, teknikleri göstermek için birkaç örnek yürülim.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="b6bc7-113">Düğüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6bc7-113">Creating Nodes</span></span>

<span data-ttu-id="b6bc7-114">Yine de nispeten daha başlayalım.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-114">Let's start relatively simply again.</span></span> <span data-ttu-id="b6bc7-115">Bu bölümlerin tamamında üzerinde çalıştık ekleme ifadesini kullanacağız:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="b6bc7-116">Bu ifade ağacını oluşturmak için yaprak düğümleri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="b6bc7-117">Yaprak düğümler sabittir, bu sayede `Expression.Constant` düğümleri oluşturmak için yöntemini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="b6bc7-118">Daha sonra, toplama ifadesi oluşturacaksınız:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="b6bc7-119">Toplama ifadesini aldıktan sonra lambda ifadesini oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="b6bc7-120">Bağımsız değişken içermediğinden bu çok basit bir lambda ifadesidir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="b6bc7-121">Bu bölümde daha sonra, bağımsız değişkenlerin parametrelere nasıl eşlendiğini ve daha karmaşık ifadeler nasıl oluşturulacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="b6bc7-122">Bu kadar basit olan ifadeler için tüm çağrıları tek bir deyim halinde birleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="b6bc7-123">Ağaç oluşturma</span><span class="sxs-lookup"><span data-stu-id="b6bc7-123">Building a Tree</span></span>

<span data-ttu-id="b6bc7-124">Bu, bellekte bir ifade ağacı oluşturmanın temel larıdır.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="b6bc7-125">Daha karmaşık ağaçlar genellikle daha fazla düğüm türü ve ağaçta daha fazla düğüm anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="b6bc7-126">Daha sonra bir örnek daha çalıştıralım ve genellikle ifade ağaçları oluştururken oluşturacağınız iki düğüm türü gösterelim: bağımsız değişken düğümleri ve yöntem çağrı düğümleri.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="b6bc7-127">Bu ifadeyi oluşturmak için bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="b6bc7-128">Ve için parametre ifadeleri oluşturarak başlayacaksınız `x` `y` :</span><span class="sxs-lookup"><span data-stu-id="b6bc7-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="b6bc7-129">Çarpma ve ekleme ifadelerinin oluşturulması, zaten gördüğünüz kalıbı izler:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="b6bc7-130">Ardından, çağrısı için bir yöntem çağrısı ifadesi oluşturmanız gerekir `Math.Sqrt` .</span><span class="sxs-lookup"><span data-stu-id="b6bc7-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="b6bc7-131">Son olarak, yöntem çağrısını bir lambda ifadesine yerleştirir ve lambda ifadesinin bağımsız değişkenlerini tanımladığınızdan emin olun:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="b6bc7-132">Bu daha karmaşık örnekte, genellikle ifade ağaçları oluşturmanız için gereken birkaç teknik görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="b6bc7-133">İlk olarak, parametreleri veya yerel değişkenleri kullanmadan önce bunları temsil eden nesneleri oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="b6bc7-134">Bu nesneleri oluşturduktan sonra, bunları, ihtiyacınız olan her yerde ifade ağacınızdaki bir şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="b6bc7-135">İkinci olarak, bir nesne oluşturmak için yansıma API 'lerinin bir alt kümesini kullanmanız gerekir `MethodInfo` ; böylece bu yönteme erişmek için bir ifade ağacı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="b6bc7-136">Kendinizi .NET Core platformunda bulunan yansıma API 'Lerinin alt kümesiyle sınırlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="b6bc7-137">Bu teknikler yine de diğer ifade ağaçlarına genişletilir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="b6bc7-138">Derinlemesine kod derleme</span><span class="sxs-lookup"><span data-stu-id="b6bc7-138">Building Code In Depth</span></span>

<span data-ttu-id="b6bc7-139">Bu API 'Leri kullanarak neleri oluşturabileceğiniz sınırlı değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="b6bc7-140">Ancak, derlemek istediğiniz daha karmaşık ifade ağacı, kodun yönetilmesi ve okunması daha zordur.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="b6bc7-141">Bu kodun eşdeğeri olan bir ifade ağacı oluşturalım:</span><span class="sxs-lookup"><span data-stu-id="b6bc7-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="b6bc7-142">Yukarıda, ifade ağacını oluşturamadım, ancak yalnızca temsilciyi temsil ediyorum.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="b6bc7-143">Sınıfını kullanarak `Expression` , ifade lambdaları derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="b6bc7-144">Aynı işlevselliği oluşturmak için gereken kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="b6bc7-145">Döngü oluşturmak için bir API olmaması `while` , bunun yerine koşullu bir test içeren bir döngü ve döngünün dışına bölmek için bir etiket hedefi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

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

<span data-ttu-id="b6bc7-146">Çarpınımı işlevi için ifade ağacını oluşturmaya yönelik kod çok daha uzun, daha karmaşıktır ve Etiketler ve break deyimleri ve günlük kodlama görevlerimizde kaçınmak istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="b6bc7-147">Bu bölüm için, ziyaretçi kodunu bu ifade ağacındaki her düğümü ziyaret etmek ve bu örnekte oluşturulan düğümlerle ilgili bilgileri yazmak için güncelleştirdim.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="b6bc7-148">Örnek kodu DotNet/docs GitHub deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) .</span><span class="sxs-lookup"><span data-stu-id="b6bc7-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="b6bc7-149">Örnekleri oluşturup çalıştırarak kendiniz için denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="b6bc7-150">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../samples-and-tutorials/index.md#view-and-download-samples).</span><span class="sxs-lookup"><span data-stu-id="b6bc7-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="b6bc7-151">API 'Leri İnceleme</span><span class="sxs-lookup"><span data-stu-id="b6bc7-151">Examining the APIs</span></span>

<span data-ttu-id="b6bc7-152">İfade ağacı API 'Leri, .NET Core 'ta gezinmek daha zordur, ancak bu kadar iyidir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="b6bc7-153">Amaçları, karmaşık bir yetersiz alma: çalışma zamanında kod üreten kod yazma.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="b6bc7-154">C# dilinde kullanılabilir olan tüm denetim yapılarını destekleme ve API 'lerin yüzey alanını makul şekilde küçük tutmak arasında bir denge sağlamak açısından karmaşık olmaları gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="b6bc7-155">Bu Bakiye, birçok denetim yapısının C# yapıları tarafından değil, ancak derleyicinin bu üst düzey yapıların oluşturduğu temel mantığı temsil eden yapılar tarafından temsil edildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="b6bc7-156">Ayrıca, şu anda doğrudan sınıf yöntemleri kullanılarak derlenemez C# ifadeleri vardır `Expression` .</span><span class="sxs-lookup"><span data-stu-id="b6bc7-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="b6bc7-157">Genellikle, bu, C# 5 ve C# 6 ' da eklenen en yeni işleçler ve ifadeler olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b6bc7-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="b6bc7-158">(Örneğin, `async` ifadeler derlenemez ve yeni `?.` işleç doğrudan oluşturulamaz.)</span><span class="sxs-lookup"><span data-stu-id="b6bc7-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="b6bc7-159">İleri--Ifadeleri çevirme</span><span class="sxs-lookup"><span data-stu-id="b6bc7-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
