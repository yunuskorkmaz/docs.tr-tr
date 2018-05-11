---
title: C# dize ilişkilendirme
description: Dize ilişkilendirme ile C# sonuç dizesine biçimlendirilmiş ifade sonuçlarında öğrenin.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 3e463ceb0902658107280559b7fb57849beb8153
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="string-interpolation-in-c"></a>C# dize ilişkilendirme #

Bu öğretici nasıl kullanılacağını gösterir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçimlendirmek ve bir sonuç dizesinde ifade sonuçları dahil edin. Örnekler, temel C# kavramları ve .NET türü biçimlendirme bildiğinizi varsayar. Dize ilişkilendirme veya .NET türü biçimlendirme yeniyseniz, kullanıma [etkileşimli dize ilişkilendirme quickstart](../quick-starts/interpolated-strings.yml) ilk. Biçimlendirme .NET türleri hakkında daha fazla bilgi için bkz: [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) konu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Giriş

[Dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği üstünde oluşturulan [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özellik ve sonucu dize biçimlendirilmiş ifade sonuçları dahil etmek daha okunabilir ve kullanışlı bir sözdizimi sağlar.

Bir dize olarak ara değerli bir dize sabit değeri tanımlamak için kendisiyle başına `$` simgesi. Ara değerli bir dize bir değer döndüren herhangi bir geçerli C# ifadeler eklenebilir. Aşağıdaki örnekte, bir ifadenin hemen sonucunu bir dizeye dönüştürülür ve bir sonuç dizesinde yer:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Yukarıda gösterildiği örnek olarak, köşeli parantez ile kapsayan tarafından Ara değerli bir dize bir ifade içerir:

```
{<interpolatedExpression>}
```

Derleme zamanında Ara değerli bir dize genellikle dönüştürülür bir <xref:System.String.Format%2A?displayProperty=nameWithType> yöntem çağrısı. Tüm özelliklerine yapar [bileşik biçimlendirme dize](../../standard/base-types/composite-formatting.md) özelliği de ara değerli dizeler ile kullanmak için de kullanılabilir.

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>Ara değerli bir ifade için bir biçim dizesi belirtme

Ara değerli ifadesi iki nokta ile izleyerek ifade sonucunun türü tarafından desteklenen bir biçim dizesini belirtin (":") ve biçim dizesi:

```
{<interpolatedExpression>:<formatString>}
```

Aşağıdaki örnekte, tarih ve saat veya sayısal sonuçlar üretmek ifadeler için standart ve özel biçim dizeleri belirtmek gösterilmektedir:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Daha fazla bilgi için bkz: [biçim dizesi bileşen](../../standard/base-types/composite-formatting.md#format-string-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu. Bu bölüm .NET temel türleri tarafından desteklenen standart ve özel biçim dizeleri açıklayan konulara bağlantılar sağlar.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>Alan genişliği ve hizalamasını biçimlendirilmiş Ara değerli ifadesinin denetleme

Ara değerli ifade virgül ile izleyerek en düşük alan genişliği ve biçimlendirilmiş ifade sonucu hizalamasını belirtin (",") ve sabit ifade:

```
{<interpolatedExpression>,<alignment>}
```

Varsa *hizalama* değer pozitif, sağa hizalı biçimlendirilmiş ifade sonucu; negatifse, sola hizalı.

Hizalama ve bir biçim dizesi belirtmeniz gerekiyorsa, hizalama bileşeniyle başlatın:

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

Aşağıdaki örnek hizalamayı belirtme gösterir ve kullandığı kanal karakterler ("|") metin alanları sınırlandırmak için:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Örnek olarak biçimlendirilmiş ifade sonucunun uzunluğu aşması durumunda çıkış gösterir, alan genişliği belirtilen *hizalama* değeri yoksayılır.

Daha fazla bilgi için bkz: [hizalama bileşen](../../standard/base-types/composite-formatting.md#alignment-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Ara değerli bir dize çıkış sıraları kullanma

Ara değerli dizeler kullanılabilir tüm kaçış sıraları sıradan dize değişmez değerleri destekler. Daha fazla bilgi için bkz: [dize kaçış sıraları](../programming-guide/strings/index.md#string-escape-sequences).

Kaçış dizileri tam anlamıyla yorumlamak için kullanılan kullanan bir [verbatim](../language-reference/tokens/verbatim.md) dize sabit değeri. Harfi harfine Ara değerli bir dize ile başlayan `$` karakter arkasından `@` karakter.

Bir küme parantezi dahil etmek için "{" veya "}", bir sonuç dizesinde iki küme ayraçları kullanmak "{{" veya "}}". Daha fazla bilgi için bkz: [kaçış ayraçlar](../../standard/base-types/composite-formatting.md#escaping-braces) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.

Aşağıdaki örnek, sonuç dizesinde kaşlı ayraç içeren ve verbatim Ara değerli dizesi oluşturmak gösterilmektedir:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>Üçlü koşullu bir işleç kullanma `?:` Ara değerli deyimde

İki nokta üst üste olarak (":") kullanmak için bir ara değerli ifade sahip bir öğe içinde özel bir anlamı yoktur bir [koşullu işleç](../language-reference/operators/conditional-operator.md) aşağıdaki örnekte gösterildiği gibi parantez içine bir ifadede:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Kültüre özgü Sonuç dizesini dize ilişkilendirme oluşturma

Varsayılan olarak, Ara değerli bir dize tarafından tanımlanan geçerli kültür kullanır <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> tüm biçimlendirme işlemleri için özellik. Ara değerli bir dize olarak örtük dönüştürme kullanmak bir <xref:System.FormattableString?displayProperty=nameWithType> örneği ve arama kendi <xref:System.FormattableString.ToString(System.IFormatProvider)> bir kültüre özgü sonuç dizesi oluşturmak için yöntem. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Örnekte gösterildiği gibi kullanabilirsiniz <xref:System.FormattableString> çeşitli kültürler için birden çok sonuç dizelerini oluşturmak için örnek.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Sabit kültür kullanarak bir sonuç dize oluşturma

İle birlikte <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> yöntemi statik kullanabilirsiniz <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> Ara değerli bir dize için bir sonuç dizeye çözümlemek için yöntemi <xref:System.Globalization.CultureInfo.InvariantCulture>. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Sonuç

Bu öğretici dize ilişkilendirme kullanımı genel senaryolar açıklanmaktadır. Dize ilişkilendirme hakkında daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu. Biçimlendirme .NET türleri hakkında daha fazla bilgi için bkz: [.NET biçimlendirme türleri](../../standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) Konular.

## <a name="see-also"></a>Ayrıca bkz.

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[Dizeler](../programming-guide/strings/index.md)  
