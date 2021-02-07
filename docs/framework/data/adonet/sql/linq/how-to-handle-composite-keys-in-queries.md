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
