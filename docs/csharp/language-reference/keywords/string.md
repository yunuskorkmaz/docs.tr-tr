---
title: "string (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 87df2b158b173072aad5257594e1b1482ae61067
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="string-c-reference"></a>string (C# Başvurusu)
`string` Türü sıfır veya daha fazla Unicode karakterler dizisini temsil eder. `string`bir diğer adı için <xref:System.String> .NET Framework'teki.  
  
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
  
 Harfi harfine dize değişmez değerleri başlayın ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:  
  
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
  
 Başka bir kullanımını kullanmak için @ sembolü başvurulan ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) C# anahtar sözcükler tanımlayıcıları.  
  
 C# dizeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeleri kullanmak için en iyi uygulamalar](../../../standard/base-types/best-practices-strings.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)  
 [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
 [Temel dize işlemleri](../../../standard/base-types/basic-string-operations.md)  
 [Yeni dizeler oluşturma](../../../standard/base-types/creating-new.md)  
 [Sayısal sonuçlar tablosunu biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
