---
title: Nesneler Olarak Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715100"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

C#'da diziler aslında nesnelerdir ve c ve c++'daki gibi bitişik belleğin yalnızca adreslenebilir bölgeleri değildir. <xref:System.Array>tüm dizi türlerinin soyut temel türüdür. Özellikleri ve <xref:System.Array> sahip diğer sınıf üyeleri kullanabilirsiniz. Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliği kullanmaktır. Aşağıdaki kod, dizinin `numbers` uzunluğunu atar, `5`bu da `lengthOfNumbers`, adlı bir değişkene:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

Sınıf, <xref:System.Array> dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.

## <a name="example"></a>Örnek

Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özelliği kullanır.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Basit Diziler](./jagged-arrays.md)
