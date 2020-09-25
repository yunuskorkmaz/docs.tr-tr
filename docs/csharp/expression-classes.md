---
title: İfade Ağaçlarını Destekleyen Çerçeve Türleri
description: İfade ağaçlarını destekleyen çerçeve türleri, ifade ağaçları oluşturma ve ifade ağacı API 'Leri ile çalışmaya yönelik teknikler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 548f5ba6a2de00d9556621791515555b6f6a325c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180445"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="2f111-103">İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="2f111-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="2f111-104">Önceki--Ifade ağaçları açıklanıyor</span><span class="sxs-lookup"><span data-stu-id="2f111-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="2f111-105">.NET Core Framework 'te Ifade ağaçları ile çalışan sınıfların büyük bir listesi vardır.</span><span class="sxs-lookup"><span data-stu-id="2f111-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="2f111-106">Listenin tam listesini görebilirsiniz <xref:System.Linq.Expressions> .</span><span class="sxs-lookup"><span data-stu-id="2f111-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="2f111-107">Tam liste üzerinden çalıştırmak yerine, Framework sınıflarının nasıl tasarlandığını anlayalim.</span><span class="sxs-lookup"><span data-stu-id="2f111-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="2f111-108">Dil tasarımında, bir ifade bir değeri değerlendiren ve döndüren bir kod gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="2f111-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="2f111-109">İfadeler çok basit olabilir: sabit ifade, `1` 1 sabit değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f111-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="2f111-110">Daha karmaşık olabilir: ifade, `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` ikinci dereceden bir Denklem için bir kök döndürür (denklemin bir çözüme sahip olduğu durumda).</span><span class="sxs-lookup"><span data-stu-id="2f111-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="2f111-111">Hepsi System. LINQ. Expression ile başlar</span><span class="sxs-lookup"><span data-stu-id="2f111-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="2f111-112">İfade ağaçları ile çalışmanın karmaşıklıklarından biri, programlarda birçok yerde birçok farklı türde ifade geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="2f111-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="2f111-113">Atama ifadesi düşünün.</span><span class="sxs-lookup"><span data-stu-id="2f111-113">Consider an assignment expression.</span></span> <span data-ttu-id="2f111-114">Atamanın sağ tarafı sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başka bir değer olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f111-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="2f111-115">Bu dil esnekliği, bir ifade ağacında çapraz geçiş yaparken bir ağacın düğümleri içinde herhangi bir yerde birçok farklı ifade türüyle karşılaşacağınız anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2f111-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="2f111-116">Bu nedenle, temel ifade türüyle çalışabilmeniz için en kolay yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="2f111-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="2f111-117">Ancak bazen daha fazla bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2f111-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="2f111-118">Taban Ifade sınıfı `NodeType` Bu amaç için bir özellik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2f111-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="2f111-119">`ExpressionType`Olası ifade türlerinin bir numaralandırması olan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="2f111-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="2f111-120">Düğümün türünü öğrendikten sonra, bu türe çevirebilirsiniz ve ifade düğümünün türünü bilmenin belirli eylemlerini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f111-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="2f111-121">Belirli düğüm türlerini arayabilir ve ardından bu tür bir ifadenin belirli özellikleriyle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f111-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="2f111-122">Örneğin, bu kod bir değişken erişim ifadesi için bir değişkenin adını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2f111-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="2f111-123">Düğüm türünü denetleme, sonra bir değişken erişim ifadesine atama ve ardından belirli bir ifade türünün özelliklerini denetleme alıştırması yaşıyorum:</span><span class="sxs-lookup"><span data-stu-id="2f111-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="2f111-124">Ifade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f111-124">Creating Expression Trees</span></span>

<span data-ttu-id="2f111-125">`System.Linq.Expression`Sınıfı ayrıca ifadeler oluşturmak için birçok statik yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="2f111-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="2f111-126">Bu yöntemler, alt öğeleri için sağlanan bağımsız değişkenleri kullanarak bir ifade düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f111-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="2f111-127">Bu şekilde, yaprak düğümlerinden bir ifade oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="2f111-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="2f111-128">Örneğin, bu kod bir ekleme ifadesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2f111-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="2f111-129">Bu basit örnekte, ifade ağaçları oluşturmak ve bunlarla çalışmak için birçok tür bulunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f111-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="2f111-130">Bu karmaşıklık, C# dili tarafından sunulan zengin sözlük yeteneklerini sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2f111-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="2f111-131">API 'Lerde gezinme</span><span class="sxs-lookup"><span data-stu-id="2f111-131">Navigating the APIs</span></span>

<span data-ttu-id="2f111-132">C# dilinin sözdizimi öğelerinin neredeyse tamamına eşlenen Ifade düğüm türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2f111-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="2f111-133">Her türün bu tür dil öğesi için özel yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2f111-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="2f111-134">Tek seferde baş bir süre içinde tutulması çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2f111-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="2f111-135">Her şeyi yeniden denemeye çalışmak yerine, Ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2f111-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="2f111-136">Gözden geçirmeniz `ExpressionType` gereken olası düğümleri öğrenmek için numaralandırmanın üyelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2f111-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="2f111-137">Bu aslında bir ifade ağacını geçmek ve anlamak istediğinizde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2f111-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="2f111-138">`Expression`Bir ifade oluşturmak için sınıfın statik üyelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="2f111-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="2f111-139">Bu yöntemler bir alt düğümleri kümesinden herhangi bir ifade türü oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="2f111-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="2f111-140">`ExpressionVisitor`Değiştirilen bir ifade ağacı oluşturmak için sınıfına bakın.</span><span class="sxs-lookup"><span data-stu-id="2f111-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="2f111-141">Bu üç alanın her birine baktığımızda daha fazla bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f111-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="2f111-142">Bağımsız olarak, bu üç adımdan biriyle başladığınızda ne yapmanız gerektiğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2f111-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="2f111-143">Sonraki--Ifade ağaçları yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="2f111-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
