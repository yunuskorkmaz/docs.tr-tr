---
title: -Dizilerle foreach kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 05/23/2018
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: a22cb939370b38780881eca0d9585a14002c8250
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683723"
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a>Dizilerle foreach kullanma (C# Programlama Kılavuzu)

[Foreach](../../language-reference/keywords/foreach-in.md) deyimi bir dizi öğelerinde yineleme yapmak için basit ve temiz bir yol sağlar.

Tek boyutlu diziler için `foreach` deyimi, artan dizin sırasıyla dizini 0'ile başlayıp diziniyle öğeleri işler `Length - 1`:

 [!code-csharp[csProgGuideArrays#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#28)]

En sağdaki boyutu dizinleri artan ilk sonra sonraki sol boyut vb. için sol olduğuna gibi çok boyutlu diziler için öğeleri geçirilir:

 [!code-csharp[csProgGuideArrays#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#29)]

Ancak, çok boyutlu dizilerle, iç içe bir kullanarak [için](../../language-reference/keywords/for.md) döngü, dizi öğeleri işlemek sırada üzerinde daha fazla denetim sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../index.md)
- [Diziler](index.md)
- [Tek Boyutlu Diziler](single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](multidimensional-arrays.md)
- [Düzensiz Diziler](jagged-arrays.md)
