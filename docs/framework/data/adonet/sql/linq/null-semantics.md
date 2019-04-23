---
title: Null Semantikler
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: eb1e96ba44c5d64e8366a654c2d06d89c9b46c9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172763"
---
# <a name="null-semantics"></a><span data-ttu-id="7a7d9-102">Null Semantikler</span><span class="sxs-lookup"><span data-stu-id="7a7d9-102">Null Semantics</span></span>
<span data-ttu-id="7a7d9-103">Aşağıdaki tabloda çeşitli bölümlerine bağlantılar sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri nerede `null` (`Nothing` Visual Basic'te) sorunlar ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="7a7d9-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="7a7d9-104">Konu</span><span class="sxs-lookup"><span data-stu-id="7a7d9-104">Topic</span></span>|<span data-ttu-id="7a7d9-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a7d9-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7a7d9-106">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="7a7d9-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="7a7d9-107">Bu konunun "Null Semantikler" bölümünde üç durumlu SQL Boole iki durumlu ortak dil çalışma zamanı (CLR) karşı tartışılması içerir <xref:System.Boolean>, değişmez değer `Nothing` (Visual Basic) ve `null` (C#) ve diğer benzer sorun.</span><span class="sxs-lookup"><span data-stu-id="7a7d9-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="7a7d9-108">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="7a7d9-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="7a7d9-109">Bu konunun "Null Semantikler" bölümünde, null karşılaştırma semantiği açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7a7d9-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="7a7d9-110">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="7a7d9-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="7a7d9-111">Bu konunun "Farklar gelen .NET" bölümünde değerinin 0'dan nasıl açıklar <xref:System.String.LastIndexOf%2A> dizenin null olduğunu ya da bulunan konumu 0 olduğu anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="7a7d9-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="7a7d9-112">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="7a7d9-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="7a7d9-113">Açıklayan nasıl <xref:System.Linq.Enumerable.Sum%2A> işleci değerlendirilen `null` (`Nothing` Visual Basic'te) yerine boş bir dizi veya yalnızca null içeren bir dizi için 0.</span><span class="sxs-lookup"><span data-stu-id="7a7d9-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a7d9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7a7d9-114">See also</span></span>

- [<span data-ttu-id="7a7d9-115">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7a7d9-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
