---
title: Tek Boyutlu Diziler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: c2f26fd74a596ada21eef578e58c9cd8e0305d6c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891869"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)

Aşağıdaki örnekte gösterildiği gibi beş tamsayı tek boyutlu bir dizi bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Bu dizinin öğeleri içeren `array[0]` için `array[4]`. [Yeni](../../../csharp/language-reference/keywords/new.md) işleci dizi oluşturmak ve varsayılan değerlerine dizi öğelerini başlatmak için kullanılır. Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.  
  
 Dize öğesi depolayan bir dizi aynı şekilde bildirilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Bildirimi, bağlı bir diziyi başlatmaya mümkündür, bu durumda sıra belirticisi gerekli değil çünkü zaten başlatma listedeki öğelerin sayısı tarafından sağlanır. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 Dize dizisi aynı şekilde başlatılabilir. Bir dize dizisi bildirimi her dizi öğesi günün bir adı nerede başlatılır verilmiştir:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Bir dizi bildirimi üzerine başlattığınızda, aşağıdaki kısayolları kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Bir dizi değişkeni başlatma olmadan belirtmek mümkündür, ancak kullanmalısınız `new` Bu değişken için bir dizi atadığınızda işleci. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0, örtük olarak yazılan diziler tanıtır. Daha fazla bilgi için [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Değer türü ve referans türü diziler

 Aşağıdaki dizi bildirimi göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Bu ifade sonucu bağlıdır `SomeType` bir değer türü veya bir başvuru türü. Bir değer türü ise, her biri türüne sahip bir dizi 10 öğelerin deyimi oluşturur `SomeType`. Varsa `SomeType` bir başvuru türüdür deyimi her biri için bir null başvuru başlatılır 10 öğe, bir dizi oluşturur.  
  
 Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [türleri](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Array>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Diziler](../../../csharp/programming-guide/arrays/index.md)  
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
