---
title: Başvuru türü parametreleri geçirme-C# Programlama Kılavuzu
description: C# ' de bir başvuru türü parametresini bir değer ile geçirdiğinizde, başvurulan nesnedeki veriler, başvurunun kendisi için değer olarak değişebilir.
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: 315c1193de12a8fb5c066e023bb98bc228ce85bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91154125"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)

Bir [başvuru türü](../../language-reference/keywords/reference-types.md) değişkeni, verilerini doğrudan içermez; Bu, verilerine bir başvuru içerir. Bir başvuru türü parametresini değere göre geçirdiğinizde, bir sınıf üyesinin değeri gibi başvurulan nesneye ait verileri değiştirmek mümkündür. Bununla birlikte, başvurunun kendisi için değerini değiştiremezsiniz; Örneğin, yeni bir nesne için bellek ayırmak ve yöntemin dışında kalmasını sağlamak için aynı başvuruyu kullanamazsınız. Bunu yapmak için [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğünü kullanarak parametreyi geçirin. Basitlik için aşağıdaki örneklerde kullanılması gerekir `ref` .  
  
## <a name="passing-reference-types-by-value"></a>Başvuru türlerini değere göre geçirme  

 Aşağıdaki örnek, bir başvuru türü parametresinin, `arr` değere göre bir yöntemine geçirilmesini gösterir `Change` . Parametresi öğesine bir başvuru olduğundan `arr` , dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametreyi farklı bir bellek konumuna yeniden atama girişimi yalnızca yöntemin içinde çalışır ve özgün değişkenini etkilemez `arr` .  
  
 [!code-csharp[csProgGuideParameters#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#7)]  
  
 Önceki örnekte, `arr` bir başvuru türü olan array parametresi olmadan yöntemine geçirilir `ref` . Böyle bir durumda, başvurusunun öğesine işaret eden bir kopyası `arr` yöntemine geçirilir. Çıktı, yönteminin bu durumda ' den ' a bir dizi öğesinin içeriğini değiştirme olasılığı olduğunu gösterir `1` `888` . Ancak, yöntemin içindeki [New](../../language-reference/operators/new-operator.md) işlecini kullanarak belleğin yeni bir bölümünü ayırmak, `Change` değişken `pArray` başvurusunu yeni bir dizi olarak yapar. Bu nedenle, bundan sonra yapılan tüm değişiklikler içinde oluşturulan orijinal diziyi etkilemez `arr` `Main` . Aslında, bu örnekte, bir diğeri içinde ve bir içinde iki dizi oluşturulur `Main` `Change` .  
  
## <a name="passing-reference-types-by-reference"></a>Başvuru türlerini başvuruya göre geçirme  

 Aşağıdaki örnek, `ref` anahtar sözcüğünün Yöntem üstbilgisine eklenmesi ve çağrmasının dışında, önceki örnekle aynıdır. Yönteminde gerçekleşen tüm değişiklikler, çağıran programdaki özgün değişkeni etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#8)]  
  
 Yöntemi içinde gerçekleşen tüm değişiklikler içindeki orijinal diziyi etkiler `Main` . Aslında, özgün dizi işleci kullanılarak yeniden ayrılır `new` . Bu nedenle, yöntemini çağırdıktan sonra, `Change` `arr` yöntemi içinde oluşturulan beş öğeli diziyi işaret eden herhangi bir başvuru `Change` .  
  
## <a name="swapping-two-strings"></a>Iki dizeyi değiştirme  

 Dizeleri değiştirme, başvuru türü parametrelerini başvuruya göre geçirmek için iyi bir örnektir. Örnekte, ve şeklinde iki dize ' `str1` `str2` de başlatılır `Main` ve `SwapStrings` anahtar sözcüğü tarafından değiştirilen parametreler olarak yöntemine geçirilir `ref` . İki dize, yönteminin içinde ve içinde bulunur `Main` .  
  
 [!code-csharp[csProgGuideParameters#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#9)]  
  
 Bu örnekte, çağıran programdaki değişkenleri etkilemek için parametrelerin başvuruya göre geçirilmesi gerekir. `ref`Anahtar sözcüğünü hem Yöntem başlığından hem de yöntem çağrısından kaldırırsanız, çağıran programda hiçbir değişiklik gerçekleşmeyecektir.  
  
 Dizeler hakkında daha fazla bilgi için bkz. [String](../../language-reference/builtin-types/reference-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Parametreleri geçirme](./passing-parameters.md)
- [ref](../../language-reference/keywords/ref.md)
- ['ndaki](../../language-reference/keywords/in-parameter-modifier.md)
- [dışı](../../language-reference/keywords/out.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
