---
title: İfade Ağaçları
description: .NET Core'daki ifade ağaçları ve kodu inceleyebilir, değiştirebileceğiniz ve yürütebileceğiniz yapılar olarak ifade etmek için bunları nasıl kullanacağınız hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145845"
---
# <a name="expression-trees"></a><span data-ttu-id="5e71d-103">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="5e71d-103">Expression Trees</span></span>

<span data-ttu-id="5e71d-104">LINQ kullandıysanız, türlerin API kümesinin `Func` bir parçası olduğu zengin bir kitaplık la deneyiminiz vardır.</span><span class="sxs-lookup"><span data-stu-id="5e71d-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="5e71d-105">(EĞER LINQ aşina değilseniz, muhtemelen bundan önce [LINQ öğretici](linq/index.md) ve [lambda ifadeler](./programming-guide/statements-expressions-operators/lambda-expressions.md) hakkında makale okumak istiyorum.) *İfade Ağaçlar* işlevleri olan bağımsız değişkenler ile daha zengin etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e71d-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="5e71d-106">LINQ sorguları oluştururken genellikle Lambda İfadeleri'ni kullanarak işlev bağımsız değişkenleri yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="5e71d-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="5e71d-107">Tipik bir LINQ sorgusunda, bu işlev bağımsız değişkenleri derleyicinin oluşturduğu bir temsilciye dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5e71d-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span>

<span data-ttu-id="5e71d-108">Daha zengin bir etkileşim esahip olmak istediğinizde, *İfade Ağaçları*kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e71d-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="5e71d-109">İfade Ağaçları kodu inceleyebilir, değiştirebileceğiniz veya yürütebileceğiniz bir yapı olarak temsil ederler.</span><span class="sxs-lookup"><span data-stu-id="5e71d-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="5e71d-110">Bu araçlar, çalışma süresi boyunca kodu işleme gücü verir.</span><span class="sxs-lookup"><span data-stu-id="5e71d-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="5e71d-111">Çalışan algoritmaları inceleyen veya yeni özellikler enjekte eden kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e71d-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="5e71d-112">Daha gelişmiş senaryolarda, çalışan algoritmaları değiştirebilir ve hatta C# ifadelerini başka bir ortamda yürütme için başka bir forma çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e71d-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="5e71d-113">Büyük olasılıkla İfade Ağaçları kullanan kod yazdınız.</span><span class="sxs-lookup"><span data-stu-id="5e71d-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="5e71d-114">Entity Framework'ün LINQ API'leri, Linq Sorgu İfade Deseni'nin bağımsız değişkenleri olarak İfade Ağaçları'nı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="5e71d-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="5e71d-115">Bu, [Entity Framework'ün](/ef/) C#'da yazdığınız sorguyu veritabanı altyapısında yürüten SQL'e çevirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e71d-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="5e71d-116">Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir alay çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="5e71d-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="5e71d-117">Bu öğreticinin kalan bölümleri, İfade Ağaçlarının ne olduğunu inceleyecek, ifade ağaçlarını destekleyen çerçeve sınıflarını inceleyecek ve ifade ağaçlarıyla nasıl çalışacağınızı gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="5e71d-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="5e71d-118">İfade ağaçlarını okumayı, ifade ağaçlarının nasıl oluşturulacağını, değiştirilmiş ifade ağaçlarının nasıl oluşturulacağını ve ifade ağaçlarıyla temsil edilen kodun nasıl yürütüleceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5e71d-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="5e71d-119">Okuduktan sonra, zengin uyarlanabilir algoritmalar oluşturmak için bu yapıları kullanmaya hazır olacak.</span><span class="sxs-lookup"><span data-stu-id="5e71d-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="5e71d-120">İfade Ağaçları Açıklaması</span><span class="sxs-lookup"><span data-stu-id="5e71d-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="5e71d-121">*İfade Ağaçlarının*arkasındaki yapı ve kavramları anlayın.</span><span class="sxs-lookup"><span data-stu-id="5e71d-121">Understand the structure and concepts behind *Expression Trees*.</span></span>

2. [<span data-ttu-id="5e71d-122">İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="5e71d-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

    <span data-ttu-id="5e71d-123">İfade ağaçlarını tanımlayan ve manipüle eden yapılar ve sınıflar hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>

3. [<span data-ttu-id="5e71d-124">İfade Yürütme</span><span class="sxs-lookup"><span data-stu-id="5e71d-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="5e71d-125">Lambda İfadesi olarak temsil edilen bir ifade ağacını temsilciye nasıl dönüştüreceklerini ve elde edilen temsilciyi nasıl yürütüldüğünü öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="5e71d-126">İfade Yorumlama</span><span class="sxs-lookup"><span data-stu-id="5e71d-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="5e71d-127">İfade ağacının hangi kodu temsil etmesini anlamak için *ifade ağaçlarını* nasıl inceleyeceğinizi ve inceleyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="5e71d-128">İfade Derleme</span><span class="sxs-lookup"><span data-stu-id="5e71d-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="5e71d-129">İfade ağacı için düğümleri nasıl oluşturup ifade ağaçları inşa etmeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="5e71d-130">İfade Çevirme</span><span class="sxs-lookup"><span data-stu-id="5e71d-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="5e71d-131">İfade ağacının değiştirilmiş bir kopyasını nasıl oluşturarak nasıl çevireceklerini veya bir ifade ağacını farklı bir biçime nasıl çevireceklerini öğrenin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="5e71d-132">Özetleme</span><span class="sxs-lookup"><span data-stu-id="5e71d-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="5e71d-133">İfade ağaçlarıyla ilgili bilgileri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="5e71d-133">Review the information on expression trees.</span></span>
