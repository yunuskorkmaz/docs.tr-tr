---
title: Destek ifade ağaçları Framework türleri
description: İfade ağaçları destekleme framework türleri ifade ağaçları ve ifade ağacına API'leri ile çalışmak için teknikleri oluşturma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214951"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="682df-103">Destek ifade ağaçları Framework türleri</span><span class="sxs-lookup"><span data-stu-id="682df-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="682df-104">Önceki--Açıklandığı ifade ağaçları</span><span class="sxs-lookup"><span data-stu-id="682df-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="682df-105">İfade ağaçları ile iş sınıfları .NET Core Framework'te büyük listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="682df-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="682df-106">Tam listeye bakın [burada](/dotnet/core/api/System.Linq.Expressions).</span><span class="sxs-lookup"><span data-stu-id="682df-106">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="682df-107">Tam listeyi çalıştırmak yerine nasıl framework sınıfları tasarlanmış anlayalım.</span><span class="sxs-lookup"><span data-stu-id="682df-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="682df-108">Dil tasarımında, bir ifade değerlendirir ve bir değer döndürür kodu gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="682df-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="682df-109">İfadeleri çok basit: sabit ifade `1` sabit 1 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="682df-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="682df-110">Daha karmaşık olabilir: ifade `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` ikinci derece eşitlik (denklemi bir çözüme sahip olduğu durumda) için bir kök döndürür.</span><span class="sxs-lookup"><span data-stu-id="682df-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="682df-111">Tüm System.Linq.Expression ile başlar</span><span class="sxs-lookup"><span data-stu-id="682df-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="682df-112">İfade ağaçları ile çalışmanın karmaşıklıkları birçok farklı türde ifadeler programlar birçok yerde geçerli olduğunu biridir.</span><span class="sxs-lookup"><span data-stu-id="682df-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="682df-113">Bir atama ifadesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="682df-113">Consider an assignment expression.</span></span> <span data-ttu-id="682df-114">Sağ taraftaki atama sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başkalarının olabilir.</span><span class="sxs-lookup"><span data-stu-id="682df-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="682df-115">Bu dil esneklik bir ifade ağacına gezme zaman ağaç düğümleri başka bir yerindeki birçok farklı ifade türleri karşılaşabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="682df-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="682df-116">Temel ifade türü ile çalışabilir, bu nedenle, iş için en basit yolu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="682df-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="682df-117">Ancak, bazen daha fazla bilgi edinmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="682df-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="682df-118">Temel ifade sınıfı içeren bir `NodeType` özelliği bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="682df-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="682df-119">Döndürdüğü bir `ExpressionType` olası ifade türleri numaralandırması olduğu.</span><span class="sxs-lookup"><span data-stu-id="682df-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="682df-120">Düğüm türü öğrendikten sonra onu bu türe ve ifade düğümü türü bilerek belirli eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682df-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="682df-121">Belirli düğüm türleri arayın ve sonra bu tür bir ifade belirli özellikleri ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="682df-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="682df-122">Örneğin, bu kod bir değişken adı bir değişken erişim ifadenin yazdırır.</span><span class="sxs-lookup"><span data-stu-id="682df-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="682df-123">Düğüm türü denetimi sonra bir değişken erişim ifadesi atama ve belirli ifade türünün özelliklerini denetleme uygulama takip:</span><span class="sxs-lookup"><span data-stu-id="682df-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="682df-124">İfade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="682df-124">Creating Expression Trees</span></span>

<span data-ttu-id="682df-125">`System.Linq.Expression` Sınıfı ayrıca ifadeleri oluşturmak için birçok statik yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="682df-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="682df-126">Bu yöntemler, çocuklar için sağlanan bağımsız değişkenler kullanarak bir ifade düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="682df-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="682df-127">Bu şekilde, bir ifade, yaprak düğümü oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="682df-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="682df-128">Örneğin, bu kod bir Ekle ifade oluşturur:</span><span class="sxs-lookup"><span data-stu-id="682df-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="682df-129">Bu basit örneğindeki birçok türleri oluşturma ve ifade ağaçları ile çalışma oynayan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682df-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="682df-130">Bu karmaşıklık C# dili tarafından sağlanan zengin sözlük özellikleri sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="682df-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="682df-131">API'ler gezinme</span><span class="sxs-lookup"><span data-stu-id="682df-131">Navigating the APIs</span></span>
<span data-ttu-id="682df-132">Neredeyse tüm C# dili sözdizimi öğelerinin eşleme ifadesi düğüm türü vardır.</span><span class="sxs-lookup"><span data-stu-id="682df-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="682df-133">Her tür language öğesi türü için belirli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="682df-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="682df-134">Bir kerede başının içinde tutmak için çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="682df-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="682df-135">Her şeyi ezberleme çalıştığınızda yerine ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="682df-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="682df-136">Ara üyelerinden birinde `ExpressionType` incelemekte olası düğümleri enum.</span><span class="sxs-lookup"><span data-stu-id="682df-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="682df-137">Bu gerçekten çapraz geçiş ve bir ifade ağacına anlamak istediğinizde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="682df-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="682df-138">Ara statik üyeleri `Expression` bir ifade oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="682df-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="682df-139">Bu yöntemlerin herhangi bir alt kümesini ifade türünden düğümleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682df-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="682df-140">Bakmak `ExpressionVisitor` değiştirilmiş ifade ağacına oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="682df-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="682df-141">Yazarken daha fazla alanlarının her birinde bu üç Ara bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="682df-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="682df-142">Neredeyse şaşmaz biçimde, bu üç adımı biri ile başlattığınızda gerekenler bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="682df-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="682df-143">Sonraki--İfade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="682df-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
