---
description: 'Daha fazla bilgi edinin: System. Math yöntemleri'
title: System.Math Yöntemleri
ms.date: 03/30/2017
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
ms.openlocfilehash: e97e0a16b6eafdb57f4aaf72d62788e6657afbdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681350"
---
# <a name="systemmath-methods"></a><span data-ttu-id="4ea4f-103">System.Math Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4ea4f-103">System.Math Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4ea4f-104">Aşağıdaki <xref:System.Math> yöntemleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-104">does not support the following <xref:System.Math> methods.</span></span>  
  
- <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
- <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="4ea4f-105">.NET farklılıkları</span><span class="sxs-lookup"><span data-stu-id="4ea4f-105">Differences from .NET</span></span>  

 <span data-ttu-id="4ea4f-106">.NET Framework, SQL Server farklı yuvarlama semantiklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-106">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="4ea4f-107"><xref:System.Math.Round%2A>.NET Framework yöntemi, sonraki daha yüksek basamak yerine, 5 içinde sonlanan sayıların en yakın çift basamağına yuvarlamasını *Banker yuvarlama* işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-107">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="4ea4f-108">Örneğin, 2,5 2 ' ye yuvarlanır, ancak 3,5 4 ' e yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-108">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="4ea4f-109">(Bu teknik, büyük veri işlemlerinde daha yüksek değerlere yönelik doğru bir sapmanın önlenmesine yardımcı olur.)</span><span class="sxs-lookup"><span data-stu-id="4ea4f-109">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="4ea4f-110">SQL 'de, `ROUND` işlev her zaman 0 ' dan uzağa yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-110">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="4ea4f-111">Bu nedenle 2,5, .NET Framework 2 ' ye yuvarlanarak 3 ' e yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-111">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4ea4f-112">SQL semantiğinin üzerinden geçer `ROUND` ve Banker yuvarlama uygulamayı denemez.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-112">passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ea4f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ea4f-113">See also</span></span>

- [<span data-ttu-id="4ea4f-114">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4ea4f-114">Data Types and Functions</span></span>](data-types-and-functions.md)
