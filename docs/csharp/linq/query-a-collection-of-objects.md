---
title: Nesneler koleksiyonunu sorgulama
description: Koleksiyonları nasıl sorgu.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: a62e5c6324d15376f1b42ad078eeb883b05ef14f
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="query-a-collection-of-objects"></a>Nesneler koleksiyonunu sorgulama
Bu örnek listesini basit bir sorgu gerçekleştirme gösterir `Student` nesneleri. Her `Student` nesnesi Öğrenci ve dört incelemelerde öğrencinin başarı gösteren liste hakkında bazı temel bilgileri içerir.  
  
 Aynı kullanan çok sayıda diğer örnekler için bu bölümdeki framework olarak bu uygulamaya hizmet `students` veri kaynağı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu 90 veya kendi ilk incelemesi üzerinde daha büyük bir puan alınan Öğrenciler döndürür.  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 Bu sorgu, deneme etkinleştirmek kasıtlı olarak basit bir işlemdir. Örneğin, daha fazla koşullarında deneyebilirsiniz `where` yan tümcesi ya da kullanım bir `orderby` sonuçları sıralamak için yan tümcesi.  
  

## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Query Expressions](index.md)  
 [Dize ilişkilendirme](../language-reference/tokens/interpolated.md)
