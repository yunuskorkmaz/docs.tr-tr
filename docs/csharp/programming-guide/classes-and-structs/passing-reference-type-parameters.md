---
title: Başvuru türü parametreleri geçirme- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: f4329c525995b8246427072d1f537d91d875ef95
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596269"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)
Bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni, verilerini doğrudan içermez; Bu, verilerine bir başvuru içerir. Bir başvuru türü parametresini değere göre geçirdiğinizde, bir sınıf üyesinin değeri gibi başvurulan nesneye ait verileri değiştirmek mümkündür. Bununla birlikte, başvurunun kendisi için değerini değiştiremezsiniz; Örneğin, yeni bir nesne için bellek ayırmak ve yöntemin dışında kalmasını sağlamak için aynı başvuruyu kullanamazsınız. Bunu yapmak için [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak parametreyi geçirin. Basitlik için aşağıdaki örneklerde kullanılması `ref`gerekir.  
  
## <a name="passing-reference-types-by-value"></a>Başvuru türlerini değere göre geçirme  
 Aşağıdaki örnek, bir başvuru türü parametresinin, `arr`değere göre bir `Change`yöntemine geçirilmesini gösterir. Parametresi öğesine `arr`bir başvuru olduğundan, dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametreyi farklı bir bellek konumuna yeniden atama girişimi yalnızca yöntemin içinde çalışır ve özgün değişkenini `arr`etkilemez.  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 Önceki örnekte, bir başvuru türü olan array `arr` `ref` parametresi olmadan yöntemine geçirilir. Böyle bir durumda, başvurusunun öğesine `arr`işaret eden bir kopyası yöntemine geçirilir. Çıktı, yönteminin bu durumda ' den `1` `888`' a bir dizi öğesinin içeriğini değiştirme olasılığı olduğunu gösterir. Ancak, `Change` yöntemin içindeki [New](../../language-reference/operators/new-operator.md) işlecini kullanarak belleğin yeni bir bölümünü ayırmak, değişken `pArray` başvurusunu yeni bir dizi olarak yapar. Bu nedenle, bundan sonra yapılan tüm değişiklikler içinde `arr` `Main`oluşturulan orijinal diziyi etkilemez. Aslında, bu örnekte, bir diğeri `Main` içinde ve bir `Change` içinde iki dizi oluşturulur.  
  
## <a name="passing-reference-types-by-reference"></a>Başvuru türlerini başvuruya göre geçirme  
 Aşağıdaki örnek, `ref` anahtar sözcüğünün Yöntem üstbilgisine eklenmesi ve çağrmasının dışında, önceki örnekle aynıdır. Yönteminde gerçekleşen tüm değişiklikler, çağıran programdaki özgün değişkeni etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Yöntemi içinde gerçekleşen tüm değişiklikler içindeki `Main`orijinal diziyi etkiler. Aslında, özgün dizi `new` işleci kullanılarak yeniden ayrılır. Bu nedenle, `Change` yöntemini çağırdıktan sonra, `arr` yöntemiiçindeoluşturulanbeşöğelidiziyiişaretedenherhangibirbaşvuru.`Change`  
  
## <a name="swapping-two-strings"></a>Iki dizeyi değiştirme  
 Dizeleri değiştirme, başvuru türü parametrelerini başvuruya göre geçirmek için iyi bir örnektir. Örnekte, `str1` ve `str2` şeklindeiki`Main` dize ' de başlatılır ve `ref` anahtar sözcüğü tarafından değiştirilen parametreler olarak yönteminegeçirilir.`SwapStrings` İki dize, yönteminin içinde ve içinde `Main` bulunur.  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 Bu örnekte, çağıran programdaki değişkenleri etkilemek için parametrelerin başvuruya göre geçirilmesi gerekir. `ref` Anahtar sözcüğünü hem Yöntem başlığından hem de yöntem çağrısından kaldırırsanız, çağıran programda hiçbir değişiklik gerçekleşmeyecektir.  
  
 Dizeler hakkında daha fazla bilgi için bkz. [String](../../language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri Geçirme](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- [in](../../language-reference/keywords/in-parameter-modifier.md)
- [out](../../language-reference/keywords/out.md)
- [Başvuru Türleri](../../language-reference/keywords/reference-types.md)
