---
title: $-dize ilişkilendirme- C# başvuru
ms.custom: seodec18
description: Dize ilişkilendirme, dize çıkışını geleneksel dize bileşik biçimlendirmeden biçimlendirmek için daha okunabilir ve kullanışlı bir sözdizimi sağlar.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 53a8938a373136df65e23c162b94c4d8dc1f30b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253860"
---
# <a name="---string-interpolation-c-reference"></a>$-dize ilişkilendirme (C# başvuru)

Özel `$` karakter, bir dize sabit değerini, *enterpolasyonlu dize*olarak tanımlar. Enterpolasyonlu dize, *enterpolasyon ifadeleri*içerebilen bir dize sabit değeri. Bir enterpolasyonlu dize bir sonuç dizesine çözümlendiğinde, enterpolasyon ifadesi içeren öğeler, ifade sonuçlarının dize gösterimleriyle değiştirilmiştir. Bu özellik C# 6 ' dan itibaren kullanılabilir.

Dize ilişkilendirme, [dize bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md) özelliğinden biçimlendirilmiş dizeler oluşturmak için daha okunabilir ve uygun bir sözdizimi sağlar. Aşağıdaki örnek, aynı çıktıyı üretmek için her iki özelliği de kullanır:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Enterpolasyonlu bir dizenin yapısı

Bir dize sabit değerini, enterpolasyonlu bir dize olarak tanımlamak için, `$` simgeyi simgesiyle önüne ekleyin. `$` Ve arasındabirdizesabitiBaşlatanboşlukolamaz.`"`

Enterpolasyon ifadesi içeren bir öğenin yapısı aşağıdaki gibidir:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Köşeli parantezler içindeki öğeler isteğe bağlıdır. Aşağıdaki tabloda her öğe açıklanmaktadır:

|Öğe|Açıklama|
|-------------|-----------------|
|`interpolationExpression`|Biçimlendirilecek bir sonuç üreten ifade. `null` Öğesinin<xref:System.String.Empty?displayProperty=nameWithType>dize temsili.|
|`alignment`|Değeri, ifade sonucunun dize temsilinde minimum karakter sayısını tanımlayan sabit ifade. Pozitif ise, dize temsili sağa hizalanır; negatifse, sola hizalanır. Daha fazla bilgi için bkz. [Hizalama bileşeni](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|İfade sonucunun türü tarafından desteklenen bir biçim dizesi. Daha fazla bilgi için bkz. [Biçim dize bileşeni](../../../standard/base-types/composite-formatting.md#format-string-component).|

Aşağıdaki örnek, yukarıda açıklanan isteğe bağlı biçimlendirme bileşenlerini kullanır:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Özel karakterler

"{" Veya "}" küme ayracı eklemek için, enterpolasyonlu bir dize tarafından üretilen metinde, "{{" veya "}}" iki küme ayracı kullanın. Daha fazla bilgi için bkz. [kaçış ayraçları](../../../standard/base-types/composite-formatting.md#escaping-braces).

İki nokta üst üste (":"), enterpolasyon ifadesi öğesinde [koşullu bir işleç](../operators/conditional-operator.md) kullanmak için bir ilişkilendirme ifadesinde özel anlamı olduğundan, bu ifadeyi parantez içine alın.

Aşağıdaki örnek, bir sonuç dizesinde bir küme ayracın nasıl ekleneceğini ve bir ilişkilendirme ifadesinde koşullu işlecin nasıl kullanılacağını gösterir:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Ara değerli bir dize, `$` karakteriyle ve ardından `@` karakteri ile başlar. Tam dizeler hakkında daha fazla bilgi için bkz. [dize](../keywords/string.md) ve tam [tanımlayıcı](verbatim.md) konuları.

> [!NOTE]
> 8,0 ' C# den başlayarak, `$` ve `@` belirteçlerinidilediğiniz`$@"..."` sırada kullanabilirsiniz: her ikisi de geçerlibiraradeğerlidizeler.`@$"..."` Önceki C# sürümlerde, `$` belirtecin `@` belirteçten önce görünmesi gerekir.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Örtük dönüştürmeler ve uygulama belirtme `IFormatProvider`

Enterpolasyonlu bir dizeden üç örtük dönüştürme vardır:

1. Enterpolasyonlu bir dizenin, <xref:System.String> sonuçları doğru biçimli dize gösterimlerine göre değiştirilmekte olan enterpolasyon ifade öğeleriyle birlikte bulunan bir örneğe dönüştürülmesi. Bu dönüştürme, <xref:System.Globalization.CultureInfo.CurrentCulture> ' ın biçim ifadesi sonuçlarını kullanır.

1. Enterpolasyonlu bir dizenin <xref:System.FormattableString> , bir bileşik biçim dizesini temsil eden, ifade sonuçlarıyla birlikte bir örneğe dönüştürülmesi. Bu, tek <xref:System.FormattableString> bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza olanak sağlar. Bunu yapmak için aşağıdaki yöntemlerden birini çağırın:

      - İçin sonuç dizesi üreten bir <xref:System.FormattableString.ToString> aşırı yükleme. <xref:System.Globalization.CultureInfo.CurrentCulture>
      - İçin sonuç dizesi üreten bir <xref:System.FormattableString.Invariant%2A> yöntem. <xref:System.Globalization.CultureInfo.InvariantCulture>
      - Belirtilen <xref:System.FormattableString.ToString(System.IFormatProvider)> kültür için sonuç dizesi üreten bir yöntem.

    Yöntemi, <xref:System.FormattableString.ToString(System.IFormatProvider)> özel biçimlendirmeyi destekleyen <xref:System.IFormatProvider> arabirimin Kullanıcı tanımlı bir uygulamasını sağlamak için de kullanabilirsiniz. Daha fazla bilgi için [.net makalesindeki biçimlendirme türleri](../../../standard/base-types/formatting-types.md) konusunun [ICustomFormatter ile özel biçimlendirme](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) bölümüne bakın.

1. Enterpolasyonlu bir dizenin tek <xref:System.IFormattable> <xref:System.IFormattable> bir örnekten kültüre özgü içerikle birden çok sonuç dizesi oluşturmanıza izin veren bir örneğe dönüştürülmesi.

Aşağıdaki örnek, kültüre özgü sonuç dizeleri <xref:System.FormattableString> oluşturmak için için örtük dönüştürmeyi kullanır:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Ek kaynaklar

Dize ilişkilendirme konusunda yeni bir adım daha kullanıyorsanız etkileşimli öğreticide [dize ilişkilendirmeyi C# ](../../tutorials/exploration/interpolated-strings.yml) inceleyin. Ayrıca, biçimlendirilen dizeleri oluşturmak için, enterpolasyonlu dizelerin nasıl kullanılacağını gösteren öğreticideki başka bir [dize ilişkilendirmeyi C# ](../../tutorials/string-interpolation.md) da denetleyebilirsiniz.

## <a name="compilation-of-interpolated-strings"></a>Enterpolasyonlu dizelerin derlenmesi

Bir enterpolasyonlu dize türü `string`varsa, genellikle bir <xref:System.String.Format%2A?displayProperty=nameWithType> yöntem çağrısına dönüştürülür. Çözümlenen davranış birleştirme ile <xref:System.String.Format%2A?displayProperty=nameWithType> eşdeğer <xref:System.String.Concat%2A?displayProperty=nameWithType> olacaksa, derleyici ile değiştirilebilir.

Bir enterpolasyonlu dize türü <xref:System.IFormattable> veya <xref:System.FormattableString>ise, derleyici <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> yöntemine bir çağrı oluşturur.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [enterpolasyonlu dizeler](~/_csharplang/spec/expressions.md#interpolated-strings) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# özel karakterleri](index.md)
- [Dizeler](../../programming-guide/strings/index.md)
- [Sayısal sonuçlar tablosunu biçimlendirme](../keywords/formatting-numeric-results-table.md)
- [Bileşik biçimlendirme](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
