---
title: Join tümcesinin sonuçlarını sıralama
description: Join tümcesinin sonuçlarını sıralama yapma.
ms.date: 12/1/2016
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f426152e614ed9a9c4aa41d7ba7cb8ddf1cd3063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="order-the-results-of-a-join-clause"></a>Join tümcesinin sonuçlarını sıralama
Bu örnek, bir birleştirme işlemi sonuçlarını sıralama gösterilmektedir. Sıralama birleştirme sonrasında gerçekleştirildiğini unutmayın. Kullanabilirsiniz ancak bir `orderby` yan tümcesi bir veya daha fazla kaynak ile dizilerinin birleştirme öncesinde, genellikle bunu önermiyoruz. Bazı LINQ sağlayıcıları bu birleştirme sonrasında sıralama koruyabilir değil.  
  
## <a name="example"></a>Örnek  
 Bu sorgu, bir grup birleşim oluşturur ve hala kapsam içi kategori öğesi temelinde grupları sıralar. Anonim tür başlatıcısı bir alt sorgu ürünleri serisinden eşleşen tüm öğeleri sıralar.  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [orderby yan tümcesi](../language-reference/keywords/orderby-clause.md)  
 [join yan tümcesi](../language-reference/keywords/join-clause.md) 
