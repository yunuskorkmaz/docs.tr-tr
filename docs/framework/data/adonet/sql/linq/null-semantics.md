---
title: Null Semantikler
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 739ee95be45d7d64a4ad1678837b9706a533f07d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147547"
---
# <a name="null-semantics"></a><span data-ttu-id="2a8b2-102">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="2a8b2-102">Null Semantics</span></span>

<span data-ttu-id="2a8b2-103">Aşağıdaki tabloda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `null` ( `Nothing` Visual Basic) sorunların ele alındığı, belgelerin çeşitli bölümlerinin bağlantıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="2a8b2-104">Konu</span><span class="sxs-lookup"><span data-stu-id="2a8b2-104">Topic</span></span>|<span data-ttu-id="2a8b2-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a8b2-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="2a8b2-106">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="2a8b2-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="2a8b2-107">Bu konunun "null semantiği" bölümünde, üç durumlu SQL Boolean ile iki durumlu ortak dil çalışma zamanı (CLR) <xref:System.Boolean> , değişmez değer `Nothing` (Visual Basic) ve `null` (C#) ve diğer benzer sorunlar yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="2a8b2-108">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="2a8b2-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="2a8b2-109">Bu konunun "null semantiği" bölümünde ' de null karşılaştırma semantiği açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2a8b2-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="2a8b2-110">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2a8b2-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="2a8b2-111">Bu konunun ".NET farkları" bölümünde, <xref:System.String.LastIndexOf%2A> dizenin null veya bulunan konumun 0 olduğu anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="2a8b2-112">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="2a8b2-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="2a8b2-113"><xref:System.Linq.Enumerable.Sum%2A> `null` `Nothing` Yalnızca null değerleri veya boş bir dizi içeren bir sıra için 0 yerine, işlecin (Visual Basic) olarak nasıl değerlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a8b2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-114">See also</span></span>

- [<span data-ttu-id="2a8b2-115">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2a8b2-115">Data Types and Functions</span></span>](data-types-and-functions.md)
