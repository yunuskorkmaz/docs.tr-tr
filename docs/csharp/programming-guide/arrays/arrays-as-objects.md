---
title: Nesneler olarak diziler-C# Programlama Kılavuzu
description: C# içindeki diziler soyut temel tür dizisinin nesneleridir. Array öğesinin özelliklerini ve diğer sınıf üyelerini (length özelliği gibi) kullanabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474728"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

C# ' de, diziler aslında nesneler ve yalnızca C ve C++ ' da olduğu gibi bitişik belleğin adreslenebilir bölgelerini değildir. <xref:System.Array>tüm dizi türlerinin soyut temel türüdür. Özellikleri ve olan diğer sınıf üyelerini kullanabilirsiniz <xref:System.Array> . Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır. Aşağıdaki kod, dizi uzunluğunu, `numbers` yani `5` adlı bir değişkene atar `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array>Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.

## <a name="example"></a>Örnek

Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
