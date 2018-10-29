---
title: $ - dize ilişkilendirme (C# Başvurusu)
description: Dize ilişkilendirme, daha geleneksel dize bileşik biçimlendirme dizesi çıkış biçimine daha okunabilir ve kullanışlı bir söz dizimi sağlar.
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
ms.openlocfilehash: 2758a724b7e1e410fd1e1ba262db451b7f994164
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196995"
---
# <a name="---string-interpolation-c-reference"></a>$ - dize ilişkilendirme (C# Başvurusu)

`$` Özel karakter tanımlayan bir dize sabit değeri olarak bir *ilişkilendirilmiş bir dizedir*. İçerebilir bir dize sabit değeri ilişkilendirilmiş bir dizedir *ilişkilendirilmiş ifade*. İlişkilendirilmiş dize bir sonuç dizesine çözüldüğünde, ilişkilendirilmiş ifadeler öğeleriyle ifade sonuçları dize temsillerini tarafından değiştirilir. Bu özellik, C# 6 ve sonraki sürümlerinde dil kullanılabilir.

Dize ilişkilendirme, biçimlendirilmiş dize değerinden oluşturmak için daha okunabilir ve kullanışlı bir söz dizimi sağlar bir [bileşik biçimlendirme dizesi](../../../standard/base-types/composite-formatting.md) özelliği. Aşağıdaki örnek, aynı çıktı oluşturmak için her iki özellik kullanır:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Bir aradeğerlendirme dizesinde yapısı

Bir dize ilişkilendirilmiş dize sabit değeri belirlemek için onunla önüne ekleyin `$` simgesi. Arasında beyaz boşluk olamaz `$` ve `"` bir dize sabit değeri başlar. Bunun yapılması, bir derleme zamanı hatasına neden olur.

Bir öğe ile ilişkilendirilmiş ifade yapısı aşağıdaki gibidir:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Köşeli parantezler içindeki öğeler isteğe bağlıdır. Aşağıdaki tablo her öğeyi açıklar:

|Öğe|Açıklama|
|-------------|-----------------|
|`interpolatedExpression`|Biçimlendirilecek bir sonuç üretir ifade. Dize gösterimini `null` sonucudur <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Sabit ifade değeri, ilişkilendirilmiş ifadenin sonucu dize gösterimi en az karakter sayısını tanımlar. Pozitif ise sağa hizalı dize gösterimi; negatif ise sola hizalıdır. Daha fazla bilgi için [hizalama bileşeni](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Deyim sonucu türü tarafından desteklenen bir biçim dizesi. Daha fazla bilgi için [biçim dizesi bileşeni](../../../standard/base-types/composite-formatting.md#format-string-component).|

Aşağıdaki örnek, yukarıda açıklanan isteğe bağlı bir biçimlendirme bileşenleri kullanır:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Özel karakterler

Bir küme ayracı, dahil etmek için "{" veya "}", bir aradeğerlendirme dizesinde tarafından üretilen metinde iki küme ayraçları kullanın "{{" veya "}}". Daha fazla bilgi için [kaçış küme ayraçları](../../../standard/base-types/composite-formatting.md#escaping-braces).

İki nokta üst üste olarak (":") kullanmak için ilişkilendirilmiş ifade öğenin özel anlama sahip bir [koşullu işleç](../operators/conditional-operator.md) , parantez içindeki ifade bir ilişkilendirilmiş ifadede alın.

Aşağıdaki örnek, sonuç dizesinde ayraç ekleme ve bir ilişkilendirilmiş ifadede koşullu bir işleç kullanma işlemini gösterir:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Verbatim ilişkilendirilmiş bir dize ile başlayan `$` karakteri ve ardından `@` karakter. Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](../keywords/string.md) ve [tam tanımlayıcı](verbatim.md) konuları.

> [!NOTE]
> `$` Belirteci önce görünmelidir `@` verbatim ilişkilendirilmiş dize belirteci.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Örtük dönüşümler ve belirterek `IFormatProvider` uygulama

Bir aradeğerlendirme dizesinde üç örtük dönüştürmelerine vardır:

1. Bir araya alınmış dizeye dönüştürme bir <xref:System.String> ilişkilendirilmiş ifade ile ilişkilendirilmiş dize çözümü sonucu olan örneği öğelerini sonuçları düzgün şekilde biçimlendirilmiş dize temsillerini ile değiştiriliyor. Bu dönüştürme, geçerli kültürü kullanır.

1. Bir araya alınmış dizeye dönüştürme bir <xref:System.FormattableString> Biçimlendirilecek ifade sonuçları ile birlikte bir bileşik biçimlendirme dizesi temsil eden örneği. Kültüre özgü ile birden çok sonuç dizeleri oluşturmak için tek bir içerik sağlayan <xref:System.FormattableString> örneği. Yapmak için aşağıdaki yöntemlerden birini arayın:

      - A <xref:System.FormattableString.ToString> için bir sonuç dizesi oluşturur aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Bir <xref:System.FormattableString.Invariant%2A> için bir sonuç dizesi oluşturur yöntemi <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> yönteminin belirtilen kültür için bir sonuç dizesi oluşturur.

    Ayrıca <xref:System.FormattableString.ToString(System.IFormatProvider)> kullanıcı tanımlı bir uygulamasını sağlamak üzere yöntemi <xref:System.IFormatProvider> özel biçimlendirmeyi destekleyen arabirimi. Daha fazla bilgi için [Icustomformatter ile özel biçimlendirme](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Bir araya alınmış dizeye dönüştürme bir <xref:System.IFormattable> Ayrıca, birden çok sonuç oluşturmanıza olanak sağlayan örnek dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.

Aşağıdaki örnek örtük olarak dönüştürülmesine kullanır <xref:System.FormattableString> kültüre özgü sonuç dizeleri oluşturmak için:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Ek kaynaklar

Dize ilişkilendirme için yeni başlıyorsanız bkz [dize ilişkilendirme, C# ](../../tutorials/intro-to-csharp/interpolated-strings.yml) etkileşimli öğretici. Ya da deneyebilirsiniz [dize ilişkilendirme, C# ](../../tutorials/string-interpolation.md) makinenizde yerel olarak öğretici.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)
- [Dizeler](../../programming-guide/strings/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Özel Karakterleri](index.md)
- [C# başvurusu](../index.md)
