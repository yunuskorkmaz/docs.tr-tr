---
title: İfade ağaçları özeti
description: Kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz özetleri.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: e0d46aa67b61fd4e1d2bcc20b4a567524bb00301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33213516"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="e3739-103">İfade ağaçları özeti</span><span class="sxs-lookup"><span data-stu-id="e3739-103">Expression Trees Summary</span></span>

[<span data-ttu-id="e3739-104">Önceki--İfadeleri çevirme</span><span class="sxs-lookup"><span data-stu-id="e3739-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="e3739-105">Bu dizide nasıl kullanacağınızı gördünüz *ifade ağaçları* kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e3739-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="e3739-106">Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3739-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="e3739-107">Yalnızca bu kodu inceleyebilirsiniz değil.</span><span class="sxs-lookup"><span data-stu-id="e3739-107">You can not only examine that code.</span></span> <span data-ttu-id="e3739-108">Özgün kod değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3739-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="e3739-109">Bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil veya ortamla bu algoritmayı çevir.</span><span class="sxs-lookup"><span data-stu-id="e3739-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="e3739-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="e3739-110">Limitations</span></span>

<span data-ttu-id="e3739-111">İyi ifade ağaçlara Çevir olmayan bazı yeni C# dil öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e3739-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="e3739-112">İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="e3739-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="e3739-113">C# 6 sürümde eklenen özelliklerin tam olarak ifade ağaçlarında yazılmış gibi görünmüyor.</span><span class="sxs-lookup"><span data-stu-id="e3739-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="e3739-114">Bunun yerine, ifade ağaçları eşdeğer, önceki sözdiziminde daha yeni özellikleri sunulur.</span><span class="sxs-lookup"><span data-stu-id="e3739-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="e3739-115">Bu düşündüğünüzden gibi sınırlandırılmasıdır kadar olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e3739-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="e3739-116">Aslında, bu yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu hala olasılıkla aynı çalışacağını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e3739-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="e3739-117">Bu kısıtlamalarla bile ifade ağaçları yorumlama ve veri yapısı olarak temsil edilir kodu değiştirme dayanan dinamik algoritmaları oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3739-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="e3739-118">Güçlü bir araçtır ve ne yaptıklarını gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosistemi özelliklerini biridir.</span><span class="sxs-lookup"><span data-stu-id="e3739-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

