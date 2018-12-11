---
title: -Başvuru türü parametreleri geçirme C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
ms.openlocfilehash: faf9222d7850b9859f4bc61eb2a0bbe8f4b5bbc1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243640"
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a>Başvuru Türü Parametreleri Geçirme (C# Programlama Kılavuzu)
Bir değişken bir [başvuru türüne](../../../csharp/language-reference/keywords/reference-types.md) verilerini içermiyor doğrudan; verilerine bir başvuru içeriyor. Değere göre bir başvuru türü parametresi geçirdiğinizde, bir sınıf üyesinin değerini gibi başvurulan nesnenin ait verileri değiştirmek mümkündür. Ancak, başvuru değeri değiştiremezsiniz; Örneğin, aynı başvuru için yeni bir sınıf bellek ayırmak ve sahip yöntemi dışında kalıcı hale getirmek için kullanamazsınız. Parametresini kullanarak bunu yapmak için geçirmek [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) anahtar sözcüğü. Kolaylık olması için aşağıdaki örneklerde `ref`.  
  
## <a name="passing-reference-types-by-value"></a>Değere göre geçirme başvuru türleri  
 Aşağıdaki örnek, bir başvuru türü parametre geçirerek gösterir `arr`, bir yönteme değeriyle `Change`. Parametresi bir başvuru olduğundan `arr`, dizi öğelerinin değerlerini değiştirmek mümkündür. Ancak, parametre yalnızca farklı bir bellek konumuna yeniden denemesi yöntem içinde çalışır ve özgün değişken etkilemez `arr`.  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 Yukarıdaki örnekte, dizinin `arr`, bir başvuru türü olduğu yöntemine geçirilir `ref` parametresi. Böyle bir durumda kopyasını başvurunun işaret ettiği için `arr`, yönteme iletilir. Bu durumda olan bir dizi öğe içeriklerinin Değiştir yönteminin mümkündür çıktı gösterir `1` için `888`. Ancak, kullanarak yeni bir bölümü bellek ayırma [yeni](../../../csharp/language-reference/keywords/new.md) işleci içinde `Change` değişkeni hale getirdiğini `pArray` yeni bir dizi başvuru. Bu nedenle, orijinal diziyi etkilemez sonra değişiklikleri `arr`, içinde oluşturulan `Main`. Bu örnekte, biri içinde iki diziler aslında, oluşturulan `Main` ve bir iç `Change` yöntemi.  
  
## <a name="passing-reference-types-by-reference"></a>Başvuruya göre geçirme başvuru türleri  
 Aşağıdaki örnek dışında önceki örnekle aynıdır `ref` anahtar sözcüğü çağrısı ve yöntem üst bilgisi eklenir. Yönteminde gerçekleşecek herhangi bir değişiklik, çağıran program özgün değişkeninde etkiler.  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 Yöntem içinde gerçekleşen tüm değişiklikler özgün dizide etkileyen `Main`. Özgün dizinin kullanarak aslında, bırakılan `new` işleci. Bu nedenle, arama sonra `Change` herhangi yöntemi başvurusu `arr` oluşturulur beş öğeli dizinin işaret `Change` yöntemi.  
  
## <a name="swapping-two-strings"></a>İki dizeyi değiştirme  
 Dizeleri değiştirme, başvuruya göre başvuru türü parametreleri geçirme, iyi bir örnektir. Örnekte, iki dizeyi `str1` ve `str2`, içinde başlatılan `Main` geçirilir `SwapStrings` yöntemi değiştiren parametreleri olarak `ref` anahtar sözcüğü. İki dizenin içine ve yöntemi içinde takas `Main` de.  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 Bu örnekte, çağıran program değişkenlerinde etkilemek için başvuruya göre geçirilen parametreler gerekir. Kaldırırsanız `ref` yöntem üst bilgisi ve yöntem çağrısının anahtar sözcüğü, hiçbir değişiklik çağıran program yerinde götürür.  
  
 Dizeleri hakkında daha fazla bilgi için bkz. [dize](../../../csharp/language-reference/keywords/string.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Parametreleri Geçirme](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
- [ref](../../../csharp/language-reference/keywords/ref.md)  
- [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
- [out](../../../csharp/language-reference/keywords/out.md)  
- [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)
