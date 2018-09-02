---
title: unchecked (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415782"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)
`unchecked` Anahtar sözcüğü, Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi gizlemek için kullanılır.  
  
 Bir ifade hedef türün aralığı dışında bir değer veriyorsa işaretlenmemiş bir bağlamda taşma işaretlenmemiştir. Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifade, bir tamsayı göz ardı edilir için sonuç çok büyük olduğunu ve `int1` -2,147,483,639 değeri atanır.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Varsa `unchecked` ortam kaldırılır, bir derleme hatası oluşur. İfadenin tüm koşulları sabitleri olduğundan overflow derleme zamanında algılanabilir.  
  
 Sabit olmayan terimleri içeren ifadeler, derleme zamanında varsayılan olarak işaretli ve çalışma zamanı. Bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) denetlenmiş bir ortamda etkinleştirme hakkında bilgi için.  
  
 Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi olduğundan, tehlike olduğu taşma performansı iyileştirebilir. Ancak, denetlenmiş bir ortamda taşma olasılığı varsa kullanılmalıdır.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını gösterir `unchecked` anahtar sözcüğü.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [İşaretli ve İşaretsiz](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [checked](../../../csharp/language-reference/keywords/checked.md)
