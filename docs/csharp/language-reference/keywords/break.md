---
title: "break (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a>break (C# Başvurusu)
`break` Açıklamayı sonlandıran en yakın kapsayan bir döngü veya [geçiş](../../../csharp/language-reference/keywords/switch.md) göründüğü deyimi. Denetim sonlandırılan deyimi aşağıdaki deyim varsa geçirilir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, koşullu ifade 1'den 100'e saymak için beklenen sayaç içerir; Ancak, `break` açıklamayı sonlandıran döngü sonra 4 sayar.  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `break` deyimi dışında bir iç iç içe geçmiş döngüsünü kesmek ve denetim için dış döngü döndürmek için kullanılır.  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek kullanımını gösteren `break` içinde bir [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimi.  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 Girerseniz `4`, çıktı aşağıdaki gibi olur:  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [geçiş](../../../csharp/language-reference/keywords/switch.md)  
 [Atlama deyimleri](../../../csharp/language-reference/keywords/jump-statements.md)  
 [Yineleme deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
