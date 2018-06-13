---
title: İfade Ağaçları
description: İfade ağaçları .NET Core ve bunları inceleyin, değiştirme, yürütme ve yapıları olarak kodunu temsil etmek için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214919"
---
# <a name="expression-trees"></a><span data-ttu-id="8684e-103">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="8684e-103">Expression Trees</span></span>

<span data-ttu-id="8684e-104">LINQ kullandıysanız, zengin kitaplığıyla deneyim sahibi olduğu `Func` türleri API kümesi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8684e-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="8684e-105">(LINQ ile bilmiyorsanız, büyük olasılıkla okumak istediğiniz [LINQ öğretici](linq/index.md) ve öğretici [lambda ifadeleri](lambda-expressions.md) bundan önce.) *İfade ağaçları* işlevleri olan bağımsız değişkenler daha zengin etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="8684e-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="8684e-106">LINQ sorgularını oluşturduğunuzda, genellikle Lambda ifadeleri kullanma işlev bağımsız değişkenleri, yazma.</span><span class="sxs-lookup"><span data-stu-id="8684e-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="8684e-107">Tipik bir LINQ Sorgu bu işlev bağımsız değişkenleri derleyici oluşturur temsilci dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="8684e-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="8684e-108">Daha zengin etkileşim olmasını istediğinizde, kullanmanıza gerek *ifade ağaçları*.</span><span class="sxs-lookup"><span data-stu-id="8684e-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="8684e-109">İfade ağaçları kodu inceleyin, değiştirme, execute veya bir yapı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8684e-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="8684e-110">Bu araçları çalışma zamanı sırasında kodu işlemek için güç sağlar.</span><span class="sxs-lookup"><span data-stu-id="8684e-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="8684e-111">Çalışan algoritmaları inceler ya da yeni özellikler yerleştirir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8684e-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="8684e-112">Daha gelişmiş senaryolarda algoritmaları çalıştıran değiştirmek ve hatta C# başka bir form için başka bir ortamda yürütme ifadelere çevirir.</span><span class="sxs-lookup"><span data-stu-id="8684e-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="8684e-113">İfade ağaçları kullanan kodu büyük olasılıkla zaten yazdıktan.</span><span class="sxs-lookup"><span data-stu-id="8684e-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="8684e-114">Entity Framework'ün LINQ API'ları ifade ağaçları LINQ Sorgu ifade deseni bağımsız değişkenleri olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8684e-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="8684e-115">Sağlayan [Entity Framework](http://docs.efproject.net/en/latest/) yazdığınız C# veritabanı altyapısı'nda yürüten SQL içine sorgu çevrilemedi.</span><span class="sxs-lookup"><span data-stu-id="8684e-115">That enables [Entity Framework](http://docs.efproject.net/en/latest/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="8684e-116">Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir mocking framework olduğu.</span><span class="sxs-lookup"><span data-stu-id="8684e-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="8684e-117">Bu öğreticinin kalan bölümleri ifade ağaçları nelerdir keşfetmek, ifade ağaçları destekleyen ve ifade ağaçları ile nasıl çalışacağınızı framework sınıfları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="8684e-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="8684e-118">İfade ağaçları okumak nasıl, ifade ağaçları oluşturma, değiştirilmiş ifade ağaçları oluşturma ve ifade ağaçları tarafından temsil edilen kodu çalıştırma hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8684e-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="8684e-119">Okuma sonra zengin Uyarlamalı algoritmaları oluşturmak için bu yapıları kullanıma hazır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8684e-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="8684e-120">İfade Ağaçları Açıklaması</span><span class="sxs-lookup"><span data-stu-id="8684e-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="8684e-121">Yapı ve kavramları anlamanız *ifade ağaçları*.</span><span class="sxs-lookup"><span data-stu-id="8684e-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="8684e-122">İfade Ağaçlarını Destekleyen Çerçeve Türleri</span><span class="sxs-lookup"><span data-stu-id="8684e-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="8684e-123">Tanımlayan ve ifade ağaçları işlemek sınıfları ve yapıları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="8684e-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="8684e-124">İfade Yürütme</span><span class="sxs-lookup"><span data-stu-id="8684e-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="8684e-125">Lambda ifadesi bir temsilci temsil bir ifade ağacına dönüştürülemiyor öğrenin ve sonuçta elde edilen temsilci yürütün.</span><span class="sxs-lookup"><span data-stu-id="8684e-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="8684e-126">İfade Yorumlama</span><span class="sxs-lookup"><span data-stu-id="8684e-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="8684e-127">Çapraz geçiş ve incelemek öğrenin *ifade ağaçları* ne ifade ağacına kod anlamak için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8684e-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="8684e-128">İfade Derleme</span><span class="sxs-lookup"><span data-stu-id="8684e-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="8684e-129">Bir ifade ağacına düğümleri oluşturmak ve ifade ağaçları oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="8684e-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="8684e-130">İfade Çevirme</span><span class="sxs-lookup"><span data-stu-id="8684e-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="8684e-131">Bir ifade ağacına değiştirilmiş bir kopyasını oluşturmak ya da farklı bir biçime bir ifade ağacına çevrilemedi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="8684e-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="8684e-132">Özetle</span><span class="sxs-lookup"><span data-stu-id="8684e-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="8684e-133">İfade ağaçları bilgileri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="8684e-133">Review the information on expression trees.</span></span>
    
