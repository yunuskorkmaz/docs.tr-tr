---
title: İfade Ağaçları
description: İfade ağaçlarında .NET Core ve bunları kodunu incelemek, değiştirmek, çalıştırmak ve yapıları olarak temsil etmek üzere kullanma hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db6e23d1ad0014a7dbb58a0cd473e67d6bd9acc0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096621"
---
# <a name="expression-trees"></a><span data-ttu-id="69cac-103">İfade Ağaçları</span><span class="sxs-lookup"><span data-stu-id="69cac-103">Expression Trees</span></span>

<span data-ttu-id="69cac-104">LINQ kullandıysanız, zengin kitaplığı deneyimi olan burada `Func` türleri API kümesi bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="69cac-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="69cac-105">(LINQ ile ilgili bilgi sahibi değilseniz, büyük olasılıkla okumak istediğiniz [LINQ öğretici](linq/index.md) ve ilgili makaleyi [lambda ifadeleri](./programming-guide/statements-expressions-operators/lambda-expressions.md) bundan önce.) *İfade ağaçları* işlevleri bağımsız değişkenleriyle daha zengin etkileşim sağlar.</span><span class="sxs-lookup"><span data-stu-id="69cac-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="69cac-106">İşlev bağımsız değişkenlerinin, Lambda ifadeleri LINQ sorguları oluşturduğunuzda genellikle kullanarak yazın.</span><span class="sxs-lookup"><span data-stu-id="69cac-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="69cac-107">Bu işlev bağımsız değişkenleri, tipik bir LINQ Sorgu derleyici oluşturur bir temsilciye dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="69cac-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="69cac-108">Daha zengin etkileşim görüntülemek istiyorsanız, kullanmanız gereken *ifade ağaçları*.</span><span class="sxs-lookup"><span data-stu-id="69cac-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="69cac-109">İfade ağaçları kodunu incelemek, değiştirmek, çalıştırmak veya bir yapı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="69cac-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="69cac-110">Bu araçlar çalışma zamanı sırasında kod düzenleme olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="69cac-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="69cac-111">Çalışan algoritmalar inceler ve yeni özellikleri ekler kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69cac-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="69cac-112">Daha gelişmiş senaryolarda algoritmaları çalıştıran değiştirebilir ve hatta çevir C# ifadelere başka bir form için başka bir ortamda yürütme.</span><span class="sxs-lookup"><span data-stu-id="69cac-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="69cac-113">İfade ağaçları kullanan kodu büyük olasılıkla zaten yazdığınız.</span><span class="sxs-lookup"><span data-stu-id="69cac-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="69cac-114">Entity Framework'ün LINQ API'leri ifade ağaçları LINQ Sorgu ifade deseni için bağımsız değişkenler olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="69cac-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="69cac-115">Etkinleştiren [Entity Framework](/ef/) içinde yazdığınız sorgu çevrilecek C# Veritabanı Altyapısı'nda yürütülen SQL içine.</span><span class="sxs-lookup"><span data-stu-id="69cac-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="69cac-116">Başka bir örnek [Moq](https://github.com/Moq/moq), .NET için popüler bir sahte işlem altyapısı olduğu.</span><span class="sxs-lookup"><span data-stu-id="69cac-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="69cac-117">Bu öğreticinin geri kalan bölümlerini ifade ağaçları nelerdir keşfedin, ifade ağaçlarını destekleyen ve ifade ağaçları ile nasıl Göster framework sınıfları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="69cac-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="69cac-118">İfade ağaçları okuma, ifade ağaçları oluşturma, değiştirilen ifade ağaçları oluşturma ve ifade ağaçları tarafından temsil edilen kodunun nasıl çalıştırılacağını öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="69cac-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="69cac-119">Okuma sonra bu yapıları zengin bir Uyarlamalı algoritmalar oluşturmak için kullanılmaya hazır olacaktır.</span><span class="sxs-lookup"><span data-stu-id="69cac-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="69cac-120">İfade ağaçları açıklaması</span><span class="sxs-lookup"><span data-stu-id="69cac-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="69cac-121">Yapı ve kavramları anlama *ifade ağaçları*.</span><span class="sxs-lookup"><span data-stu-id="69cac-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="69cac-122">İfade ağaçlarını destekleyen çerçeve türleri</span><span class="sxs-lookup"><span data-stu-id="69cac-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="69cac-123">Yapılar ve sınıflar tanımlayın ve ifade ağaçları işlemek hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="69cac-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="69cac-124">İfade yürütme</span><span class="sxs-lookup"><span data-stu-id="69cac-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="69cac-125">Bir temsilciye Lambda ifadesiyle temsil edilen bir ifade ağacı dönüştürme hakkında bilgi alın ve sonuç olarak oluşan temsilci yürütün.</span><span class="sxs-lookup"><span data-stu-id="69cac-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="69cac-126">İfade yorumlama</span><span class="sxs-lookup"><span data-stu-id="69cac-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="69cac-127">Geçiş ve incelemek öğrenin *ifade ağaçları* ne ifade ağacı kod anlamak için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="69cac-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="69cac-128">İfade derleme</span><span class="sxs-lookup"><span data-stu-id="69cac-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="69cac-129">İfade ağacı düğümleri oluşturmak ve ifade ağaçları oluşturma hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="69cac-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="69cac-130">İfade çevirme</span><span class="sxs-lookup"><span data-stu-id="69cac-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="69cac-131">İfade ağacı değiştirilmiş bir kopyasını oluşturun veya bir ifade ağacı farklı bir biçime çevir öğrenin.</span><span class="sxs-lookup"><span data-stu-id="69cac-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="69cac-132">Özetle</span><span class="sxs-lookup"><span data-stu-id="69cac-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="69cac-133">İfade ağaçları bilgileri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="69cac-133">Review the information on expression trees.</span></span>
