---
title: Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e01b9463eca88858633b847be256ae5b063459b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313507"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)
Bir dizi veri yapısında aynı türde birden fazla değişken depolayabilirsiniz. Dizi öğeleri türü belirterek bildirin.  
  
 `type[] arrayName;`  
  
 Aşağıdaki örnekler tek boyutlu, çok boyutlu ve basit diziler oluşturun:  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a>Dizi genel bakış  
 Bir dizi aşağıdaki özelliklere sahiptir:  
  
-   Bir dizi olabilir [tek boyutlu](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [çok boyutlu](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) veya [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).  
  
-   Array örneği oluşturulduğunda boyut sayısını ve her boyutun uzunluğu oluşturulur. Örneğin ömrü boyunca bu değerler değiştirilemez.  
  
-   Varsayılan değerleri sayısal dizi öğelerinin sıfıra ayarlanır ve başvuru öğeleri ayarlanır null.  
  
-   Basit dizi oluşan bir dizi ve bu nedenle öğeleri başvuru türleri için başlatılan `null`.  
  
-   Dizi dizini sıfır olan: sahip bir dizi `n` öğeleri dizine `0` için `n-1`.  
  
-   Dizi öğeleri bir dizi türü de dahil olmak üzere, herhangi bir türde olabilir.  
  
-   Dizi türleri [başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md) soyut taban türünden türetilmiş <xref:System.Array>. Bu tür uygulayan beri <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>, kullanabileceğiniz [foreach](../../../csharp/language-reference/keywords/foreach-in.md) yineleme tüm diziler C# üzerinde.  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
-   [Nesne Olarak Diziler](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [Dizilerle foreach kullanma](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [Dizileri Bağımsız Değişkenler Olarak Geçirme](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [ref ve out Kullanarak Dizileri Geçirme](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Koleksiyonlar](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Dizi koleksiyon türü](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
