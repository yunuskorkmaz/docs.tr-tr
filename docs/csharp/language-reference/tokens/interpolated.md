---
title: $ - dize ilişkilendirme (C# Başvurusu)
description: Dize ilişkilendirme daha geleneksel dize bileşik biçimlendirme dizesi çıkış biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6873c3b419323fa9f5523143ad607289b6fd6e2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="---string-interpolation-c-reference"></a>$ - dize ilişkilendirme (C# Başvurusu)

`$` Özel karakter tanımlayan bir dize sabit değeri olarak bir *Ara değerli dize*. Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*. Ara değerli dize çözüldüğünde, örneğin bir atama ifadesi veya bir yöntem çağrısı Ara değerli ifadeler Sonuç dizesini üretmek için sonuçları dize gösterimlerini tarafından değiştirilir. Bu özellik, C# 6 ve sonraki sürümlerinde kullanılabilir.

Dize ilişkilendirme daha biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve kolay bir yolu olan bir [bileşik biçimlendirme dize](../../../standard/base-types/composite-formatting.md) özelliği. Aşağıdaki örnek, aynı çıktı oluşturmak için her iki özellik kullanır:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> Arasında herhangi bir boşluk olamaz `$` ve `"` dize başlar. Bunun yapılması, derleme zamanı hatasına neden olur.

Ara değerli bir ifadenin bir öğesiyle yapısı aşağıdaki gibidir:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Köşeli parantezler içindeki öğeler isteğe bağlıdır. Aşağıdaki tablo her öğeyi açıklar.

|Öğe|Açıklama|
|-------------|-----------------|
|`interpolatedExpression`|Biçimlendirilecek bir sonuç almak için değerlendirilecek olan ifade. Dize gösterimini `null` sonuç <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Sabit ifade değeri Ara değerli ifadenin sonucu dize gösterimini en az karakter sayısını tanımlar. Pozitif, sağa hizalı dize gösterimi; negatifse, sola hizalı. Daha fazla bilgi için bkz: [hizalama bileşen](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|İfade sonucunun türü tarafından desteklenen standart veya özel biçim dizesi. Daha fazla bilgi için bkz: [biçim dizesi bileşen](../../../standard/base-types/composite-formatting.md#format-string-component).|

Aşağıdaki örnek, yukarıdaki tabloda açıklandığı gibi biçimlendirme isteğe bağlı bileşenler kullanır:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

Kaşlı ayraç içerecek şekilde ("{" veya "}") iki süslü ayraçlar Ara değerli bir dize tarafından üretilen metin kullanma "{{" veya "}}". Daha fazla bilgi için bkz: [kaçış ayraçlar](../../../standard/base-types/composite-formatting.md#escaping-braces).

Noktalı virgül (;) özel bir anlamı kullanmak için bir ara değerli ifade öğesi var. gibi bir [koşullu işleç](../operators/conditional-operator.md) Ara değerli bir ifadede bu ifadesi parantez içine alın.

Aşağıdaki örnekte, kaşlı ayraç sonuç dizeye dahil etme ve Ara değerli bir ifadede koşullu bir işleç kullanma gösterilmektedir:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Harfi harfine dizeler Kullan'ı değiştirilmiş `$` karakter arkasından `@` karakter. Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](../keywords/string.md) konu.

> [!NOTE]
> `$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.

## <a name="implicit-conversions"></a>Örtük dönüşümler

Ara değerli bir dizeden üç örtük tür dönüşümleri vardır:

1. Ara değerli bir dizeye dönüştürme bir <xref:System.String> Ara değerli ifade ile Ara değerli dize çözümlemesi sonucu örneği öğelerini sonuçları düzgün biçimlendirilmiş dize gösterimlerini ile değiştiriliyor. Bu dönüştürme geçerli kültürü kullanır.

1. Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> bileşik biçimi gösteren değişkeni Biçimlendirilecek ifade sonuçları birlikte dize. Kültüre özgü ile birden çok sonuç dizesi oluşturmak için tek bir içerik sağlayan <xref:System.FormattableString> örneği. Yapmak için aşağıdaki yöntemlerden birini arayın:

      - A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - A <xref:System.FormattableString.Invariant%2A> için bir sonuç dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem.

1. Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> ayrıca birden çok sonuç oluşturmanıza olanak tanıyan bir değişken dizeler tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.

Aşağıdaki örnek, örtük dönüştürmeye kullanır <xref:System.FormattableString> kültüre özgü sonuç dizeleri oluşturmak için:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-reading"></a>Ek kaynaklar

Dize ilişkilendirme yeniyseniz, denetleme [Ara değerli dizeler quickstart](../../quick-starts//interpolated-strings.yml). Daha fazla örnek için bkz: [dize ilişkilendirme Öğreticisi](../../tutorials/string-interpolation.md).

## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)  
 [Dizeler](../../../csharp/programming-guide/strings/index.md)  
 [C# Özel Karakterleri](../../../csharp/language-reference/tokens/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# başvurusu](../../../csharp/language-reference/index.md)  