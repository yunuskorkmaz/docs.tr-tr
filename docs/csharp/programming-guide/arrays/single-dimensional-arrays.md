---
title: Tek Boyutlu Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)
Aşağıdaki örnekte gösterildiği gibi beş tamsayıların tek boyutlu bir dizi bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Bu dizi öğeleri içeren `array[0]` için `array[4]`. [Yeni](../../../csharp/language-reference/keywords/new.md) işleci dizi oluşturmak ve dizi öğeleri varsayılan değerlerine başlatmak için kullanılır. Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.  
  
 Dize öğesi depolayan bir dizi aynı şekilde bildirilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Dizi başlatma  
 Bir dizi bildirimi bağlı Initialize mümkündür; bu durumda sıra belirticisi gerekli değildir başlatma listesindeki öğelerin sayısı tarafından zaten sağlanan çünkü. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Bir dize dizisi aynı şekilde başlatılabilir. Bir dize dizisi bildirimi her dizi öğesi bir günlük adıyla nerede başlatılır verilmiştir:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Bir dizi bildirimi bağlı başlattığınızda aşağıdaki kısayollarını kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Bir dizi değişkeni başlatma olmadan bildirmek mümkündür, ancak kullanmalısınız `new` Bu değişken için bir dizi atadığınızda işleci. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 örtük olarak yazılan diziler tanıtır. Daha fazla bilgi için bkz: [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Değer türü ve başvuru türü diziler  
 Aşağıdaki dizi bildirimi göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Bu deyimi sonucunu bağlıdır `SomeType` bir değer türü veya bir başvuru türü. Değer türü ise, her birinin türü olan bir dizi 10 öğelerinin deyimi oluşturur `SomeType`. Varsa `SomeType` bir başvuru türü deyimi 10 öğelerin her biri için bir null başvuru başlatılır dizisi oluşturur.  
  
 Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz: [türleri](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
