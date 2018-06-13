---
title: $ - dize ilişkilendirme (C# Başvurusu)
description: Dize ilişkilendirme daha geleneksel dize bileşik biçimlendirme dizesi çıkış biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058842"
---
# <a name="---string-interpolation-c-reference"></a>$ - dize ilişkilendirme (C# Başvurusu)

`$` Özel karakter tanımlayan bir dize sabit değeri olarak bir *Ara değerli dize*. Ara değerli bir dize içerebilecek bir değişmez dize değeri olan *Ara değerli ifadeleri*. Ara değerli bir dize sonucu dizeye çözümlendiğinde Ara değerli ifadelerle öğeleri ifade sonuçları dize gösterimlerini tarafından değiştirilir. Bu özellik, C# 6 ve sonraki sürümlerinde dil kullanılabilir.

Dize ilişkilendirme daha biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve kullanışlı bir sözdizimi sağlar bir [bileşik biçimlendirme dize](../../../standard/base-types/composite-formatting.md) özelliği. Aşağıdaki örnek, aynı çıktı oluşturmak için her iki özellik kullanır:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Ara değerli bir dize yapısı

Bir dize olarak ara değerli bir dize sabit değeri tanımlamak için kendisiyle başına `$` simgesi. Arasında herhangi bir boşluk olamaz `$` ve `"` bir değişmez dize değeri başlatır. Bunun yapılması, derleme zamanı hatasına neden olur.

Ara değerli bir ifadenin bir öğesiyle yapısı aşağıdaki gibidir:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Köşeli parantezler içindeki öğeler isteğe bağlıdır. Aşağıdaki tabloda her öğesi açıklar:

|Öğe|Açıklama|
|-------------|-----------------|
|`interpolatedExpression`|Biçimlendirilmiş olması için bir sonuç üreten ifade. Dize gösterimini `null` sonuç <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Sabit ifade değeri Ara değerli ifadenin sonucu dize gösterimini en az karakter sayısını tanımlar. Pozitif, sağa hizalı dize gösterimi; negatifse, sola hizalı. Daha fazla bilgi için bkz: [hizalama bileşen](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|İfade sonucunun türü tarafından desteklenen bir biçim dizesi. Daha fazla bilgi için bkz: [biçim dizesi bileşen](../../../standard/base-types/composite-formatting.md#format-string-component).|

Aşağıdaki örnek, yukarıda açıklanan biçimlendirme isteğe bağlı bileşenler kullanır:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Özel karakterler

Bir küme parantezi dahil etmek için "{" veya "}", iki küme ayraçları Ara değerli bir dize tarafından üretilen metin kullanma "{{" veya "}}". Daha fazla bilgi için bkz: [kaçış ayraçlar](../../../standard/base-types/composite-formatting.md#escaping-braces).

İki nokta üst üste olarak (":") kullanmak için bir ara değerli ifade öğesinde özel bir anlamı yoktur bir [koşullu işleç](../operators/conditional-operator.md) Ara değerli bir ifadede bu ifadesi parantez içine alın.

Aşağıdaki örnek, sonuç dizesinde ayraç ekleme ve Ara değerli bir ifadede koşullu bir işleç kullanmayı gösterir:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Harfi harfine Ara değerli bir dize ile başlayan `$` karakter arkasından `@` karakter. Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](../keywords/string.md) ve [verbatim tanımlayıcı](verbatim.md) Konular.

> [!NOTE]
> `$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Örtük dönüşümler ve belirterek `IFormatProvider` uygulama

Ara değerli bir dizeden üç örtük dönüşümler vardır:

1. Ara değerli bir dizeye dönüştürme bir <xref:System.String> Ara değerli ifade ile Ara değerli dize çözümlemesi sonucu örneği öğelerini sonuçları düzgün biçimlendirilmiş dize gösterimlerini ile değiştiriliyor. Bu dönüştürme geçerli kültürü kullanır.

1. Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> boyunca bileşik biçim dizesi Biçimlendirilecek ifade sonuçlarla temsil eden örneği. Kültüre özgü ile birden çok sonuç dizesi oluşturmak için tek bir içerik sağlayan <xref:System.FormattableString> örneği. Yapmak için aşağıdaki yöntemlerden birini arayın:

      - A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Bir <xref:System.FormattableString.Invariant%2A> için bir sonuç dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem.

    Aynı zamanda <xref:System.FormattableString.ToString(System.IFormatProvider)> , kullanıcı tanımlı bir uygulama sunmak amacıyla yöntemi <xref:System.IFormatProvider> özel biçimlendirmeyi destekler arabirimi. Daha fazla bilgi için bkz: [özel biçimlendirme ICustomFormatter ile](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanızı sağlayan örnek dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.

Aşağıdaki örnek, örtük dönüştürmeye kullanır <xref:System.FormattableString> kültüre özgü sonuç dizesi oluşturmak için:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Ek kaynaklar

Dize ilişkilendirme yeni istiyorsanız bkz [dize ilişkilendirme C#](../../quick-starts/interpolated-strings.yml) hızlı başlangıç. Daha fazla örnek için bkz: [dize ilişkilendirme C#](../../tutorials/string-interpolation.md) Öğreticisi.

## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)  
 [Dizeler](../../programming-guide/strings/index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [C# Özel Karakterleri](index.md)  
 [C# başvurusu](../index.md)  