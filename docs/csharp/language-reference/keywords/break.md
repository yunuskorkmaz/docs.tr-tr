---
title: break (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 0cfe722bfefc1befd8a453f4454b05b3e4a0da76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [switch](../../../csharp/language-reference/keywords/switch.md)  
 [Atlama Deyimleri](../../../csharp/language-reference/keywords/jump-statements.md)  
 [Yineleme Deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
