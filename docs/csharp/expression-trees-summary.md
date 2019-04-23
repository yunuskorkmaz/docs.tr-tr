---
title: İfade ağaçları özeti
description: Kod veri olarak yorumlar ve yapı bu koduna göre yeni işlevselliği dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz hakkında bilgiler bulabilirsiniz.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148635"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="f6dc5-103">İfade ağaçları özeti</span><span class="sxs-lookup"><span data-stu-id="f6dc5-103">Expression Trees Summary</span></span>

[<span data-ttu-id="f6dc5-104">Önceki--İfade çevirme</span><span class="sxs-lookup"><span data-stu-id="f6dc5-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="f6dc5-105">Bu seride, nasıl kullanacağınızı öğrendiniz *ifade ağaçları* kod veri olarak yorumlar ve yapı bu koduna göre yeni işlevselliği dinamik programlar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="f6dc5-106">Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="f6dc5-107">Yalnızca bu kodu inceleyebilirsiniz değil.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-107">You can not only examine that code.</span></span> <span data-ttu-id="f6dc5-108">Özgün koda değiştirilmiş sürümlerini temsil yeni ifade ağaçları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="f6dc5-109">Ayrıca, bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil ya da ortam bu algoritmayı çevirir.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="f6dc5-110">Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="f6dc5-110">Limitations</span></span>

<span data-ttu-id="f6dc5-111">Vardır bazı yeni C# iyi ifade ağaçları Çevir olmayan dil öğeleri.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="f6dc5-112">İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="f6dc5-113">İçinde eklenen özelliklerin birçoğu C# 6 yayın tam olarak ifade ağaçlarında olarak yazılmış görünmez.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="f6dc5-114">Bunun yerine, eşdeğer, eski sözdizimi ifade ağaçlarında yeni özellikler sunulur.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="f6dc5-115">Bu gibi düşünebilirsiniz ilişkin bir sınırlama kadar olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="f6dc5-116">Aslında, yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu yine de büyük olasılıkla aynı çalışacağını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="f6dc5-117">Bu kısıtlamalarla bile ifade ağaçları yorumlama ve bir veri yapısı olarak temsil edilen kod değiştirme dayanan dinamik algoritmaları oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="f6dc5-118">Güçlü bir araçtır ve ne yaptıkları gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosisteminin özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="f6dc5-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
