---
title: İfade Ağaçları Özeti
description: Kodu veri olarak yorumlayan ve bu koda dayalı yeni işlevler oluşturan dinamik programlar oluşturmak için ifade ağaçlarını nasıl kullanabileceğinizi özetler.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145897"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="94d40-103">İfade Ağaçları Özeti</span><span class="sxs-lookup"><span data-stu-id="94d40-103">Expression Trees Summary</span></span>

[<span data-ttu-id="94d40-104">Önceki -- İfadeleri Çevirme</span><span class="sxs-lookup"><span data-stu-id="94d40-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="94d40-105">Bu seride, kodu veri olarak yorumlayan ve bu koda dayalı yeni işlevler oluşturan dinamik programlar oluşturmak için *ifade ağaçlarını* nasıl kullanabileceğinizi gördünüz.</span><span class="sxs-lookup"><span data-stu-id="94d40-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="94d40-106">Bir algoritmanın amacını anlamak için ifade ağaçlarını inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d40-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="94d40-107">Sadece bu kodu inceleyebilir.</span><span class="sxs-lookup"><span data-stu-id="94d40-107">You can not only examine that code.</span></span> <span data-ttu-id="94d40-108">Özgün kodun değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d40-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="94d40-109">Bir algoritmaya bakmak ve bu algoritmayı başka bir dile veya ortama çevirmek için ifade ağaçlarını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94d40-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span>

## <a name="limitations"></a><span data-ttu-id="94d40-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="94d40-110">Limitations</span></span>

<span data-ttu-id="94d40-111">İfade ağaçlarına iyi çevrilen bazı yeni C# dil öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="94d40-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="94d40-112">İfade ağaçları `await` ifadeler veya `async` lambda ifadeleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="94d40-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="94d40-113">C# 6 sürümünde eklenen özelliklerin çoğu ifade ağaçlarında yazıldığı gibi görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="94d40-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="94d40-114">Bunun yerine, daha yeni özellikler eşdeğer, önceki sözdizimi ifadeler ağaçlar maruz kalır.</span><span class="sxs-lookup"><span data-stu-id="94d40-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="94d40-115">Bu düşündüğünüz kadar bir sınırlama olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="94d40-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="94d40-116">Aslında, ifade ağaçlarını yorumlayan kodunuzu yeni dil özellikleri tanıtıldığında büyük olasılıkla yine de aynı şekilde çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="94d40-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="94d40-117">Bu sınırlamalara rağmen, ifade ağaçları, veri yapısı olarak temsil edilen kodu yorumlamaya ve değiştirmeye dayanan dinamik algoritmalar oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="94d40-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="94d40-118">Bu güçlü bir araçtır ve .NET ekosisteminin entity framework gibi zengin kitaplıkların yaptıklarını gerçekleştirmesini sağlayan özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="94d40-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
