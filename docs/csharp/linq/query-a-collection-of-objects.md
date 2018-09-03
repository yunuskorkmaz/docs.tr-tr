---
title: (C# üzerinde LINQ) nesneler koleksiyonunu sorgulama
description: Bilgi koleksiyonları LINQ C# kullanarak nasıl sorgulama.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480926"
---
# <a name="query-a-collection-of-objects"></a>Nesneler koleksiyonunu sorgulama

Bu örnek bir listesi basit bir sorgu gerçekleştirmek nasıl gösterir `Student` nesneleri. Her `Student` nesnesi Öğrenci ve öğrencinin puanları üzerindeki dört incelemelerde temsil eden bir liste hakkında bazı temel bilgileri içerir.  
  
Bu uygulama, aynı kullanan çok sayıda diğer örnekler için bu bölümdeki framework görür `students` veri kaynağı.  
  
## <a name="example"></a>Örnek

Aşağıdaki sorgu bir puana 90 ya da kendi ilk sınavı büyük öğrencilere döndürür.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Bu sorgu, denemenizi etkinleştirmek kasıtlı olarak basit bir işlemdir. Örneğin, daha fazla koşullarında deneyebilirsiniz `where` yan tümcesi veya kullanımı bir `orderby` sonuçları sıralamak için yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)  
- [Dize ilişkilendirme](../language-reference/tokens/interpolated.md)