---
title: while (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 23c5ca3bb7dc401a894a6c3918fbaec9a9306153
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [while Deyimi (C++)](/cpp/cpp/while-statement-cpp)  
 [Yineleme Deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
