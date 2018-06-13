---
title: Dizilerle foreach kullanma (C# Programlama Kılavuzu)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: b858f35167e24390a729769487ce98908a3d349f
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549461"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit, temiz bir yol sağlar.

Tek boyutlu diziler için `foreach` deyimini işler sırayla dizin 0 ile başlayıp diziniyle artan dizin öğeleri `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

En sağdaki boyutu dizinlerini artan ilk ardından sonraki sol boyut solundaki vb. gibi olduğuna göre çok boyutlu diziler için öğeleri geçiş:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Ancak, çok boyutlu diziler ile iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü dizi öğelerini işlemek hangi sırayla üzerinde daha fazla denetim sağlar.

## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Array>  
 [C# Programlama Kılavuzu](../index.md)  
 [Diziler](index.md)  
 [Tek Boyutlu Diziler](single-dimensional-arrays.md)  
 [Çok Boyutlu Diziler](multidimensional-arrays.md)  
 [Düzensiz Diziler](jagged-arrays.md)
