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
ms.openlocfilehash: 2cbfab57ffaf294109f9f01f228f2826097fc299
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151401"
---
# <a name="if-else-c-reference"></a>if-else (C# Başvurusu)

Bir `if` deyimi çalıştırmak için hangi deyimi, bir Boolean ifadesinin değerine göre tanımlar. Aşağıdaki örnekte, `bool` değişkeni `result` ayarlanır `true` ve ardından iade `if` deyimi. Çıktı `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

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

İçinde bir `if-else` ifadesi varsa `condition` true olarak değerlendirilen `then-statement` çalıştırır. Varsa `condition` false ise `else-statement` çalıştırır. Çünkü `condition` aynı anda true ve false olamaz `then-statement` ve `else-statement` , bir `if-else` deyimi hiçbir zaman hem de çalıştırabilirsiniz. Sonra `then-statement` veya `else-statement` çalıştığında, Denetim, sonra sonraki deyime aktarılır `if` deyimi.

İçinde bir `if` deyimi içermeyen bir `else` deyimi, `condition` true ise `then-statement` çalıştırır. Varsa `condition` yanlış denetimi sonra sonraki deyime aktarılır `if` deyimi.

Hem `then-statement` ve `else-statement` tek bir deyim veya küme ayraçları içine alınmış birden çok deyim içerebilir (`{}`). Tek bir deyim için Küme ayraçları isteğe bağlıdır ancak önerilir.

Deyim ya da deyimlerinde `then-statement` ve `else-statement` başka dahil olmak üzere, herhangi bir türden olabilir `if` deyimi özgün içinde iç içe `if` deyimi. İçinde iç içe geçmiş `if` deyimleri, her `else` yan tümcesi ait son `if` karşılık gelen yok `else`. Aşağıdaki örnekte, `Result1` her iki görünür `m > 10` ve `n > 20` true olarak değerlendirin. Varsa `m > 10` geçerlidir ancak `n > 20` false ise `Result2` görünür.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Bunun yerine, isterseniz `Result2` olduğunda görüntülenecek `(m > 10)` başındaki ve sonundaki iç içe'kurmak için küme ayraçlarını kullanarak bu ilişkiyi belirleyebilir, yanlış `if` aşağıdaki örnekte gösterildiği gibi bir ifade.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` görünür koşul `(m > 10)` yanlış olarak değerlendirilir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir karakter klavyeden girmeniz ve iç içe bir programın kullandığı `if` girdi karakteri alfabetik bir karakter olup olmadığını belirlemek için deyimi. Girdi karakteri alfabetik bir karakter ise, programın giriş karakterin büyük harf veya küçük harf olup olmadığını denetler. Her durum için bir ileti görüntülenir.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Örnek

Ayrıca yuvalayabilirsiniz bir `if` başka bir blok içinde bir ifade aşağıdaki kodu kısmi gösterildiği gibi. Örnek Yuvalar `if` iki başka blokları ve ardından bloğu içindeki deyimler. True veya false her blok içinde hangi koşullar açıklamaları belirtin.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir girdi karakteri küçük harf, bir büyük harf veya sayı olup olmadığını belirler. Üç tüm koşullar false olursa, karakterin alfasayısal bir karakter değildir. Örneğin, her örneği için bir ileti görüntüler.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Yalnızca bir deyimde başka bloğu ya da sonra blok herhangi bir geçerli ifade olabilir, koşul için geçerli bir Boole ifade kullanabilirsiniz. Mantıksal işleçler gibi kullanabileceğiniz [ && ](../operators/conditional-and-operator.md), [ & ](../operators/and-operator.md), [ &#124; &#124; ](../operators/conditional-or-operator.md), [ &#124; ](../operators/or-operator.md) ve [!](../operators/logical-negation-operator.md) Bileşik koşul yapma. Aşağıdaki kod örnekleri gösterir.

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

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [?: İşleç](../operators/conditional-operator.md)  
- [if-else Deyimi (C++)](/cpp/cpp/if-else-statement-cpp)  
- [switch](switch.md)  
