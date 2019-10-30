---
title: İfade Ağaçları
description: .NET Core 'daki ifade ağaçları ve kodu, inceleyebileceğiniz, değiştirebileceğiniz ve yürütemeyeceğiniz yapılar olarak göstermek için nasıl kullanacağınızı öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036316"
---
# <a name="expression-trees"></a><span data-ttu-id="e5734-103">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="e5734-103">Expression Trees</span></span>

<span data-ttu-id="e5734-104">LINQ kullandıysanız, `Func` türlerinin API kümesinin bir parçası olduğu zengin bir kitaplık ile karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="e5734-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="e5734-105">(LINQ hakkında bilginiz yoksa, büyük olasılıkla [LINQ öğreticisini](linq/index.md) ve bu uygulamadan önce [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) hakkındaki makaleyi okumak istersiniz.) *Ifade ağaçları* , işlevleri olan bağımsız değişkenlerle daha zengin etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5734-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="e5734-106">LINQ sorguları oluştururken, genellikle lambda Ifadeleri kullanarak işlev bağımsız değişkenleri yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="e5734-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="e5734-107">Tipik bir LINQ sorgusunda, bu işlev bağımsız değişkenleri derleyicinin oluşturduğu bir temsilciye dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e5734-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="e5734-108">Daha zengin bir etkileşim sağlamak istediğinizde, *Ifade ağaçları*kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e5734-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="e5734-109">İfade ağaçları kodu, inceleyebileceğiniz, değiştirebileceğiniz veya yürütebilmeniz için bir yapı olarak temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5734-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="e5734-110">Bu araçlar, çalışma zamanında kodu işleme gücü sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5734-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="e5734-111">Çalışan algoritmaların incelediği veya yeni özellikleri barındıran bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5734-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="e5734-112">Daha Gelişmiş senaryolarda, çalışan algoritmaları değiştirebilir ve hatta farklı bir ortamda yürütmek üzere C# ifadeleri başka bir biçimde çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5734-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="e5734-113">Büyük olasılıkla Ifade ağaçları kullanan kodu zaten yazmış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5734-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="e5734-114">Entity Framework LINQ API 'Leri, LINQ sorgu Ifade deseninin bağımsız değişkenleri olarak Ifade ağaçlarını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e5734-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="e5734-115">Bu, [Entity Framework](/ef/) , yazdığınız sorguyu veritabanı ALTYAPıSıNDA yürütülen SQL C# 'e çevirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5734-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="e5734-116">.NET için popüler bir sahte işlem çerçevesi olan [moq](https://github.com/Moq/moq)başka bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="e5734-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="e5734-117">Bu öğreticinin geri kalan bölümleri, Ifade ağaçlarının ne olduğunu keşfedebilir, ifade ağaçlarını destekleyen çerçeve sınıflarını inceler ve ifade ağaçlarıyla nasıl çalışabileceğinize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e5734-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="e5734-118">İfade ağaçlarını nasıl okuyacağınızı, ifade ağaçları oluşturmayı, değiştirilmiş ifade ağaçları oluşturmayı ve ifade ağaçları tarafından temsil edilen kodun nasıl yürütüleceğini öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e5734-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="e5734-119">Okunduktan sonra, zengin Uyarlamalı algoritmalar oluşturmak için bu yapıları kullanmaya hazırlanın.</span><span class="sxs-lookup"><span data-stu-id="e5734-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="e5734-120">İfade Ağaçları Açıklaması</span><span class="sxs-lookup"><span data-stu-id="e5734-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="e5734-121">*Ifade ağaçları*arkasındaki yapıyı ve kavramları anlayın.</span><span class="sxs-lookup"><span data-stu-id="e5734-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="e5734-122">İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="e5734-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="e5734-123">İfade ağaçlarını tanımlayan ve işleyen yapılar ve sınıflar hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e5734-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="e5734-124">İfade Yürütme</span><span class="sxs-lookup"><span data-stu-id="e5734-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="e5734-125">Lambda Ifadesi olarak temsil edilen bir ifade ağacını temsilciye dönüştürmeyi ve elde edilen temsilciyi yürütmeyi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e5734-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="e5734-126">İfade Yorumlama</span><span class="sxs-lookup"><span data-stu-id="e5734-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="e5734-127">İfade ağacının hangi kodun temsil ettiğini anlamak için, *ifade ağaçlarına* çapraz geçiş yapma ve İnceleme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="e5734-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="e5734-128">İfade Derleme</span><span class="sxs-lookup"><span data-stu-id="e5734-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="e5734-129">Bir ifade ağacı ve derleme ifade ağaçları için düğümleri oluşturmayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e5734-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="e5734-130">İfade Çevirme</span><span class="sxs-lookup"><span data-stu-id="e5734-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="e5734-131">Bir ifade ağacının değiştirilmiş bir kopyasını oluşturmayı veya bir ifade ağacını farklı bir biçime çevireceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e5734-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="e5734-132">Toplam</span><span class="sxs-lookup"><span data-stu-id="e5734-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="e5734-133">İfade ağaçları hakkındaki bilgileri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e5734-133">Review the information on expression trees.</span></span>
