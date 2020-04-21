---
title: $ - dize enterpolasyonu - C# referans
description: Dize enterpolasyonu, dize çıktısını geleneksel dize bileşik biçimlendirmesine göre biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 2b95fa5fe5cecd4825e8c17a33f7795c6c9480c6
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738370"
---
# <a name="---string-interpolation-c-reference"></a>$ - dize enterpolasyonu (C# referansı)

Özel `$` karakter, bir dize literal *bir interpolated dize*olarak tanımlar. Enterpolasyonlu dize, *enterpolasyon ifadeleri*içerebilecek bir dize dir. Enterpolasyonlu bir dize bir sonuç dizesine çözüldüğünde, enterpolasyon ifadeleri içeren öğeler ifade sonuçlarının dize gösterimleri ile değiştirilir. Bu özellik C# 6 ile başlayarak kullanılabilir.

Dize enterpolasyonu, [dize bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md) özelliğinden daha biçimlendirilmiş dizeleri oluşturmak için daha okunabilir ve kullanışlı bir sözdizimi sağlar. Aşağıdaki örnek, aynı çıktıyı üretmek için her iki özelliği de kullanır:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>İnterpolated dize yapısı

Bir dize literal bir interpolated dize olarak `$` tanımlamak için, sembolü ile prepend. Bir dize harfi ile `$` başlayan `"` arasında herhangi bir beyaz boşluk olamaz.

Enterpolasyon ifadesi olan bir öğenin yapısı aşağıdaki gibidir:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Köşeli parantezler içindeki öğeler isteğe bağlıdır. Aşağıdaki tabloda her öğe açıklanır:

|Öğe|Açıklama|
|-------------|-----------------|
|`interpolationExpression`|Biçimlendirilecek bir sonuç üreten ifade. String `null` gösterimi <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|İfade sonucunun dize gösterimindeki en az karakter sayısını tanımlayan değer olan sabit ifade. Pozitifse, dize gösterimi doğru hizalanmış; negatif ise, sol hizalı. Daha fazla bilgi için [Hizalama Bileşeni'ne](../../../standard/base-types/composite-formatting.md#alignment-component)bakın.|
|`formatString`|İfade sonucunun türü tarafından desteklenen bir biçim dizesi. Daha fazla bilgi için [Bkz. Biçim Dize Bileşeni.](../../../standard/base-types/composite-formatting.md#format-string-component)|

Aşağıdaki örnekte, yukarıda açıklanan isteğe bağlı biçimlendirme bileşenleri kullanır:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Özel karakterler

Enterpolasyonlu bir dize tarafından üretilen metne "{" veya "}" bir ayraç eklemek için "{{" veya "}}" olmak üzere iki ayraç kullanın. Daha fazla bilgi için [bkz.](../../../standard/base-types/composite-formatting.md#escaping-braces)

Üst üste (":") bir enterpolasyon ifade öğesinde özel bir anlamı olduğundan, bir enterpolasyon ifadesinde [koşullu işleç](../operators/conditional-operator.md) kullanmak için, bu ifadeyi parantez içine alar.

Aşağıdaki örnek, bir sonuç dizesine nasıl bir ayraç eklenmeyi ve bir enterpolasyon ifadesinde koşullu işlecinin nasıl kullanılacağını gösterir:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

İnterpolated verbatim dize `$` `@` karakter tarafından takip karakter ile başlar. Kelime nin dizeleri hakkında daha fazla bilgi için [dize](../builtin-types/reference-types.md) ve [tam olarak tanımlayıcı](verbatim.md) konulara bakın.

> [!NOTE]
> C# 8.0 ile başlayarak, `$` `@` belirteçleri ve belirteçleri herhangi bir sırada kullanabilirsiniz: her ikisi de `$@"..."` ve `@$"..."` geçerli enterpolasyonlu kelime dizeleri vardır. Önceki C# sürümlerinde `$` belirteç belirteçten `@` önce görünmelidir.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Örtülü dönüşümler ve `IFormatProvider` uygulamanın nasıl belirtilir

Enterpolasyonlu bir dizeden üç örtük dönüşüm vardır:

1. Enterpolasyonlu bir dize, enterpolasyon ifade öğelerinin sonuçlarının düzgün biçimlendirilmiş dize gösterimleriyle değiştirildiği enterpolasyon lu dize çözünürlüğünün sonucu olan bir <xref:System.String> örne dönüştürülmesi. Bu dönüştürme <xref:System.Globalization.CultureInfo.CurrentCulture> ifade sonuçlarını biçimlendirmek için kullanır.

1. Enterpolasyonlu bir dizenin biçimlendirilecek ifade sonuçlarıyla birlikte bileşik biçim dizesini temsil eden bir <xref:System.FormattableString> örne dönüştürülmesi. Bu, tek <xref:System.FormattableString> bir örnekten kültüre özgü içeriğe sahip birden çok sonuç dizesi oluşturmanıza olanak tanır. Bunu yapmak için aşağıdaki yöntemlerden birini arayın:

      - <xref:System.Globalization.CultureInfo.CurrentCulture>Için <xref:System.FormattableString.ToString> bir sonuç dizesi üreten aşırı yük.
      - <xref:System.Globalization.CultureInfo.InvariantCulture>Için <xref:System.FormattableString.Invariant%2A> bir sonuç dizesi üreten bir yöntem.
      - Belirli <xref:System.FormattableString.ToString(System.IFormatProvider)> bir kültür için sonuç dizesi üreten bir yöntem.

    Yöntemi, <xref:System.FormattableString.ToString(System.IFormatProvider)> özel biçimlendirmeyi destekleyen <xref:System.IFormatProvider> arabirimin kullanıcı tanımlı bir uygulamasını sağlamak için de kullanabilirsiniz. Daha fazla bilgi [için,.NET makalesindeki Biçimlendirme türlerinin](../../../standard/base-types/formatting-types.md) [ICustomFormatter bölümüyle Özel biçimlendirmebölümüne](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) bakın.

1. Enterpolasyonlu bir dizenin, tek <xref:System.IFormattable> <xref:System.IFormattable> bir örnekten kültüre özgü içeriğe sahip birden çok sonuç dizesi oluşturmanıza olanak tanıyan bir örne dönüştürülmesi.

Aşağıdaki örnek, kültüre <xref:System.FormattableString> özgü sonuç dizeleri oluşturmak için örtük dönüştürme kullanır:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Ek kaynaklar

Dize enterpolasyonunda yeniyseniz, C# etkileşimli [öğreticideki String enterpolasyonuna](../../tutorials/exploration/interpolated-strings.yml) bakın. Ayrıca, biçimlendirilmiş dizeleri oluşturmak için enterpolasyonlu dizeleri nasıl kullanılacağını gösteren C# öğreticibaşka bir [String enterpolasyon](../../tutorials/string-interpolation.md) kontrol edebilirsiniz.

## <a name="compilation-of-interpolated-strings"></a>Enterpolasyonlu dizelerin derlemi

Enterpolasyonlu bir dize `string`türüne sahipse, <xref:System.String.Format%2A?displayProperty=nameWithType> genellikle bir yöntem çağrısına dönüştürülür. Derleyici, çözümlenen <xref:System.String.Concat%2A?displayProperty=nameWithType> davranışın birliktemeye eşdeğer olup olmadığını değiştirebilir. <xref:System.String.Format%2A?displayProperty=nameWithType>

Enterpolasyonlu bir dize <xref:System.IFormattable> <xref:System.FormattableString>türü varsa veya derleyici <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> yönteme bir çağrı oluşturur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Enterpolasyonlu dizeleri](~/_csharplang/spec/expressions.md#interpolated-strings) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# özel karakterleri](index.md)
- [Dizeler](../../programming-guide/strings/index.md)
- [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
