---
title: "Nesne Olarak Diziler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a>Nesne Olarak Diziler (C# Programlama Kılavuzu)
C# ' ta gerçekte nesneleri ve bitişik bellek C ve C++ olduğu gibi yalnızca adreslenebilir bölümlerinin dizidir. <xref:System.Array>soyut taban tüm dizi türleri türüdür. Özelliklerini ve diğer sınıf üyeleri kullanabilirsiniz, <xref:System.Array> sahiptir. Bunun bir örneğini kullanarak <xref:System.Array.Length%2A> bir dizi uzunluğu, alınacağı özellik. Aşağıdaki kod uzunluğu atar `numbers` olan dizi `5`, adlı bir değişkene `lengthOfNumbers`:  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <xref:System.Array> Sınıfı, diğer birçok kullanışlı yöntemler ve sıralama, arama ve dizileri kopyalamak için özellikler sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Array.Rank%2A> bir dizinin boyut sayısını görüntülemek için özellik.  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Basit diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
