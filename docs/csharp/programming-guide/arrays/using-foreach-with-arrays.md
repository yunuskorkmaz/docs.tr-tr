---
title: Dizilerle foreach kullanma (C# Programlama Kılavuzu)
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 217408600e40d2ce5197f207c007b858ff3145d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147050"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit ve temiz bir yol sağlar.

Tek boyutlu diziler için `foreach` deyimi, artan dizin sırasıyla dizini 0'ile başlayıp diziniyle öğeleri işler `Length - 1`:

[!code-csharp[csProgGuideArrays#28](./codesnippet/CSharp/using-foreach-with-arrays_1.cs)]

En sağdaki boyutu dizinleri artan ilk sonra sonraki sol boyut vb. için sol olduğuna gibi çok boyutlu diziler için öğeleri geçirilir:

[!code-csharp[csProgGuideArrays#29](./codesnippet/CSharp/using-foreach-with-arrays_2.cs)]

Ancak, çok boyutlu dizilerle, iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü, dizi öğeleri işlemek sırada üzerinde daha fazla denetim sağlar.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Array>  
- [C# Programlama Kılavuzu](../index.md)  
- [Diziler](index.md)  
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)  
- [Çok Boyutlu Diziler](multidimensional-arrays.md)  
- [Düzensiz Diziler](jagged-arrays.md)
