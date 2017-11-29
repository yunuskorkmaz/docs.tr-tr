---
title: Nesneler koleksiyonunu sorgulama
description: "Koleksiyonları nasıl sorgu."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Ara değerli dizeler](../language-reference/keywords/interpolated-strings.md)
