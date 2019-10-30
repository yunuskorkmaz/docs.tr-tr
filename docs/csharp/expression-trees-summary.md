---
title: İfade ağaçları Özeti
description: Kodu veri olarak yorumlayan ve bu koda göre yeni işlevsellik oluşturan dinamik programlar oluşturmak için, ifade ağaçlarını nasıl kullanabileceğinizi öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036751"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="4c864-103">İfade ağaçları Özeti</span><span class="sxs-lookup"><span data-stu-id="4c864-103">Expression Trees Summary</span></span>

[<span data-ttu-id="4c864-104">Önceki--Ifadeleri çevirme</span><span class="sxs-lookup"><span data-stu-id="4c864-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="4c864-105">Bu seride, kod verileri olarak yorumlayan ve bu koda göre yeni işlevsellik oluşturan dinamik programlar oluşturmak için *ifade ağaçlarını* nasıl kullanabileceğinizi gördünüz.</span><span class="sxs-lookup"><span data-stu-id="4c864-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="4c864-106">Bir algoritmanın amacını anlamak için ifade ağaçlarını inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c864-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="4c864-107">Bu kodu yalnızca inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c864-107">You can not only examine that code.</span></span> <span data-ttu-id="4c864-108">Özgün kodun değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c864-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="4c864-109">Ayrıca, bir algoritmaya bakmak ve bu algoritmayı başka bir dile veya ortama çevirmek için ifade ağaçlarını de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c864-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="4c864-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="4c864-110">Limitations</span></span>

<span data-ttu-id="4c864-111">İfade ağaçlarına düzgün C# çevriolmayan bazı yeni dil öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="4c864-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="4c864-112">İfade ağaçları `await` ifade veya `async` lambda ifadesi içeremez.</span><span class="sxs-lookup"><span data-stu-id="4c864-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="4c864-113">C# 6 sürümüne eklenen özelliklerin birçoğu tam olarak ifade ağaçlarında yazılmış şekilde görünmez.</span><span class="sxs-lookup"><span data-stu-id="4c864-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="4c864-114">Bunun yerine, eşdeğer, Önceki sözdiziminde ifade ağaçlarında daha yeni özellikler kullanıma sunulacaktır.</span><span class="sxs-lookup"><span data-stu-id="4c864-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="4c864-115">Bu işlem, düşündüğünüzden bir sınırlamanın büyük bir bölümü olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4c864-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="4c864-116">Aslında, ifade ağaçlarını yorumlayan kodunuzun, yeni dil özellikleri tanıtıldığında muhtemelen aynı zamanda çalışmaya devam ettiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4c864-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="4c864-117">Bu sınırlamalar da dahil olmak üzere, ifade ağaçları, veri yapısı olarak temsil edilen kodu yorumlama ve değiştirme konusunda temel alan dinamik algoritmalar oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c864-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="4c864-118">Bu güçlü bir araçtır ve .NET ekosisteminin, Entity Framework gibi zengin kitaplıkları sağlayan özelliklerden biridir.</span><span class="sxs-lookup"><span data-stu-id="4c864-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
