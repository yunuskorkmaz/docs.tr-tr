---
title: if-else (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: eb8fe4c3a02cab8f8c887ec37244bede04b8a663
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218761"
---
# <a name="if-else-c-reference"></a>if-else (C# Başvurusu)
Bir `if` deyimi tanımlayan çalıştırmak için hangi deyimi değeri temel alınarak bir `Boolean` ifade. Aşağıdaki örnekte, `Boolean` değişkeni `result` ayarlanır `true` ve ardından iade `if` deyimi. Çıktı `The condition is true`.  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 Bunları yerleştirerek bu konudaki örnekler çalıştırabilirsiniz `Main` bir konsol uygulaması yöntemi.  
  
 Bir `if` C# deyimi, aşağıdaki örnekte gösterildiği gibi iki form alabilir.  
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.  
  
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
 İçinde bir `if-else` deyimi, varsa `condition` doğru olarak değerlendirir `then-statement` çalıştırır. Varsa `condition` false, `else-statement` çalıştırır. Çünkü `condition` aynı anda true ve false olamaz `then-statement` ve `else-statement` , bir `if-else` deyimi hiçbir zaman hem de çalıştırabilirsiniz. Sonra `then-statement` veya `else-statement` çalıştığında, Denetim sonra next deyimi için aktarılır `if` deyimi.  
  
 İçinde bir `if` içermeyen deyimi bir `else` deyimi, varsa `condition` doğrudur `then-statement` çalıştırır. Varsa `condition` denetim sonra next deyimi için aktarılır yanlış `if` deyimi.  
  
 Hem `then-statement` ve `else-statement` tek bir deyimde veya ayraç içine birden çok deyime oluşabilir (`{}`). Tek bir deyimde için Küme ayraçları isteğe bağlıdır ancak önerilir.  
  
 Deyimin veya deyimlerinde `then-statement` ve `else-statement` başka dahil olmak üzere her türlü olabilir `if` deyimi, özgün içinde iç içe geçmiş `if` deyimi. İçinde iç içe geçmiş `if` deyimleri, her `else` yan tümcesi ait son `if` karşılık gelen yok `else`. Aşağıdaki örnekte, `Result1` her iki görünür `m > 10` ve `n > 20` true olarak değerlendirin. Varsa `m > 10` geçerlidir, ancak `n > 20` false, `Result2` görüntülenir.  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Bunun yerine, isterseniz, `Result2` ne zaman görünmesi `(m > 10)` başlangıcı ve sonu iç içe oluşturmak için Küme ayraçları kullanarak bu ilişkiyi belirtebilirsiniz yanlış `if` deyimi, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2` görünür koşul `(m > 10)` yanlış olarak değerlendirilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, klavyeden bir karakter girin ve programı bir iç içe kullanır `if` giriş karakter alfasayısal bir karakter olup olmadığını belirlemek için deyimi. Giriş karakter alfasayısal bir karakter ise, program giriş karakteri küçük harfler veya büyük olup olmadığını denetler. Her örneği için bir ileti görüntülenir.  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a>Örnek  
 Ayrıca geçirebilmenize bir `if` başka bir blok ifadeye aşağıdaki gösterildiği gibi kısmi kodu. Örnek Yuvalar `if` ifadeleri iki başka blokları ve sonra bloğu içinde. True veya false her bloğundaki hangi koşullar açıklamaları belirtin.  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir giriş karakteri küçük harf, büyük harf veya sayı olup olmadığını belirler. Tüm üç koşul yanlış ise, karakter alfasayısal bir karakter değil. Örneğin, her örneği için bir ileti görüntüler.  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 Herhangi bir geçerli ifadesi başka blok veya sonra blok deyiminde yalnızca olabildiği kadar koşul için geçerli bir Boolean ifadesini kullanabilirsiniz. Mantıksal işleçler gibi kullanabilir [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), [ &#124; ](../../../csharp/language-reference/operators/or-operator.md) ve [!](../../../csharp/language-reference/operators/logical-negation-operator.md) Bileşik koşullar yapma. Aşağıdaki kod örnekleri gösterir.  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// Short-circuit AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// Short-circuit OR  
if (m > n || m > p)  
{  
    Console.WriteLine("m isn't the smallest.");  
}  
  
// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// m isn't the smallest.  
// Now m is the smallest.  
```  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [?: İşleci](../../../csharp/language-reference/operators/conditional-operator.md)  
 [if-else Deyimi (C++)](/cpp/cpp/if-else-statement-cpp)  
 [switch](../../../csharp/language-reference/keywords/switch.md)
