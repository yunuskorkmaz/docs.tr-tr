---
title: Nesneler koleksiyonunu sorgulama
description: Koleksiyonları nasıl sorgu.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="query-a-collection-of-objects"></a>Nesneler koleksiyonunu sorgulama
Bu örnek listesini basit bir sorgu gerçekleştirme gösterir `Student` nesneleri. Her `Student` nesnesi Öğrenci ve dört incelemelerde öğrencinin başarı gösteren liste hakkında bazı temel bilgileri içerir.  
  
 Aynı kullanan çok sayıda diğer örnekler için bu bölümdeki framework olarak bu uygulamaya hizmet `students` veri kaynağı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu 90 veya kendi ilk incelemesi üzerinde daha büyük bir puan alınan Öğrenciler döndürür.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Bu sorgu, deneme etkinleştirmek kasıtlı olarak basit bir işlemdir. Örneğin, daha fazla koşullarında deneyebilirsiniz `where` yan tümcesi ya da kullanım bir `orderby` sonuçları sıralamak için yan tümcesi.  
  

## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)  
 [Dize ilişkilendirme](../language-reference/tokens/interpolated.md)
