---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: sorgularda bileşik anahtarları Işleme'
title: 'Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 9d7c68495810bee6a383d98a75694e7cd24f1015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738877"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="4576a-103">Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme</span><span class="sxs-lookup"><span data-stu-id="4576a-103">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="4576a-104">Bazı işleçler yalnızca bir bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="4576a-104">Some operators can take only one argument.</span></span> <span data-ttu-id="4576a-105">Bağımsız değişkeninizdeki veritabanından birden fazla sütun içermesi gerekiyorsa, birleşimi temsil etmek için anonim bir tür oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4576a-105">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4576a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4576a-106">Example</span></span>  

 <span data-ttu-id="4576a-107">Aşağıdaki örnek, `GroupBy` yalnızca bir bağımsız değişken içerebilen işleci çağıran bir sorguyu gösterir `key` .</span><span class="sxs-lookup"><span data-stu-id="4576a-107">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4576a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4576a-108">Example</span></span>  

 <span data-ttu-id="4576a-109">Aynı durum, aşağıdaki örnekte olduğu gibi birleşimlere aittir:</span><span class="sxs-lookup"><span data-stu-id="4576a-109">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4576a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4576a-110">See also</span></span>

- [<span data-ttu-id="4576a-111">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="4576a-111">Query Concepts</span></span>](query-concepts.md)
