---
title: İfade Ağaçlarını Destekleyen Çerçeve Türleri
description: İfade ağaçlarını destekleyen, ifade ağaçları oluşturan çerçeve türleri ve ifade ağacı API'leriyle çalışma teknikleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146092"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="571d1-103">İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="571d1-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="571d1-104">Önceki -- İfade Ağaçları Açıklaması</span><span class="sxs-lookup"><span data-stu-id="571d1-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="571d1-105">.NET Core çerçevesinde Expression Trees ile çalışan sınıfların büyük bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="571d1-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="571d1-106">Tam listeyi . <xref:System.Linq.Expressions></span><span class="sxs-lookup"><span data-stu-id="571d1-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="571d1-107">Tam listeyi gözden geçirmek yerine, çerçeve sınıflarının nasıl tasarlandığını anlayalım.</span><span class="sxs-lookup"><span data-stu-id="571d1-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="571d1-108">Dil tasarımında, bir ifade bir değeri değerlendiren ve döndüren bir kod gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="571d1-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="571d1-109">İfadeler çok basit olabilir: `1` sabit ifade 1'in sabit değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="571d1-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="571d1-110">Bunlar daha karmaşık olabilir: `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` İfade, kuadratik bir denklem için bir kök döndürür (denklemin bir çözümü olduğu durumlarda).</span><span class="sxs-lookup"><span data-stu-id="571d1-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="571d1-111">Her şey System.Linq.Expression ile başlar.</span><span class="sxs-lookup"><span data-stu-id="571d1-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="571d1-112">İfade ağaçlarıyla çalışmanın karmaşıklıklarından biri, programların birçok yerinde birçok farklı ifade türün geçerli olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="571d1-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="571d1-113">Atama ifadesini düşünün.</span><span class="sxs-lookup"><span data-stu-id="571d1-113">Consider an assignment expression.</span></span> <span data-ttu-id="571d1-114">Bir atamanın sağ tarafı sabit bir değer, değişken, yöntem arama ifadesi veya başka olabilir.</span><span class="sxs-lookup"><span data-stu-id="571d1-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="571d1-115">Bu dil esnekliği, bir ifade ağacında gezinirken bir ağacın düğümlerinde herhangi bir yerde birçok farklı ifade türüyle karşılaşabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="571d1-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="571d1-116">Bu nedenle, temel ifade türüyle çalışabildiğinizde, bu en basit çalışma şeklidir.</span><span class="sxs-lookup"><span data-stu-id="571d1-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="571d1-117">Ancak, bazen daha fazla bilmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="571d1-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="571d1-118">Taban İfade sınıfı `NodeType` bu amaç için bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="571d1-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="571d1-119">Olası ifade `ExpressionType` türlerinin numaralandırması olan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="571d1-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="571d1-120">Düğümün türünü anladıktan sonra, bu türe atabilir ve ifade düğümünün türünü bilerek belirli eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="571d1-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="571d1-121">Belirli düğüm türlerini arayabilir ve ardından bu tür bir ifadenin belirli özellikleriyle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="571d1-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="571d1-122">Örneğin, bu kod değişken erişim ifadesi için bir değişkenin adını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="571d1-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="571d1-123">Düğüm türünü denetleme, ardından değişken erişim ifadesine döküm ve ardından belirli ifade türünün özelliklerini denetleme alıştırmasını uyguladım:</span><span class="sxs-lookup"><span data-stu-id="571d1-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="571d1-124">İfade Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="571d1-124">Creating Expression Trees</span></span>

<span data-ttu-id="571d1-125">Sınıf, `System.Linq.Expression` ifadeler oluşturmak için birçok statik yöntem de içerir.</span><span class="sxs-lookup"><span data-stu-id="571d1-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="571d1-126">Bu yöntemler, alt ları için sağlanan bağımsız değişkenleri kullanarak bir ifade düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="571d1-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="571d1-127">Bu şekilde, yaprak düğümlerinden bir ifade oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="571d1-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="571d1-128">Örneğin, bu kod bir Ekle ifadesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="571d1-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="571d1-129">Bu basit örnekten, ifade ağaçlarının oluşturulması nda ve bununla çalışmada birçok türde rol aldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="571d1-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="571d1-130">Bu karmaşıklık C# dili tarafından sağlanan zengin kelime yeteneklerini sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="571d1-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="571d1-131">API'ler de gezinme</span><span class="sxs-lookup"><span data-stu-id="571d1-131">Navigating the APIs</span></span>
<span data-ttu-id="571d1-132">C# dilinin hemen hemen tüm sözdizimi öğeleriyle eşleyen İfade düğümü türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="571d1-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="571d1-133">Her türde dil öğesi bu tür için özel yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="571d1-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="571d1-134">Aynı anda kafanda tutmak çok fazla.</span><span class="sxs-lookup"><span data-stu-id="571d1-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="571d1-135">Yerine her şeyi ezberlemek için denemek, burada Ifade ağaçları ile çalışmak için kullandığınız teknikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="571d1-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="571d1-136">İncelemeniz gereken olası `ExpressionType` düğümleri belirlemek için enum üyelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="571d1-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="571d1-137">Bu gerçekten geçiş ve bir ifade ağacı anlamak istediğinizde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="571d1-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="571d1-138">Bir ifade oluşturmak için `Expression` sınıfın statik üyelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="571d1-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="571d1-139">Bu yöntemler, alt düğümleri kümesinden herhangi bir ifade türü oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="571d1-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="571d1-140">Değiştirilmiş bir `ExpressionVisitor` ifade ağacı oluşturmak için sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="571d1-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="571d1-141">Bu üç alanın her birine baktıkça daha fazlasını bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="571d1-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="571d1-142">Her zaman, bu üç adımdan biriyle başladığınızda ihtiyacınız olanı bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="571d1-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="571d1-143">Sonraki -- İfade Ağaçlarını Yürütme</span><span class="sxs-lookup"><span data-stu-id="571d1-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
