---
title: string (C# Başvurusu)
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
ms.openlocfilehash: 748016682db6e02cadbfb8c767391a18d48e1286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="string-c-reference"></a>string (C# Başvurusu)
`string` Türü sıfır veya daha fazla Unicode karakterler dizisini temsil eder. `string` bir diğer adı için <xref:System.String> .NET içinde.  
  
 Ancak `string` bir başvuru türü eşitlik işleçleri (`==` ve `!=`) değerlerini karşılaştırmak için tanımlanan `string` nesneleri, değil başvuruyor. Bu, daha sezgisel dize eşitlik için test kolaylaştırır. Örneğin:  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Bu "True" görüntüler ve ardından "False" dizeleri içeriğini eşdeğer olduğundan ancak `a` ve `b` aynı dize örneğine başvurmamasını sağlama.  
  
 + İşleci dizeleri art arda ekler:  
  
```csharp  
string a = "good " + "morning";  
```  
  
 Bu, "Günaydın" içeren bir dize nesnesi oluşturur.  
  
 Dizelerdir *değişmez*--bir dize nesnesi içeriğini nesne oluşturulduktan sonra değiştirilemez, sözdizimi yapar ancak görünür Bunu yapmak gibi. Örneğin, bu kodu yazarken derleyici gerçekten yeni karakter dizisi tutmak için yeni bir dize nesnesi oluşturur ve bu yeni nesne B'ye atanır. "Y" dizesi sonra atık toplama için uygundur.  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 [] İşleci tek tek karakter salt okunur erişim için kullanılan bir `string`:  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Dize değişmez değerleri türündedir `string` ve tırnak içine alınmış iki biçimde yazılabilir ve @-quoted. Değişmez değerler çift tırnak işaretleri (") arasına alınan sınırlandırılmış:  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Dize değişmez değerleri değişmez değer herhangi bir karakter içerebilir. Kaçış sıraları dahil edilir. Aşağıdaki örnek, kaçış sırası kullanır `\\` ters eğik çizgi için `\u0066` harfi f için ve `\n` yeni satır için.  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Çıkış kodu `\udddd` (burada `dddd` dört basamaklı bir sayı değil) Unicode karakteri U + temsil eden`dddd`. Sekiz basamaklı Unicode çıkış kodları ayrıca tanınan: `\Udddddddd`.  
  
 Harfi harfine dize değişmez değerleri başlayarak `@` ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 Harfi harfine dizeler avantajlarından kaçış sıraları olmasıdır *değil* işlenen, hangi kolaylaştırır yazma, örneğin, bir tam dosya adı:  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Çift tırnak işareti içinde dahil etmek için bir @-quoted dize, onu çift:  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Diğer kullanımlar için `@` özel karakter bkz [@--verbatim tanımlayıcı](../tokens/verbatim.md).  
  
 C# dizeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeleri Kullanmak için En İyi Uygulamalar](../../../standard/base-types/best-practices-strings.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)  
 [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)  
 [Sayısal Sonuçlar Tablosunu Biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
