---
title: Tek boyutlu diziler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 719e4463806c9c7e8b5407f2494c3b548ffa43e8
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200786"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tek Boyutlu Diziler (C# Programlama Kılavuzu)

Aşağıdaki örnekte gösterildiği gibi beş tamsayı tek boyutlu bir dizi bildirebilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Bu dizinin öğeleri içeren `array[0]` için `array[4]`. [Yeni](../../../csharp/language-reference/keywords/new.md) işleci dizi oluşturmak ve varsayılan değerlerine dizi öğelerini başlatmak için kullanılır. Bu örnekte, tüm dizi öğeleri sıfır olarak başlatılır.  
  
 Dize öğesi depolayan bir dizi aynı şekilde bildirilebilir. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Dizi başlatma

 Bildirimi, bağlı bir diziyi başlatmaya mümkündür, bu durumda uzunluğu tanımlayıcısı gerekli değildir çünkü zaten başlatma listedeki öğelerin sayısı tarafından sağlanır. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Dize dizisi aynı şekilde başlatılabilir. Bir dize dizisi bildirimi her dizi öğesi günün bir adı nerede başlatılır verilmiştir:  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Bir dizi bildirimi üzerine başlattığınızda, aşağıdaki kısayolları kullanabilirsiniz:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Bir dizi değişkeni başlatma olmadan belirtmek mümkündür, ancak kullanmalısınız `new` Bu değişken için bir dizi atadığınızda işleci. Örneğin:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0, örtük olarak yazılan diziler tanıtır. Daha fazla bilgi için [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Değer türü ve referans türü diziler

 Aşağıdaki dizi bildirimi göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Bu ifade sonucu bağlıdır `SomeType` bir değer türü veya bir başvuru türü. Bir değer türü ise, her biri türüne sahip bir dizi 10 öğelerin deyimi oluşturur `SomeType`. Varsa `SomeType` bir başvuru türüdür deyimi her biri için bir null başvuru başlatılır 10 öğe, bir dizi oluşturur.  
  
 Değer türleri ve başvuru türleri hakkında daha fazla bilgi için bkz. [türleri](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Diziler](../../../csharp/programming-guide/arrays/index.md)
- [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
