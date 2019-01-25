---
title: 'Nasıl yapılır: Sorgularda bileşik anahtarlar işleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 0ee0bda8c3ee46cb6e08ee415def68a4a9832617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523487"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Nasıl yapılır: Sorgularda bileşik anahtarlar işleme
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
