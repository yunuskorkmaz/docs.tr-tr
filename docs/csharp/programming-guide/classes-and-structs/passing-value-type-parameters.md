---
title: -Değer türü parametrelerini geçirme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: ba693948bce91fa80f0c6cd73f2d5fc537e5f900
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423746"
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
A [değer türü](../../../csharp/language-reference/keywords/value-types.md) değişkeni doğrudan öğesine verilerini içeren bir [başvuru türü](../../../csharp/language-reference/keywords/reference-types.md) verilerine bir başvuru içeren bir değişkeni. Bir değer türü değişkenine bir yönteme değere göre geçirme yöntemine değişkenin bir kopyasını ileterek anlamına gelir. Yöntem içinde gerçekleşmesi değişiklikleri parametresine bağımsız değişkeninde depolanan özgün veriler herhangi bir etkisi vardır. Çağrılan yöntem bağımsız değişkeninin değerini değiştirmek istiyorsanız, başvuruya göre geçmelidir kullanarak [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü. Ayrıca [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) değeri değiştirilmeyecektir güvence altına almak sırasında kopya önlemek için başvuruya göre bir değer parametresini geçirmek için anahtar sözcüğü. Kolaylık olması için aşağıdaki örneklerde `ref`.  
  
## <a name="passing-value-types-by-value"></a>Değere göre geçirme değer türleri  
 Aşağıdaki örnek, geçirme değer türü gösterir. parametre değeri. Değişken `n` yöntemine geçirilen değere göre `SquareIt`. Yöntemi içinde gerçekleşen tüm değişiklikler özgün değerin değişkeninin hiçbir etkisi sahip.  
  
 [!code-csharp[csProgGuideParameters#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#3)]  
  
 Değişken `n` bir değer türüdür. Değer verisini içerdiği `5`. Zaman `SquareIt` çağrılır, içeriğini `n` parametrede kopyalanır `x`, yöntem içinde kare. İçinde `Main`, ancak değeri `n` çağırdıktan sonra aynıdır `SquareIt` haliyle yöntemiydi önce. Yöntemin içinde yer alan bu değişiklik yalnızca yerel değişken etkiler `x`.  
  
## <a name="passing-value-types-by-reference"></a>Başvuruya göre geçirme değer türleri  
 Bağımsız değişken olarak geçirilen dışında aşağıdaki örnek önceki örnekle aynıdır bir `ref` parametresi. Temel alınan bağımsız değişkeninin değerini `n`, ne zaman değişir `x` yöntemi değiştirildi.  
  
 [!code-csharp[csProgGuideParameters#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#4)]  
  
 Bu örnekte, bu değeri değil `n` yapan; bunun yerine, bir başvuru `n` geçirilir. Parametre `x` değil bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md); bir başvurudur bir `int`, bu durumda, bir başvuru `n`. Bu nedenle, `x` kare bir yöntemde, aslında kare nedir `x` başvurduğu, `n`.  
  
## <a name="swapping-value-types"></a>Değer türleri değiştirme  
 Burada iki değişkenin yönteme geçirin ve bunların içeriğini yöntemi değiştirir swap yöntemi bağımsız değişken değerlerini değiştirme, yaygın bir örnektir. Swap yöntemi için bağımsız değişkenler başvuruya göre geçmesi gerekir. Aksi takdirde, yerel kopyalarını parametreleri yöntemi içinde takas ve çağıran yöntemin herhangi bir değişiklik oluşur. Aşağıdaki örnek, tamsayı değerlerini değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#5)]  
  
 Çağırdığınızda `SwapByRef` yöntemi, kullanım `ref` çağrısında, aşağıdaki örnekte gösterildiği gibi anahtar sözcüğü.  
  
 [!code-csharp[csProgGuideParameters#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)
- [Başvuru Türü Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
