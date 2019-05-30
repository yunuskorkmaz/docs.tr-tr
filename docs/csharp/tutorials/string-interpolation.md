---
title: C# dize ilişkilendirme
description: Dize ilişkilendirme ile C# dilinde bir sonuç dizesi olarak biçimlendirilmiş bir ifade sonuçları eklemeyi öğrenin.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 2990298821fddc8a69430a4cf4bb5e3dd9df314d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251025"
---
# <a name="string-interpolation-in-c"></a>C'de dize ilişkilendirme\#

Bu öğreticide nasıl kullanılacağını gösterir [dize ilişkilendirme](../language-reference/tokens/interpolated.md) biçimlendirmek ve ifade sonuçları bir sonuç dizesine eklemek için. Örnekler C# temel kavramları ve .NET türü biçimlendirme ile ilgili bilgi sahibi olduğunuz varsayılır. Dize ilişkilendirme veya .NET türü biçimlendirme için yeni başladıysanız, kullanıma [etkileşimli dize ilişkilendirme öğretici](exploration/interpolated-strings.yml) ilk. . NET'te türleri biçimlendirme hakkında daha fazla bilgi için bkz. [NET'teki biçimlendirme türleri](../../standard/base-types/formatting-types.md) konu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Giriş

[Dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği üzerine kurulmuştur [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özellik ve biçimlendirilmiş bir ifade sonuçları bir sonuç dizesine eklemek için daha okunabilir ve kullanışlı bir söz dizimi sağlar.

Bir dize ilişkilendirilmiş dize sabit değeri belirlemek için onunla önüne ekleyin `$` simgesi. Bir aradeğerlendirme dizesinde bir değer döndüren herhangi bir geçerli C# ifade ekleyebilir. Aşağıdaki örnekte, bir ifade değerlendirilir hemen sonra sonucu bir dizeye dönüştürülür ve sonuç dizesine dahil:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Örnekte gösterildiği gibi bir ifade bir aradeğerlendirme dizesinde küme ayraçlarıyla kapsayan tarafından şunlardır:

```
{<interpolationExpression>}
```

İlişkilendirilmiş dizeler destekleyen tüm özelliklerine [bileşik biçimlendirme dizesi](../../standard/base-types/composite-formatting.md) özelliği. Getiren bunları kullanımını daha okunabilir bir alternatif <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Bir biçim dizesi için bir ilişkilendirme ifade belirtme

İki nokta ile ilişkilendirme ifade izleyerek ifadenin sonuç türü tarafından desteklenen bir biçim dizesi belirtin (":") ve biçim dizesi:

```
{<interpolationExpression>:<formatString>}
```

Aşağıdaki örnekte, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizeleri belirtmek gösterilmektedir:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Daha fazla bilgi için [biçim dizesi bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu. Bu bölüm .NET temel türleri tarafından desteklenen standart ve özel biçim dizeleri açıklayan konulara bağlantılar sağlar.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Alan genişliğini ve hizalamasını biçimlendirilmiş ilişkilendirme ifade denetleme

En düşük alan genişliğini ve hizalamasını biçimlendirilmiş bir ifade sonucu ilişkilendirme ifade bir virgül ile izleyerek belirtin (",") ve sabit ifade:

```
{<interpolationExpression>,<alignment>}
```

Varsa *hizalama* değeri pozitif ise sağa hizalı biçimlendirilmiş bir ifade sonucu; negatif ise sola hizalanmış.

Hizalama hem bir biçim dizesi belirtmek gerekirse, hizalama bileşeni ile başlayın:

```
{<interpolationExpression>,<alignment>:<formatString>}
```

Aşağıdaki örnek hizalaması belirtmek nasıl gösterir ve kullandığı kanal karakter ("|") metin alanları sınırlandırmak için:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Örnek olarak biçimlendirilmiş bir ifade sonucunun uzunluğu aşması durumunda çıktıda gösterildiği, alan genişliğini belirtilen *hizalama* değer yoksayılır.

Daha fazla bilgi için [hizalama bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Bir aradeğerlendirme dizesinde çıkış sıraları kullanma

İlişkilendirilmiş dizeler sıradan dize değişmez değerleri kullanılabilir tüm kaçış dizileri destekler. Daha fazla bilgi için [dize kaçış dizileri](../programming-guide/strings/index.md#string-escape-sequences).

Kaçış dizileri tam anlamıyla yorumlanması için kullanmak bir [verbatim](../language-reference/tokens/verbatim.md) dize sabit değeri. Verbatim ilişkilendirilmiş bir dize ile başlayan `$` karakteri ve ardından `@` karakter.

Bir küme ayracı, dahil etmek için "{" veya "}", bir sonuç dizesinde iki küme ayraçları kullanın "{{" veya "}}". Daha fazla bilgi için [kaçış küme ayraçları](../../standard/base-types/composite-formatting.md#escaping-braces) bölümünü [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konu.

Aşağıdaki örnek, küme ayraçları bir sonuç dizesine eklemek ve bir harfi harfine ilişkilendirilmiş dize oluşturma gösterilmektedir:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Üçlü koşullu bir işleç kullanmayı `?:` ilişkilendirme ifadede

İki nokta üst üste olarak (":") kullanmak için bir ilişkilendirme ifadeyle bir öğedeki özel anlama sahip bir [koşullu işleç](../language-reference/operators/conditional-operator.md) aşağıdaki örnekte gösterildiği gibi parantez içine bir ifadede:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Dize ilişkilendirme ile bir kültüre özgü sonuç dizesi oluşturma

Varsayılan olarak, bir aradeğerlendirme dizesinde tarafından tanımlanan geçerli kültürü kullanan <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> tüm biçimlendirme işlemleri için özellik. Örtük dönüştürme için bir aradeğerlendirme dizesinde kullanmak bir <xref:System.FormattableString?displayProperty=nameWithType> örneği ve çağrı kendi <xref:System.FormattableString.ToString(System.IFormatProvider)> bir kültüre özgü sonuç dizesi oluşturmak için yöntemi. Aşağıdaki örnek bunu nasıl yapacağınız gösterilmektedir:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Örnekte gösterildiği gibi kullanabilirsiniz <xref:System.FormattableString> örneğini çeşitli kültürler için kullanılabilecek birden fazla sonuç dizeleri üretir.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Sabit kültür kullanılarak bir sonuç dizesi oluşturma

İle birlikte <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> yöntemi statik kullanabileceğiniz <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemi için bir sonuç dizesini bir aradeğerlendirme dizesinde çözümlemek için <xref:System.Globalization.CultureInfo.InvariantCulture>. Aşağıdaki örnek bunu nasıl yapacağınız gösterilmektedir:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Sonuç

Bu öğreticide, dize ilişkilendirme kullanım yaygın senaryolar açıklanmaktadır. Dize ilişkilendirme hakkında daha fazla bilgi için bkz: [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konu. . NET'te türleri biçimlendirme hakkında daha fazla bilgi için bkz. [NET'teki biçimlendirme türleri](../../standard/base-types/formatting-types.md) ve [bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konuları.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Dizeler](../programming-guide/strings/index.md)
