---
title: -Nesne olarak diziler C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0c4b5dcbd9e227e4edd5f549b687e3ded90ee9bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740495"
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)

C# ' ta aslında nesneler ve yalnızca adreslenebilir C ve C++ gibi bitişik bellek bölümlerinin dizilerdir. <xref:System.Array> Tüm dizi türleri soyut temel türüdür. Özellikleri ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir. Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> dizinin uzunluğunu alınacağı özellik. Aşağıdaki kod uzunluğunu atar `numbers` dizisi `5`, adında bir değişkene `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Diğer birçok kullanışlı yöntemler ve Özellikler diziler kopyalama sıralama ve arama için sınıf sağlar.  
  
## <a name="example"></a>Örnek

 Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
