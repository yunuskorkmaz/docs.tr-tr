---
title: -Nesne olarak diziler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977189"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

C# ' ta aslında nesneler ve yalnızca adreslenebilir C ve C++ gibi bitişik bellek bölümlerinin dizilerdir. <xref:System.Array> Tüm dizi türleri soyut temel türüdür. Özellikleri ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir. Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> dizinin uzunluğunu alınacağı özellik. Aşağıdaki kod uzunluğunu atar `numbers` dizisi `5`, adında bir değişkene `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <xref:System.Array> Diğer birçok kullanışlı yöntemler ve Özellikler diziler kopyalama sıralama ve arama için sınıf sağlar.  
  
## <a name="example"></a>Örnek

 Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
