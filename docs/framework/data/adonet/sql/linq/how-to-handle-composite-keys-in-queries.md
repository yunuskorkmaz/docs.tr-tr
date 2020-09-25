---
title: 'Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: bc16dde89f67572b03102b1c091993ed163b443c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203533"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Nasıl yapılır: Sorgularda Bileşik Anahtarlar İşleme

Bazı işleçler yalnızca bir bağımsız değişken alabilir. Bağımsız değişkeninizdeki veritabanından birden fazla sütun içermesi gerekiyorsa, birleşimi temsil etmek için anonim bir tür oluşturmanız gerekir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `GroupBy` yalnızca bir bağımsız değişken içerebilen işleci çağıran bir sorguyu gösterir `key` .  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Örnek  

 Aynı durum, aşağıdaki örnekte olduğu gibi birleşimlere aittir:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
