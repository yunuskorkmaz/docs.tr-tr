---
title: "Destek ifade ağaçları Framework türleri"
description: "İfade ağaçları destekleme framework türleri ifade ağaçları ve ifade ağacına API'leri ile çalışmak için teknikleri oluşturma hakkında bilgi edinin."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: ed89b286eee9b4c2e11bb27d18e50f777f94f33e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="46f7f-104">Destek ifade ağaçları Framework türleri</span><span class="sxs-lookup"><span data-stu-id="46f7f-104">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="46f7f-105">Önceki--Açıklandığı ifade ağaçları</span><span class="sxs-lookup"><span data-stu-id="46f7f-105">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="46f7f-106">İfade ağaçları ile iş sınıfları .NET Core Framework'te büyük listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-106">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="46f7f-107">Tam listeye bakın [burada](/dotnet/core/api/System.Linq.Expressions).</span><span class="sxs-lookup"><span data-stu-id="46f7f-107">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="46f7f-108">Tam listeyi çalıştırmak yerine nasıl framework sınıfları tasarlanmış anlayalım.</span><span class="sxs-lookup"><span data-stu-id="46f7f-108">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="46f7f-109">Dil tasarımında, bir ifade değerlendirir ve bir değer döndürür kodu gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-109">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="46f7f-110">İfadeleri çok basit: sabit ifade `1` sabit 1 değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="46f7f-110">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="46f7f-111">Daha karmaşık olabilir: ifade `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` ikinci derece eşitlik (denklemi bir çözüme sahip olduğu durumda) için bir kök döndürür.</span><span class="sxs-lookup"><span data-stu-id="46f7f-111">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="46f7f-112">Tüm System.Linq.Expression ile başlar</span><span class="sxs-lookup"><span data-stu-id="46f7f-112">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="46f7f-113">İfade ağaçları ile çalışmanın karmaşıklıkları birçok farklı türde ifadeler programlar birçok yerde geçerli olduğunu biridir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-113">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="46f7f-114">Bir atama ifadesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="46f7f-114">Consider an assignment expression.</span></span> <span data-ttu-id="46f7f-115">Sağ taraftaki atama sabit bir değer, bir değişken, bir yöntem çağrısı ifadesi veya başkalarının olabilir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-115">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="46f7f-116">Bu dil esneklik bir ifade ağacına gezme zaman ağaç düğümleri başka bir yerindeki birçok farklı ifade türleri karşılaşabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-116">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="46f7f-117">Temel ifade türü ile çalışabilir, bu nedenle, iş için en basit yolu olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="46f7f-117">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="46f7f-118">Ancak, bazen daha fazla bilgi edinmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-118">However, sometimes you need to know more.</span></span>
<span data-ttu-id="46f7f-119">Temel ifade sınıfı içeren bir `NodeType` özelliği bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="46f7f-119">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="46f7f-120">Döndürdüğü bir `ExpressionType` olası ifade türleri numaralandırması olduğu.</span><span class="sxs-lookup"><span data-stu-id="46f7f-120">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="46f7f-121">Düğüm türü öğrendikten sonra onu bu türe ve ifade düğümü türü bilerek belirli eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46f7f-121">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="46f7f-122">Belirli düğüm türleri arayın ve sonra bu tür bir ifade belirli özellikleri ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="46f7f-122">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="46f7f-123">Örneğin, bu kod bir değişken adı bir değişken erişim ifadenin yazdırır.</span><span class="sxs-lookup"><span data-stu-id="46f7f-123">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="46f7f-124">Düğüm türü denetimi sonra bir değişken erişim ifadesi atama ve belirli ifade türünün özelliklerini denetleme uygulama takip:</span><span class="sxs-lookup"><span data-stu-id="46f7f-124">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="46f7f-125">İfade ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="46f7f-125">Creating Expression Trees</span></span>

<span data-ttu-id="46f7f-126">`System.Linq.Expression` Sınıfı ayrıca ifadeleri oluşturmak için birçok statik yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-126">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="46f7f-127">Bu yöntemler, çocuklar için sağlanan bağımsız değişkenler kullanarak bir ifade düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46f7f-127">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="46f7f-128">Bu şekilde, bir ifade, yaprak düğümü oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="46f7f-128">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="46f7f-129">Örneğin, bu kod bir Ekle ifade oluşturur:</span><span class="sxs-lookup"><span data-stu-id="46f7f-129">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="46f7f-130">Bu basit örneğindeki birçok türleri oluşturma ve ifade ağaçları ile çalışma oynayan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46f7f-130">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="46f7f-131">Bu karmaşıklık C# dili tarafından sağlanan zengin sözlük özellikleri sağlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="46f7f-131">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="46f7f-132">API'ler gezinme</span><span class="sxs-lookup"><span data-stu-id="46f7f-132">Navigating the APIs</span></span>
<span data-ttu-id="46f7f-133">Neredeyse tüm C# dili sözdizimi öğelerinin eşleme ifadesi düğüm türü vardır.</span><span class="sxs-lookup"><span data-stu-id="46f7f-133">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="46f7f-134">Her tür language öğesi türü için belirli yöntemler vardır.</span><span class="sxs-lookup"><span data-stu-id="46f7f-134">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="46f7f-135">Bir kerede başının içinde tutmak için çok karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="46f7f-135">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="46f7f-136">Her şeyi ezberleme çalıştığınızda yerine ifade ağaçları ile çalışmak için kullandığım teknikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46f7f-136">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="46f7f-137">Ara üyelerinden birinde `ExpressionType` incelemekte olası düğümleri enum.</span><span class="sxs-lookup"><span data-stu-id="46f7f-137">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="46f7f-138">Bu gerçekten çapraz geçiş ve bir ifade ağacına anlamak istediğinizde yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="46f7f-138">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="46f7f-139">Ara statik üyeleri `Expression` bir ifade oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46f7f-139">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="46f7f-140">Bu yöntemlerin herhangi bir alt kümesini ifade türünden düğümleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46f7f-140">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="46f7f-141">Bakmak `ExpressionVisitor` değiştirilmiş ifade ağacına oluşturmak için sınıfı.</span><span class="sxs-lookup"><span data-stu-id="46f7f-141">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="46f7f-142">Yazarken daha fazla alanlarının her birinde bu üç Ara bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46f7f-142">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="46f7f-143">Neredeyse şaşmaz biçimde, bu üç adımı biri ile başlattığınızda gerekenler bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="46f7f-143">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="46f7f-144">Sonraki--İfade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="46f7f-144">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
