---
description: 'Daha fazla bilgi edinin: null semantiği'
title: Null Semantikler
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 2326cd20a225f31693260aa038477f1f6090d02f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695586"
---
# <a name="null-semantics"></a><span data-ttu-id="226ec-103">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="226ec-103">Null Semantics</span></span>

<span data-ttu-id="226ec-104">Aşağıdaki tabloda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `null` ( `Nothing` Visual Basic) sorunların ele alındığı, belgelerin çeşitli bölümlerinin bağlantıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="226ec-104">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="226ec-105">Konu</span><span class="sxs-lookup"><span data-stu-id="226ec-105">Topic</span></span>|<span data-ttu-id="226ec-106">Description</span><span class="sxs-lookup"><span data-stu-id="226ec-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="226ec-107">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="226ec-107">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="226ec-108">Bu konunun "null semantiği" bölümünde, üç durumlu SQL Boolean ile iki durumlu ortak dil çalışma zamanı (CLR) <xref:System.Boolean> , değişmez değer `Nothing` (Visual Basic) ve `null` (C#) ve diğer benzer sorunlar yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="226ec-108">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="226ec-109">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="226ec-109">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="226ec-110">Bu konunun "null semantiği" bölümünde ' de null karşılaştırma semantiği açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="226ec-110">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="226ec-111">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="226ec-111">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="226ec-112">Bu konunun ".NET farkları" bölümünde, <xref:System.String.LastIndexOf%2A> dizenin null veya bulunan konumun 0 olduğu anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="226ec-112">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="226ec-113">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="226ec-113">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="226ec-114"><xref:System.Linq.Enumerable.Sum%2A> `null` `Nothing` Yalnızca null değerleri veya boş bir dizi içeren bir sıra için 0 yerine, işlecin (Visual Basic) olarak nasıl değerlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="226ec-114">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="226ec-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="226ec-115">See also</span></span>

- [<span data-ttu-id="226ec-116">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="226ec-116">Data Types and Functions</span></span>](data-types-and-functions.md)
