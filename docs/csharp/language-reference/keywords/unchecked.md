---
title: unchecked (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: d7a48950b7158be3cd589c20fbfe0661f3c9c5af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267986"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)
`unchecked` Anahtar sözcüğü taşma denetimi integral türü aritmetik işlemler ve dönüştürmeleri için gizlemek için kullanılır.  
  
 Bir ifade hedef türü aralık dışında bir değer oluşturursa denetlenmeyen bir bağlamda taşma işaretlenmemiştir. Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifadesi, bir tamsayı göz ardı için sonucu çok büyük olduğunu olgu ve `int1` -2,147,483,639 değeri atanır.  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 Varsa `unchecked` ortamı kaldırılır, derleme hatası oluşur. İfadenin tüm koşulları sabitleri olduğundan taşma derleme zamanında algılanabilir.  
  
 Sabit olmayan terimleri içeren ifadeleri derleme zamanında varsayılan olarak işaretli ve çalışma zamanı. Bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) işaretli bir ortamda etkinleştirme hakkında bilgi için.  
  
 Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi için söz konusu olduğunda, tehlike taşma performansı iyileştirebilir. Taşma olasılığı varsa, ancak, denetlenen bir ortamda kullanılması gerekir.  
  
## <a name="example"></a>Örnek  
 Bu örnek nasıl kullanılacağını göstermektedir `unchecked` anahtar sözcüğü.  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [İşaretli ve İşaretsiz](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [checked](../../../csharp/language-reference/keywords/checked.md)
