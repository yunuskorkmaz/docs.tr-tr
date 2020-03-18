---
title: Nesneler koleksiyonunu sorgula (C#'da LINQ)
description: C#'da LINQ kullanarak sorgu koleksiyonlarının nasıl olduğunu öğrenin.
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 9b2f5dd09c540800e9a2498d48883357f58c0116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659819"
---
# <a name="query-a-collection-of-objects"></a>Nesneler koleksiyonunu sorgulama

Bu örnek, `Student` nesneler listesi üzerinde basit bir sorgunun nasıl gerçekleştirildirilebildiğini gösterir. Her `Student` nesne, öğrenci hakkında bazı temel bilgiler ve dört sınavda öğrencinin puanlarını temsil eden bir liste içerir.  
  
Bu uygulama, aynı `students` veri kaynağını kullanan bu bölümdeki diğer birçok örnek için bir çerçeve görevi görehizmet eder.  
  
## <a name="example"></a>Örnek

Aşağıdaki sorgu, ilk sınavda 90 veya daha fazla puan alan öğrencileri döndürür.  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
Bu sorgu deneme etkinleştirmek için kasıtlı olarak basittir. Örneğin, `where` yan tümcede daha fazla koşul `orderby` deneyebilir veya sonuçları sıralamak için bir yan tümce kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
- [Dize ilişkilendirme](../language-reference/tokens/interpolated.md)
