---
title: dize - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: f6c76f8effc5aef82803014b9a7257c2ad6865b8
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286487"
---
# <a name="string-c-reference"></a>string (C# Başvurusu)

`string` Türü bir dizi sıfır veya daha fazla Unicode karakteri temsil eder. `string` için bir diğer addır <xref:System.String> .NET içinde.

Ancak `string` bir başvuru türü eşitlik işleçleri (`==` ve `!=`) değerlerini karşılaştırmak için tanımlanan `string` nesnelerine, başvuruda değil. Bu, daha sezgisel dizeyi eşitlik için sınama yapar. Örneğin:

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

Bu "True" görüntüler ve ardından "False" eşdeğer dizeler içeriğini çünkü ancak `a` ve `b` aynı dize örneğine işaret etmiyor.

+ İşleci dizeleri birleştirir:

```csharp
string a = "good " + "morning";
```

Bu, "Günaydın" içeren bir dize nesnesi oluşturur.

Dizelerdir *değişmez*--bir dize nesnesi, içeriğini nesne oluşturulduktan sonra değiştirilemez, söz dizimi sağlar ancak görünür Bunu yapmak gibi. Örneğin, bu kod yazdığınızda, derleyici, gerçekte yeni dizi karakteri tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne b atanır. "H" dizesi, ardından çöp toplama için uygundur.

```csharp
string b = "h";
b += "ello";
```

[] İşleci karakterlerin tek tek salt okunur erişim için kullanılan bir `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer şekilde, [] işleci ayrıca her bir karakteri üzerinde yineleme için kullanılabilir bir `string`:

```csharp
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Dize değişmez değerleri, tür `string` ve teklif iki biçimde yazılır ve @-quoted. Dize değişmez değerleri çift tırnak işaretleri (") içine alınan Teklif:

```csharp
"good morning"  // a string literal
```

Dize değişmez değerleri, sabit değer herhangi bir karakter içerebilir. Kaçış dizileri dahil edilir. Aşağıdaki örnekte çıkış dizisi `\\` eğik için `\u0066` harfi f, için ve `\n` için yeni satır.

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> Çıkış kodu `\udddd` (burada `dddd` bir dört basamaklı sayıdır) U + Unicode karakteri temsil eden`dddd`. Sekiz basamağı Unicode atlatma kodları da tanınan: `\Udddddddd`.

Verbatim dize değişmez değerleri ile başlayıp `@` ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:

```csharp
@"good morning"  // a string literal
```

Kaçış dizileri: avantajlarındandır harfi harfine dizeler *değil* işlenen, hangi kolaylaştırır, örneğin, tam olarak nitelenmiş dosya adını yazın:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Çift tırnak işareti eklemek için bir @-quoted , çift, dize:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

Diğer kullanımları için `@` özel karakter bkz [@--tam tanımlayıcı](../tokens/verbatim.md).

C# dizeleri hakkında daha fazla bilgi için bkz. [dizeleri](../../programming-guide/strings/index.md).

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../standard/base-types/best-practices-strings.md)
- [C# Anahtar Sözcükleri](index.md)
- [Başvuru Türleri](reference-types.md)
- [Değer Türleri](value-types.md)
- [Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)
- [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)
- [Sayısal Sonuçlar Tablosunu Biçimlendirme](formatting-numeric-results-table.md)
