---
title: System.Math Yöntemleri
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: 5200f31bd319bad49651c3096e1c1364a8003377
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613768"
---
# <a name="systemmath-methods"></a><span data-ttu-id="4543d-102">System.Math Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4543d-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4543d-103">şunları desteklemez <xref:System.Math> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4543d-103">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="4543d-104">.NET arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="4543d-104">Differences from .NET</span></span>  
 <span data-ttu-id="4543d-105">.NET Framework, SQL Server'dan farklı yuvarlama semantiğe sahip.</span><span class="sxs-lookup"><span data-stu-id="4543d-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="4543d-106"><xref:System.Math.Round%2A> .NET Framework'teki yöntemi gerçekleştirir *Banker yuvarlama*,.5 içinde biten sayı YUVARLA burada sonraki daha yüksek sayıya bile basamak yerine en yakın.</span><span class="sxs-lookup"><span data-stu-id="4543d-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="4543d-107">Örneğin, 3.5, 4'e yuvarlanır sırada 2.5 2'ye yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="4543d-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="4543d-108">(Bu teknikleri sistematik sapması büyük veri işlemlerde yüksek değerler doğru önlemeye yardımcı olur.)</span><span class="sxs-lookup"><span data-stu-id="4543d-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="4543d-109">SQL, `ROUND` işlevi yerine 0 uzağa her zaman yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="4543d-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="4543d-110">Bu nedenle, 3, 2 .NET Framework'teki yuvarlama ile karşıtlıklar, 2.5 yuvarlar.</span><span class="sxs-lookup"><span data-stu-id="4543d-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4543d-111">SQL geçirir aracılığıyla `ROUND` semantiği ve Banker yuvarlaması uygulamak denemez.</span><span class="sxs-lookup"><span data-stu-id="4543d-111">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4543d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4543d-112">See also</span></span>

- [<span data-ttu-id="4543d-113">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4543d-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
