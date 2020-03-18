---
title: Referans Türü Parametreleri Geçme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6fa0e60fafabaa9fb04cdc5d5bf3f9e29490e84f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714715"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)
Bir başvuru [türünden](../../language-reference/keywords/reference-types.md) bir değişken verilerini doğrudan içermez; verilerine bir başvuru içerir. Bir başvuru türü parametresini değere göre geçtiğiniz zaman, bir sınıf üyesinin değeri gibi başvurulan nesneye ait verileri değiştirmek mümkündür. Ancak, başvurunun değerini değiştiremezsiniz; örneğin, belleği yeni bir nesne için ayırmak ve yöntemin dışında devam etmesini sağlamak için aynı başvuruyu kullanamazsınız. Bunu yapmak için, [ref'i](../../language-reference/keywords/ref.md) kullanarak parametreyi geçirin veya anahtar [kelimeyi atın.](../../language-reference/keywords/out-parameter-modifier.md) Basitlik için aşağıdaki örnekler `ref`kullanılır.  
  
## <a name="passing-reference-types-by-value"></a>Referans Türlerini Değere Göre Geçirme  
 Aşağıdaki örnek, bir referans türü parametre, `arr`değer, bir yönteme geçen `Change`gösterir. Parametre bir başvuru `arr`olduğundan, dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametreyi farklı bir bellek konumuna yeniden atama girişimi yalnızca yöntemin içinde `arr`çalışır ve özgün değişkeni etkilemez.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 Önceki örnekte, `arr`bir başvuru türü olan dizi, `ref` parametre olmadan yönteme geçirilir. Böyle bir durumda, başvurunun bir kopyası, `arr`hangi işaret , yönteme geçirilir. Çıktı, yöntemin bir dizi öğesinin içeriğini değiştirmesinin mümkün olduğunu gösterir, bu durumda `1` `888`. Ancak, `Change` yöntem içinde [yeni](../../language-reference/operators/new-operator.md) işleci kullanarak bellek yeni bir `pArray` bölümünü ayırmak değişken başvuru yeni bir dizi yapar. Böylece, bundan sonraki herhangi bir değişiklik `arr`içinde oluşturulan orijinal `Main`dizi, etkilemez. Aslında, bu örnekte biri içinde, `Main` diğeri yöntemin `Change` içinde olmak üzere iki dizi oluşturulur.  
  
## <a name="passing-reference-types-by-reference"></a>Referans Türlerini Başvuruya Göre Geçirme  
 Aşağıdaki örnek, anahtar kelimenin `ref` yöntem üstbilgisine ve aramaya eklenmesi dışında, önceki örnekle aynıdır. Yöntemde gerçekleşen değişiklikler, arama programındaki özgün değişkeni etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Yöntem içinde gerçekleşen tüm değişiklikler' deki özgün `Main`diziyi etkiler. Aslında, özgün dizi `new` işleç kullanılarak yeniden tahsis edilir. Böylece, `Change` yöntemi aradıktan sonra, `arr` `Change` yöntemde oluşturulan beş öğeli dizi, noktalara herhangi bir başvuru.  
  
## <a name="swapping-two-strings"></a>İki Dize Değiştirme  
 Dizeleri değiştirme başvuru türü parametreleri başvuru ile geçen iyi bir örnektir. Örnekte, iki dizeleri `str1` `str2`ve , `Main` başharfve anahtar `SwapStrings` kelime tarafından `ref` değiştirilen parametreler olarak yönteme geçirilir. İki dize yöntem içinde ve içinde `Main` de takas edilir.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 Bu örnekte, arama programındaki değişkenleri etkilemek için parametrelerin referans la geçirilmesi gerekir. Anahtar kelimeyi `ref` hem yöntem üstbilgisinden hem de yöntem çağrısından kaldırırsanız, arama programında hiçbir değişiklik yapılmaz.  
  
 Dizeleri hakkında daha fazla bilgi için [string'e](../../language-reference/builtin-types/reference-types.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [Referans](../../language-reference/keywords/ref.md)
- [Inç](../../language-reference/keywords/in-parameter-modifier.md)
- [çıkış](../../language-reference/keywords/out.md)
- [Referans Türleri](../../language-reference/keywords/reference-types.md)
