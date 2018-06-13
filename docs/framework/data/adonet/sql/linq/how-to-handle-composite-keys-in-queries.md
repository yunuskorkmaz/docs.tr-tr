---
title: 'Nasıl yapılır: bileşik anahtarlar sorgularda işlemek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 26c281445b84d3b3f85980de6ae4076411bb4fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354246"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Nasıl yapılır: bileşik anahtarlar sorgularda işlemek
Bazı işleçleri, tek bir bağımsız değişken alabilir. Bağımsız değişkeniniz veritabanından birden fazla sütunu içermelidir birleşimi temsil etmek için anonim bir tür oluşturmanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, çağıran bir sorgu gösterir `GroupBy` tek sürebilir işleci `key` bağımsız değişkeni.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Birleştirme, aşağıdaki örnekte olduğu gibi için de aynı durum geçerlidir:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
