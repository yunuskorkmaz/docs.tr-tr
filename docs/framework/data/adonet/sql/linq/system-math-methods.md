---
title: System.Math yöntemleri
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 8d0ac9e9eb394deaa9dcab1a276e3ef00e2ac01b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357122"
---
# <a name="systemmath-methods"></a><span data-ttu-id="6328d-102">System.Math yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6328d-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6328d-103"> Aşağıdaki desteklemiyor <xref:System.Math> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6328d-103"> does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="6328d-104">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="6328d-104">Differences from .NET</span></span>  
 <span data-ttu-id="6328d-105">.NET Framework, SQL Server'dan farklı yuvarlama semantiği sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6328d-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="6328d-106"><xref:System.Math.Round%2A> Yöntemi .NET Framework'teki gerçekleştirir *Banker yuvarlaması*,.5 içinde sona erer numaraları yuvarlanacağını burada yerine çift basamaklı sonraki yüksek sayıya en yakın.</span><span class="sxs-lookup"><span data-stu-id="6328d-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="6328d-107">Örneğin, 3.5 4'e yuvarlar sırada 2.5 2'ye yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="6328d-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="6328d-108">(Bu teknik daha yüksek değerleri büyük veri işlemlerde doğru sistematik sapması önlemeye yardımcı olur.)</span><span class="sxs-lookup"><span data-stu-id="6328d-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="6328d-109">SQL'de, `ROUND` işlevi yerine 0 çıktığınızda her zaman yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="6328d-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="6328d-110">Bu nedenle, .NET Framework 2. yuvarlama ile contrasted 3 2.5 yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="6328d-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6328d-111"> SQL geçirir aracılığıyla `ROUND` semantiği ve Banker yuvarlaması uygulamak denemez.</span><span class="sxs-lookup"><span data-stu-id="6328d-111"> passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6328d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6328d-112">See Also</span></span>  
 [<span data-ttu-id="6328d-113">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6328d-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
