---
title: "unchecked (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c05e7cb742d8e8f5a7804656a5ec13548d0498b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Checked ve Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [işaretli](../../../csharp/language-reference/keywords/checked.md)
