---
title: Null Semantikler
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792974"
---
# <a name="null-semantics"></a><span data-ttu-id="7c585-102">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="7c585-102">Null Semantics</span></span>
<span data-ttu-id="7c585-103">Aşağıdaki tabloda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `null` (`Nothing` Visual Basic) sorunların ele alındığı, belgelerin çeşitli bölümlerinin bağlantıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7c585-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="7c585-104">Konu</span><span class="sxs-lookup"><span data-stu-id="7c585-104">Topic</span></span>|<span data-ttu-id="7c585-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c585-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7c585-106">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="7c585-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="7c585-107">Bu konunun "null semantiği" bölümünde, üç durumlu SQL Boolean ile iki durumlu ortak dil çalışma <xref:System.Boolean>zamanı (CLR), değişmez değer `Nothing` (Visual Basic) ve `null` (C#) ve benzeri benzer tartışmalar yer almaktadır. çıkışları.</span><span class="sxs-lookup"><span data-stu-id="7c585-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="7c585-108">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="7c585-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="7c585-109">Bu konunun "null semantiği" bölümünde ' de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]null karşılaştırma semantiği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7c585-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="7c585-110">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7c585-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="7c585-111">Bu konunun <xref:System.String.LastIndexOf%2A> ".net farkları" bölümünde, dizenin null veya bulunan konumun 0 olduğu anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="7c585-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="7c585-112">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="7c585-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="7c585-113">Yalnızca null değerleri <xref:System.Linq.Enumerable.Sum%2A> veya boş bir `null` dizi`Nothing` içeren bir sıra için 0 yerine, işlecin (Visual Basic) olarak nasıl değerlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7c585-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c585-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c585-114">See also</span></span>

- [<span data-ttu-id="7c585-115">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7c585-115">Data Types and Functions</span></span>](data-types-and-functions.md)
