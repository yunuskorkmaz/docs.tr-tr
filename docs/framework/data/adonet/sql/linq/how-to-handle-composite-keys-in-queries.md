---
title: 'Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 2621ab4db207d1b868fbe3778c30c744201b0506
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135258"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme
Bazı işleçleri, tek bir bağımsız değişken alabilir. Bağımsız değişkeniniz veritabanından birden fazla sütun içermelidir, bileşimini temsil etmek için anonim bir tür oluşturmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çağıran bir sorgu gösterir `GroupBy` yalnızca bir işleç `key` bağımsız değişken.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte olduğu gibi birleşimler için de aynı durum ilgilidir:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
