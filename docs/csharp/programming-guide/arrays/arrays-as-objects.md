---
title: Nesneler olarak diziler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715100"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

' C#De, diziler aslında nesneler ve yalnızca C ve C++' de olduğu gibi bitişik belleğin adreslenebilir bölgelerini içermez. <xref:System.Array>, tüm dizi türlerinin soyut temel türüdür. <xref:System.Array> sahip olduğu özellikleri ve diğer sınıf üyelerini kullanabilirsiniz. Bunun bir örneği, bir dizinin uzunluğunu almak için <xref:System.Array.Length%2A> özelliğini kullanmaktır. Aşağıdaki kod, `5``numbers` dizinin uzunluğunu `lengthOfNumbers`adlı bir değişkene atar:

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.

## <a name="example"></a>Örnek

Bu örnek, bir dizinin boyut sayısını göstermek için <xref:System.Array.Rank%2A> özelliğini kullanır.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
