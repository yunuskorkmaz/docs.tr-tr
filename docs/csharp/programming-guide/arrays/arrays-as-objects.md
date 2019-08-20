---
title: Nesneler olarak diziler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597354"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

' C#De, diziler aslında nesneler ve yalnızca C ve C++' de olduğu gibi bitişik belleğin adreslenebilir bölgelerini içermez. <xref:System.Array>tüm dizi türlerinin soyut temel türüdür. Özellikleri ve olan <xref:System.Array> diğer sınıf üyelerini kullanabilirsiniz. Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır. Aşağıdaki kod, `numbers` dizi uzunluğunu, yani `5`adlı `lengthOfNumbers`bir değişkene atar:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar.  
  
## <a name="example"></a>Örnek

 Bu örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Diziler](./index.md)
- [Tek Boyutlu Diziler](./single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](./multidimensional-arrays.md)
- [Düzensiz Diziler](./jagged-arrays.md)
