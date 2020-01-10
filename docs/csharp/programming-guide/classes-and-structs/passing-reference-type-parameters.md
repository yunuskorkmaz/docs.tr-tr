---
title: Başvuru türü parametreleri geçirme- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 6fa0e60fafabaa9fb04cdc5d5bf3f9e29490e84f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714715"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)
Bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni, verilerini doğrudan içermez; Bu, verilerine bir başvuru içerir. Bir başvuru türü parametresini değere göre geçirdiğinizde, bir sınıf üyesinin değeri gibi başvurulan nesneye ait verileri değiştirmek mümkündür. Bununla birlikte, başvurunun kendisi için değerini değiştiremezsiniz; Örneğin, yeni bir nesne için bellek ayırmak ve yöntemin dışında kalmasını sağlamak için aynı başvuruyu kullanamazsınız. Bunu yapmak için [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak parametreyi geçirin. Basitlik için aşağıdaki örneklerde `ref`kullanılır.  
  
## <a name="passing-reference-types-by-value"></a>Başvuru türlerini değere göre geçirme  
 Aşağıdaki örnek, bir başvuru türü parametre `arr`, değere göre `Change`bir yönteme geçirmeyi gösterir. Parametresi `arr`bir başvuru olduğundan, dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametreyi farklı bir bellek konumuna yeniden atama girişimi yalnızca yöntemi içinde çalışır ve `arr`özgün değişkenini etkilemez.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 Önceki örnekte, bir başvuru türü olan `arr`dizisi, `ref` parametresi olmadan yöntemine geçirilir. Böyle bir durumda, başvuruya işaret eden `arr`bir kopyası yöntemine geçirilir. Çıktı, yönteminin bir dizi öğesinin içeriğini değiştirmek için `1`, bu durumda `888`. Ancak, `Change` yöntemi içindeki [New](../../language-reference/operators/new-operator.md) işlecini kullanarak belleğin yeni bir bölümünü ayırmak, değişkenin `pArray` yeni bir diziye başvurmasına neden olur. Bu nedenle, bundan sonra yapılan tüm değişiklikler, `Main`içinde oluşturulan `arr`orijinal diziyi etkilemez. Aslında, bu örnekte, biri `Main` içinde diğeri `Change` yöntemi içinde iki dizi oluşturulur.  
  
## <a name="passing-reference-types-by-reference"></a>Başvuru türlerini başvuruya göre geçirme  
 Aşağıdaki örnek, `ref` anahtar sözcüğünün Yöntem başlığına ve çağrısına eklenmesinin dışında, önceki örnekle aynıdır. Yönteminde gerçekleşen tüm değişiklikler, çağıran programdaki özgün değişkeni etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Yöntemi içinde gerçekleşen tüm değişiklikler `Main`orijinal diziyi etkiler. Aslında, özgün dizi `new` işleci kullanılarak yeniden ayrılır. Bu nedenle, `Change` yöntemini çağırdıktan sonra, `arr` için herhangi bir başvuru `Change` yönteminde oluşturulan beş öğeli diziyi işaret eder.  
  
## <a name="swapping-two-strings"></a>Iki dizeyi değiştirme  
 Dizeleri değiştirme, başvuru türü parametrelerini başvuruya göre geçirmek için iyi bir örnektir. Örnekte, `str1` ve `str2`iki dize `Main` başlatılır ve `ref` anahtar sözcüğüyle değiştirilen parametreler olarak `SwapStrings` yöntemine geçirilir. İki dize, yönteminin içinde ve `Main` içinde yer değiştirir.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 Bu örnekte, çağıran programdaki değişkenleri etkilemek için parametrelerin başvuruya göre geçirilmesi gerekir. Hem Yöntem başlığından hem de yöntem çağrısından `ref` anahtar sözcüğünü kaldırırsanız, çağıran programda hiçbir değişiklik gerçekleşmeyecektir.  
  
 Dizeler hakkında daha fazla bilgi için bkz. [String](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Başvuru Türleri](../../language-reference/keywords/reference-types.md)
