---
title: "İfade ağaçları özeti"
description: "Kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz özetleri."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a><span data-ttu-id="a82ed-104">İfade ağaçları özeti</span><span class="sxs-lookup"><span data-stu-id="a82ed-104">Expression Trees Summary</span></span>

[<span data-ttu-id="a82ed-105">Önceki--İfadeleri çevirme</span><span class="sxs-lookup"><span data-stu-id="a82ed-105">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="a82ed-106">Bu dizide nasıl kullanacağınızı gördünüz *ifade ağaçları* kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a82ed-106">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="a82ed-107">Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a82ed-107">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="a82ed-108">Yalnızca bu kodu inceleyebilirsiniz değil.</span><span class="sxs-lookup"><span data-stu-id="a82ed-108">You can not only examine that code.</span></span> <span data-ttu-id="a82ed-109">Özgün kod değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a82ed-109">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="a82ed-110">Bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil veya ortamla bu algoritmayı çevir.</span><span class="sxs-lookup"><span data-stu-id="a82ed-110">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="a82ed-111">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="a82ed-111">Limitations</span></span>

<span data-ttu-id="a82ed-112">İyi ifade ağaçlara Çevir olmayan bazı yeni C# dil öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a82ed-112">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="a82ed-113">İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="a82ed-113">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="a82ed-114">C# 6 sürümde eklenen özelliklerin tam olarak ifade ağaçlarında yazılmış gibi görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="a82ed-114">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="a82ed-115">Bunun yerine, ifade ağaçları eşdeğer, önceki sözdiziminde daha yeni özellikleri sunulur.</span><span class="sxs-lookup"><span data-stu-id="a82ed-115">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="a82ed-116">Bu düşündüğünüzden gibi sınırlandırılmasıdır kadar olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="a82ed-116">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="a82ed-117">Aslında, bu yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu hala olasılıkla aynı çalışacağını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a82ed-117">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="a82ed-118">Bu kısıtlamalarla bile ifade ağaçları yorumlama ve veri yapısı olarak temsil edilir kodu değiştirme dayanan dinamik algoritmaları oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a82ed-118">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="a82ed-119">Güçlü bir araçtır ve ne yaptıklarını gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosistemi özelliklerini biridir.</span><span class="sxs-lookup"><span data-stu-id="a82ed-119">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

