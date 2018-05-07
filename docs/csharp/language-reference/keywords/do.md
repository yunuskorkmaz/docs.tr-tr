---
title: do (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 5599f079e29fd094c4d6a6a75afba89fb562a166
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="do-c-reference"></a>do (C# Başvurusu)
`do` Deyimini yürütür bir deyim veya deyimleri bloğu art arda için belirtilen ifadeyi değerlendirir kadar `false`. Döngünün gövdesi kaşlı ayraç içinde alınmalıdır `{}`sürece tek bir deyimde oluşur. Bu durumda, küme ayraçları isteğe bağlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `do-while` döngü deyimlerini yürütmek değişkeni sürece `x` değerinden 5'tir.  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 Farklı [sırada](../../../csharp/language-reference/keywords/while.md) deyimi, bir `do-while` döngü koşullu ifade değerlendirilir önce bir kez gerçekleştirilir.  
  
 Bir oranda noktası `do-while` bloğu, döngü kullanarak dışında bölün [sonu](../../../csharp/language-reference/keywords/break.md) deyimi. Doğrudan adım `while` ifade değerlendirme deyimi kullanarak [devam](../../../csharp/language-reference/keywords/continue.md) deyimi. Varsa `while` ifade true olarak değerlendirilir, yürütme Döngüdeki ilk ifade adresindeki devam eder. Yanlış olarak değerlendirilir, ilk ifadeden sonra yürütülmeye `do-while` döngü.  
  
 A `do-while` döngü ayrıca çıkıldı tarafından [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), veya [throw](../../../csharp/language-reference/keywords/throw.md) deyimleri.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [do-while Deyimi (C++)](/cpp/cpp/do-while-statement-cpp)  
 [Yineleme Deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)
