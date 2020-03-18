---
title: if-else - C# Referans
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715258"
---
# <a name="if-else-c-reference"></a>if-else (C# Başvurusu)

Bir `if` deyim, Boolean ifadesinin değerine göre hangi ifadenin çalıştırılalaaçıklamasını tanımlar. Aşağıdaki örnekte, `bool` değişken `condition` ayarlanır `true` ve daha sonra `if` deyiminde işaretlenir. Çıktı. `The variable is set to true.`

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Bu konudaki örnekleri bir konsol uygulaması `Main` yöntemine yerleştirerek çalıştırabilirsiniz.

`if` Aşağıdaki örnekte görüldüğü gibi, C# ifadesi iki biçim alabilir.

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

Bir `if-else` açıklamada, `condition` doğru değerlendirirse, `then-statement` çalışır. Eğer `condition` yanlışsa, `else-statement` çalışır. Aynı `condition` anda doğru ve yanlış olamaz, `else-statement` çünkü `if-else` bir ifadenin `then-statement` ve ifadenin her ikisi de çalıştırılamaz. Çalıştırmaveya `then-statement` çalıştırmadan `else-statement` sonra, denetim deyimden `if` sonra bir sonraki ifadeye aktarılır.

Bir `if` deyim içermeyen bir `else` deyimde, `condition` eğer doğruysa, `then-statement` çalışır. Yanlışsa, `condition` denetim deyimden `if` sonra bir sonraki ifadeye aktarılır.

Hem `then-statement` de `else-statement` parantez içinde kapalı tek bir ifade veya birden çok`{}`ifadeden oluşabilir ( ). Tek bir ifade için ayraçlar isteğe bağlıdır, ancak önerilir.

İfade veya ifadeler `then-statement` ve `else-statement` orijinal `if` deyimi içinde iç içe `if` başka bir ifade de dahil olmak üzere, her türlü olabilir. İç içe `if` geçen `else` ifadelerde, her `if` bir yan tümce `else`karşılık gelen olmayan son maddeye aittir. Aşağıdaki örnekte, `Result1` her ikisi `m > 10` `n > 20` de ve doğru değerlendirmek görüntülenir. Doğruysa `m > 10` ancak `n > 20` yanlışsa `Result2` görüntülenir.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Bunun yerine, yanlış `Result2` olduğunda `(m > 10)` görünmek istiyorsanız, aşağıdaki örnekte görüldüğü gibi iç içe alan `if` deyimin başlangıç ve sonunu oluşturmak için ayraçları kullanarak bu ilişkilendirme belirtebilirsiniz.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2`koşul `(m > 10)` yanlış olarak değerlendirilirse görünür.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, klavyeden bir karakter girersiniz ve program `if` giriş karakterinin alfabetik bir karakter olup olmadığını belirlemek için iç içe bir deyim kullanır. Giriş karakteri alfabetik bir karakterse, program giriş karakterinin küçük veya büyük harf olup olmadığını denetler. Her servis talebi için bir ileti görüntülenir.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Örnek

Aşağıdaki kısmi kodun gösterdiği gibi, bir `if` deyimi başka bir bloğun içine de ekte yapabilirsiniz. Örnek, deyimleri diğer iki blok ve bir blok içinde yuvalar. `if` Açıklamalar, her blokta hangi koşulların doğru veya yanlış olduğunu belirtir.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, giriş karakterinin küçük harf mi, büyük harf mi yoksa bir sayı mı olduğunu belirler. Üç koşul da yanlışsa, karakter alfasayısal bir karakter değildir. Örnek, her servis talebi için bir ileti görüntüler.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Else bloğundaki veya sonrabloğundaki bir deyimin geçerli bir ifade olması gibi, durum için geçerli boolean ifadesini kullanabilirsiniz. , , `&&` `||`, `&` `|`, `!`gibi [mantıksal işleçleri](../operators/boolean-logical-operators.md) kullanabilirsiniz ve `^` bileşik koşullar yapmak için. Aşağıdaki kod örnekleri gösterir.

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

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [?: Operatör](../operators/conditional-operator.md)
- [if-else Deyimi (C++)](/cpp/cpp/if-else-statement-cpp)
- [Anahtarı](switch.md)
