---
description: if-else-C# başvurusu
title: if-else-C# başvurusu
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
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118513"
---
# <a name="if-else-c-reference"></a>if-else (C# Başvurusu)

Bir `if` deyimi, bir Boolean ifadesinin değerine göre hangi deyimin çalıştırılacağını tanımlar. Aşağıdaki örnekte, `bool` değişkeni `condition` olarak ayarlanır `true` ve sonra `if` deyimden işaretlenir. Çıktı `The variable is set to true.` olur.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Bu konudaki örnekleri `Main` bir konsol uygulaması yöntemine yerleştirerek çalıştırabilirsiniz.

`if`Aşağıdaki örnekte gösterildiği gibi C# içindeki bir ifade iki form alabilir.

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

Bir `if-else` bildiriminde, `condition` true olarak değerlendirilirse `then-statement` çalışır. `condition`Yanlışsa, `else-statement` çalışır. `condition`Aynı anda doğru ve yanlış olamayacağı için, `then-statement` `else-statement` bir `if-else` deyimin her ikisi de her ikisini de çalıştırmazlar. `then-statement`Veya `else-statement` çalıştırıldıktan sonra Denetim, deyimden sonra sonraki ifadeye aktarılır `if` .

`if`Eğer true ise, bir ifadesini içermeyen bir bildirimde, `else` `condition` `then-statement` çalışır. `condition`False ise, denetim deyimden sonra Next ifadesine aktarılır `if` .

Hem hem de, `then-statement` `else-statement` küme ayracı () içine alınmış tek bir ifadeden veya birden çok deyimden oluşabilir `{}` . Tek bir ifadede, küme ayraçları isteğe bağlıdır ancak önerilir.

Ve içindeki deyim veya deyimler, `then-statement` `else-statement` özgün deyimin içindeki başka bir deyim dahil olmak üzere herhangi bir türde olabilir `if` `if` . İç içe geçmiş `if` ifadelerde her `else` bir yan tümce karşılık gelen en son öğesine aittir `if` `else` . Aşağıdaki örnekte, `Result1` her ikisi de `m > 10` `n > 20` true olarak değerlendirilir. `m > 10`True ise, ancak `n > 20` false ise `Result2` görünür.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Bunun yerine, `Result2` false olduğunda görünmesini istiyorsanız, `(m > 10)` `if` Aşağıdaki örnekte gösterildiği gibi, iç içe geçmiş deyimin başlangıcını ve bitişini oluşturmak için, ayraçları kullanarak bu ilişkilendirmeyi belirtebilirsiniz.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` koşul `(m > 10)` false olarak değerlendirilirse görüntülenir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, klavyeden bir karakter girersiniz ve program, `if` giriş karakterinin alfabetik bir karakter olup olmadığını anlamak için iç içe geçmiş bir ifade kullanır. Giriş karakteri alfabetik bir karakter ise, program giriş karakterinin küçük harf veya büyük harf olup olmadığını denetler. Her durumda bir ileti görüntülenir.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Örnek

Ayrıca `if` , aşağıdaki kısmi kodun gösterdiği gibi, bir ifadeyi Else bloğunun içine iç içe geçirebilirsiniz. Örnek, `if` iki diğer blok içindeki deyimlerini bir ve sonra blok içinde ifade etti. Açıklamalar, her blokta hangi koşulların doğru veya yanlış olduğunu belirtir.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir giriş karakterinin küçük harf, büyük harf veya sayı olduğunu belirler. Üç koşulun üçü de yanlışsa, karakter alfasayısal bir karakter değildir. Örnek, her durum için bir ileti görüntüler.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Else bloğunda bir deyim olarak veya then bloğu geçerli bir deyim olabilir, koşul için herhangi bir geçerli Boole ifadesi kullanabilirsiniz. [logical operators](../operators/boolean-logical-operators.md) `!` `&&` `||` `&` `|` `^` Bileşik koşullar oluşturmak için,,,, ve gibi mantıksal işleçleri kullanabilirsiniz. Aşağıdaki kod örnekleri gösterir.

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

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [?: İşleci](../operators/conditional-operator.md)
- [if-else Deyimi (C++)](/cpp/cpp/if-else-statement-cpp)
- [değiştirebilirsiniz](switch.md)
