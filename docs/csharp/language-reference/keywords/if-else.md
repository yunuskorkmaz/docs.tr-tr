---
title: if-else- C# Reference
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
ms.openlocfilehash: 98c1a8dceec3e5a47627841988e2d722c56fc36c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715258"
---
# <a name="if-else-c-reference"></a>if-else (C# Başvurusu)

Bir `if` deyimi, bir Boolean ifadesinin değerine göre hangi deyimin çalıştırılacağını tanımlar. Aşağıdaki örnekte, `condition` `bool` değişkeni `true` olarak ayarlanır ve sonra `if` bildiriminde denetlenir. Çıktı `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Bu konudaki örnekleri, bir konsol uygulamasının `Main` metoduna yerleştirerek çalıştırabilirsiniz.

Aşağıdaki örnekte gösterildiği gibi C# , içindeki bir `if` deyimleri iki form alabilir.

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

Bir `if-else` bildiriminde, `condition` true olarak değerlendirilirse `then-statement` çalışır. `condition` false ise, `else-statement` çalışır. `condition` aynı anda doğru ve yanlış olamayacağı için, bir `if-else` deyimin `then-statement` ve `else-statement` her ikisi de çalışmaz. `then-statement` veya `else-statement` çalıştıktan sonra Denetim, `if` deyimden sonra sonraki deyime aktarılır.

`else` bir ifade içermeyen `if` bildiriminde, `condition` true ise `then-statement` çalışır. `condition` false ise, denetim `if` deyimden sonra sonraki ifadeye aktarılır.

Hem `then-statement` hem de `else-statement`, küme ayracı (`{}`) içine alınmış tek bir ifadeden veya birden çok deyimden oluşabilir. Tek bir ifadede, küme ayraçları isteğe bağlıdır ancak önerilir.

`then-statement` ve `else-statement` ifadesi veya deyimleri, özgün `if` deyimi içinde iç içe geçmiş başka bir `if` deyimi de dahil olmak üzere herhangi bir türde olabilir. İç içe `if` deyimlerde, her bir `else` yan tümcesi karşılık gelen bir `else`sahip olmayan son `if` aittir. Aşağıdaki örnekte, hem `m > 10` hem de `n > 20` doğru olarak değerlendirilüyorsa `Result1` görünür. `m > 10` true ise, ancak `n > 20` false ise `Result2` görüntülenir.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Bunun yerine, `(m > 10)` false olduğunda `Result2` görünmesini istiyorsanız, aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş `if` deyimin başlangıcını ve sonunu oluşturmak için ayraçları kullanarak bu ilişkilendirmeyi belirtebilirsiniz.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

koşul `(m > 10)` false olarak değerlendirilirse `Result2` görüntülenir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, klavyeden bir karakter girersiniz ve program, giriş karakterinin alfabetik bir karakter olup olmadığını anlamak için iç içe geçmiş `if` beyanını kullanır. Giriş karakteri alfabetik bir karakter ise, program giriş karakterinin küçük harf veya büyük harf olup olmadığını denetler. Her durumda bir ileti görüntülenir.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Örnek

Ayrıca, aşağıdaki kısmi kodun gösterdiği gibi, bir `if` ifadesini Else bloğunun içine yerleştirebilirsiniz. Örnek, iki başka blok içindeki deyimler `if` ve bir blok. Açıklamalar, her blokta hangi koşulların doğru veya yanlış olduğunu belirtir.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir giriş karakterinin küçük harf, büyük harf veya sayı olduğunu belirler. Üç koşulun üçü de yanlışsa, karakter alfasayısal bir karakter değildir. Örnek, her durum için bir ileti görüntüler.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Else bloğunda bir deyim olarak veya then bloğu geçerli bir deyim olabilir, koşul için herhangi bir geçerli Boole ifadesi kullanabilirsiniz. Bileşik koşullar oluşturmak için `!`, `&&`, `||`, `&`, `|`ve `^` gibi [mantıksal işleçleri](../operators/boolean-logical-operators.md) kullanabilirsiniz. Aşağıdaki kod örnekleri gösterir.

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

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [?: İşleci](../operators/conditional-operator.md)
- [if-else Deyimi (C++)](/cpp/cpp/if-else-statement-cpp)
- [switch](switch.md)
