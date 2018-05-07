---
title: Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
ms.openlocfilehash: b64968a89f010f3f904d3a281d346d2ddf999e2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-value-type-parameters-c-programming-guide"></a>Değer Türü Parametrelerini Geçirme (C# Programlama Kılavuzu)
A [değer türü](../../../csharp/language-reference/keywords/value-types.md) değişkenini içeren kendi verileri doğrudan olarak tersine bir [başvuru türü](../../../csharp/language-reference/keywords/reference-types.md) değişkeni verilerine bir başvuru içeriyor. Değer türü değişkeni için bir yöntem değere göre geçirme yöntemine değişkeni bir kopyasını ileterek anlamına gelir. Yöntemi içinde gerçekleşmesi değişiklikleri parametre bağımsız değişkeninde depolanan özgün veriler herhangi bir etkisi vardır. Çağrılan yöntemi parametresinin değerini değiştirmek istiyorsanız, başvuruya göre geçmesi gereken kullanarak [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü. De kullanabilirsiniz [içinde](../../../csharp/language-reference/keywords/out-parameter-modifier.md) değeri değiştirilmeyecektir güvence altına almak sırasında kopyalama önlemek için başvuruya göre bir değer parametresini geçirmek için anahtar sözcüğü. Kolaylık olması için aşağıdaki örneklerde `ref`.  
  
## <a name="passing-value-types-by-value"></a>Değere göre geçirme değer türleri  
 Aşağıdaki örnek, geçirme değer türü gösterir değeriyle parametreleri. Değişkeni `n` değeriyle yönteme geçirilen `SquareIt`. Yöntemi içinde gerçekleşmesi değişiklikleri herhangi bir etkisi değişkeni özgün değerine sahip.  
  
 [!code-csharp[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]  
  
 Değişkeni `n` değer türü değil. Değer verisini içeren `5`. Zaman `SquareIt` çağrılır, içeriğini `n` parametresine kopyalanır `x`, yönteminin içinde kare. İçinde `Main`, ancak değerini `n` çağrıldıktan sonra aynıdır `SquareIt` yöntemi olarak edildi önce. Yöntemi içinde gerçekleşir değişiklikler yalnızca yerel değişken etkiler `x`.  
  
## <a name="passing-value-types-by-reference"></a>Başvuruya göre geçirme değer türleri  
 Bağımsız değişken olarak geçirilen dışında aşağıdaki örnekte önceki örnekle aynıdır bir `ref` parametresi. Temel alınan bağımsız değişkeninin değeri `n`, ne zaman değiştirilir `x` yönteminde değiştirilir.  
  
 [!code-csharp[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]  
  
 Bu örnekte, bu değeri değil `n` , geçirilir; bunun yerine, bir başvuru `n` geçirilir. Parametre `x` değil bir [int](../../../csharp/language-reference/keywords/int.md); bir başvurusu olan bir `int`, bu durumda, bir başvuru `n`. Bu nedenle, `x` karesi alınmış yönteminin içinde gerçekte kare nedir `x` başvurduğu, `n`.  
  
## <a name="swapping-value-types"></a>Değer türleri değiştirme  
 Burada iki değişken yönteme geçirin ve içeriklerini yöntemi değiştirir takas yöntemi, bağımsız değişkenlerinin değerlerini değiştirmenin ortak bir örnektir. Swap yöntemi bağımsız değişkenleri başvuruya göre geçmesi gerekir. Aksi halde, yerel kopyalarını yönteminin içine parametreleri değiştirme ve arama yönteminde değişikliğe oluşur. Aşağıdaki örnek tamsayı değerleri değiştirir.  
  
 [!code-csharp[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]  
  
 Çağırdığınızda `SwapByRef` yöntemi, kullanım `ref` çağrısında aşağıdaki örnekte gösterildiği gibi anahtar sözcük.  
  
 [!code-csharp[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [Başvuru Türü Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)
