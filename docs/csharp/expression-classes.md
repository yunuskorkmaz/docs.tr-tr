---
title: İfade ağaçlarını destekleyen çerçeve türleri
description: İfade ağaçlarını destekleyen çerçeve türleri ifade ağaçları ve ifade ağacı API'leri ile çalışmaya yönelik teknikleri oluşturma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: c18bbfb1273156a4b070d1f195d9e823256fde9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646585"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="e1dba-103">İfade ağaçlarını destekleyen çerçeve türleri</span><span class="sxs-lookup"><span data-stu-id="e1dba-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="e1dba-104">Önceki--İfade ağaçları açıklaması</span><span class="sxs-lookup"><span data-stu-id="e1dba-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="e1dba-105">İfade ağaçları ile çalışan .NET Core framework sınıfları büyük bir listesi bulunur.</span><span class="sxs-lookup"><span data-stu-id="e1dba-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="e1dba-106">Tam listesini görebilirsiniz <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="e1dba-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="e1dba-107">Tam bir listesi çalıştırmak yerine framework sınıfları nasıl tasarladık bakalım.</span><span class="sxs-lookup"><span data-stu-id="e1dba-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="e1dba-108">Dil tasarımında, bir ifade değerlendirir ve bir değer döndüren kod gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="e1dba-109">İfadeleri çok basit: sabit ifade `1` sabit 1 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1dba-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="e1dba-110">Bunlar, daha karmaşık olabilir: İfade `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` bir dereceden eşitlik (Denklemin bir çözümü sahip olduğu durumda) için bir kök dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1dba-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="e1dba-111">Tüm System.Linq.Expression ile başlar</span><span class="sxs-lookup"><span data-stu-id="e1dba-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="e1dba-112">İfade ağaçları ile çalışmanın karmaşıklıkları birçok farklı türde ifadeler programlar pek çok yerde geçerli olduğunu biridir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="e1dba-113">Atama ifadesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e1dba-113">Consider an assignment expression.</span></span> <span data-ttu-id="e1dba-114">Sağ taraftaki atama, sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başkalarının olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="e1dba-115">Bu dil esneklik, bir ifade ağacı gezme olduğunda, bir ağaç düğümleri herhangi bir yerindeki birçok farklı ifade türü karşılaşabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="e1dba-116">Temel ifade türü ile çalışabilir, bu nedenle, iş yapmanın en kolay yolu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e1dba-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="e1dba-117">Ancak, bazen daha fazla bilgi edinmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="e1dba-118">Temel ifade sınıfı içeren bir `NodeType` bu amaç için özellik.</span><span class="sxs-lookup"><span data-stu-id="e1dba-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="e1dba-119">Döndürür bir `ExpressionType` olası ifade türleri numaralandırması olduğu.</span><span class="sxs-lookup"><span data-stu-id="e1dba-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="e1dba-120">Düğüm türü öğrendikten sonra bu türe dönüştürme ve ifadesi düğüm türü bilerek belirli eylemleri gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="e1dba-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="e1dba-121">Belirli düğüm türleri arayın ve ardından, bu tür bir ifade belirli özelliklerle çalışma.</span><span class="sxs-lookup"><span data-stu-id="e1dba-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="e1dba-122">Örneğin, bu kod, bir değişken erişim ifadesi için bir değişken adı yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e1dba-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="e1dba-123">Düğüm türü denetimi sonra bir değişken erişim ifadesi atama ve ardından belirli ifade türünün özelliklerini denetleme uygulaması ve ardından:</span><span class="sxs-lookup"><span data-stu-id="e1dba-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="e1dba-124">İfade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e1dba-124">Creating Expression Trees</span></span>

<span data-ttu-id="e1dba-125">`System.Linq.Expression` Sınıfı da ifadeleri oluşturmak için çok sayıda statik yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="e1dba-126">Bu yöntemleri kullanarak alt öğeleri için sağlanan bağımsız değişkenler bir ifade düğüm oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1dba-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="e1dba-127">Bu şekilde, bir ifade yaprak düğümlerini oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="e1dba-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="e1dba-128">Örneğin, bu kod bir Ekle ifade oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e1dba-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="e1dba-129">Bu basit örnekte oluşturmak ve ifade ağaçları ile çalışan birçok türü katılan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dba-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="e1dba-130">Bu karmaşıklığı, C# dil tarafından sağlanan zengin sözlük yeteneklerini sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="e1dba-131">API'leri gezinme</span><span class="sxs-lookup"><span data-stu-id="e1dba-131">Navigating the APIs</span></span>
<span data-ttu-id="e1dba-132">Neredeyse tüm C# dilinin söz dizimi öğeleri için eşleme ifadesi düğüm türü vardır.</span><span class="sxs-lookup"><span data-stu-id="e1dba-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="e1dba-133">Her tür dil öğesi türü için belirli yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e1dba-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="e1dba-134">Bu, tek seferde birikimine tutmak için çok fazla olur.</span><span class="sxs-lookup"><span data-stu-id="e1dba-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="e1dba-135">Her şeyi ezberlemeniz deneyin yerine ifade ağaçları ile çalışmak için istediğim teknikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e1dba-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="e1dba-136">Konum üyelerinin `ExpressionType` incelemekte olası düğümleri sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e1dba-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="e1dba-137">Bu gerçekten geçiş yapmak ve bir ifade ağacı anlamak istediğinizde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e1dba-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="e1dba-138">Konum statik üyeleri `Expression` bir ifade oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e1dba-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="e1dba-139">Bu yöntemlerin herhangi bir ifade türü bir dizi alt düğümleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dba-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="e1dba-140">Bakmak `ExpressionVisitor` değiştirilmiş ifade ağacı oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e1dba-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="e1dba-141">Üç bu alanların her şekilde daha fazla ara bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dba-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="e1dba-142">Neredeyse şaşmaz biçimde, bu üç adımı biriyle başlattığınızda gerekenler bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1dba-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="e1dba-143">Sonraki--İfade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="e1dba-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
