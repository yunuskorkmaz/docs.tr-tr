---
title: while (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 420b409689d877c3e1ac744e8d7a65500cf8f964
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="while-c-reference"></a>while (C# Başvurusu)
`while` Deyimi, bir deyim veya ifadeleri bir blok için belirtilen ifadeyi değerlendirir kadar yürütür `false`.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a>Örnek  
 Çünkü sınamasını `while` ifade başlamaz döngünün her yürütmeden önce bir `while` sıfır veya daha fazla kez döngü yürütür. Bu farklıdır [yapmak](../../../csharp/language-reference/keywords/do.md) bir veya birden çok kez yürütür döngü.  
  
 A `while` döngü bitmelidir ne zaman bir [sonu](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimi dışında denetimi aktarır döngü. Döngü çıkmadan sonraki yinelemeye denetim geçirmek için kullanmak [devam](../../../csharp/language-reference/keywords/continue.md) deyimi. Where bağlı olarak üç önceki örnek çıktıda fark `int n` artırılır. Çıktı aşağıdaki örnekte oluşturulur.  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [while deyimi (C++)](/cpp/cpp/while-statement-cpp)  
 [Yineleme deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
