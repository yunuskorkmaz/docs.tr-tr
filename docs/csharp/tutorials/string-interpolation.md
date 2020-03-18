---
title: "C'de dize enterpolasyonu #"
description: Biçimlendirilmiş ifade sonuçlarını C#'da string enterpolasyonuyla bir sonuç dizesine nasıl eklendiğini öğrenin.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039205"
---
# <a name="string-interpolation-in-c"></a>C'de dize enterpolasyonu\#

Bu öğretici, bir sonuç dizesinde ifade sonuçlarını biçimlendirmek ve eklemek için [dize enterpolasyonunu](../language-reference/tokens/interpolated.md) nasıl kullanacağınızı gösterir. Örnekler, temel C# kavramlarıve .NET türü biçimlendirme aşina olduğunuzu varsayar. Dize enterpolasyonu veya .NET türü biçimlendirmede yeniyseniz, önce [etkileşimli dize enterpolasyon öğreticisine](exploration/interpolated-strings.yml) göz atın. .NET'teki biçimlendirme türleri hakkında daha fazla bilgi için [.NET konusundaki Biçimlendirme Türleri'ne](../../standard/base-types/formatting-types.md) bakın.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Giriş

[Dize enterpolasyon](../language-reference/tokens/interpolated.md) özelliği bileşik [biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin üstüne inşa edilmiştir ve bir sonuç dizesinde biçimlendirilmiş ifade sonuçlarını içerecek şekilde daha okunabilir ve kullanışlı bir sözdizimi sağlar.

Bir dize literal bir interpolated dize olarak `$` tanımlamak için, sembolü ile prepend. Enterpolasyonlu bir dize bir değer döndüren herhangi bir geçerli C# ifadesini katıştırabilirsiniz. Aşağıdaki örnekte, bir ifade değerlendirilir değerlendirilmez, sonucu bir dize dönüştürülür ve bir sonuç dizesine dahil edilir:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Örnekte de görüldüğü gibi, bir ifadeyi ayraçlarla ekleyerek enterpolasyonlu bir dize eklersiniz:

```csharp
{<interpolationExpression>}
```

Enterpolasyonlu dizeleri [dize bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin tüm yeteneklerini destekler. Bu onları <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemin kullanımına daha okunabilir bir alternatif yapar.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Enterpolasyon ifadesi için biçim dizesi nasıl belirtilir?

Bir üst üste (":") ve biçim dizesi ile enterpolasyon ifadesini izleyerek ifade sonucunun türü tarafından desteklenen bir biçim dizesi belirtirsiniz:

```csharp
{<interpolationExpression>:<formatString>}
```

Aşağıdaki örnek, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizelerinin nasıl belirtilen;

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Biçimlendirme Bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) biçimi bölümüne bakın. Bu bölümde, .NET taban türleri tarafından desteklenen standart ve özel biçim dizelerini açıklayan konulara bağlantılar sağlar.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Biçimlendirilmiş enterpolasyon ifadesinin alan genişliği ve hizalaması nasıl kontrol edilebilen

Enterpolasyon ifadesini virgülle (",") ve sabit ifadeyle izleyerek en az alan genişliğini ve biçimlendirilmiş ifade sonucunun hizalanmasını belirtirsiniz:

```csharp
{<interpolationExpression>,<alignment>}
```

*Hizalama* değeri pozitifse, biçimlendirilmiş ifade sonucu sağ hizalanır; negatif ise, sol hizalı.

Hem hizalama hem de biçim dizesi belirtmeniz gerekiyorsa, hizalama bileşeniyle başlayın:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

Aşağıdaki örnek, hizalamanın nasıl belirtilen ve metin alanlarını sınırlamak için boru karakterlerini ("|") nasıl kullandığını gösterir:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Örnek çıktının gösterdiği gibi, biçimlendirilmiş ifade sonucunun uzunluğu belirtilen alan genişliğini aşıyorsa, *hizalama* değeri yoksayılır.

Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Hizalama Bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümüne bakın.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>İnterpolated dize kaçış dizileri nasıl kullanılır

Enterpolasyonlu dizeleri sıradan dize literals kullanılabilir tüm kaçış dizileri destekler. Daha fazla bilgi için [String kaçış dizilerine](../programming-guide/strings/index.md#string-escape-sequences)bakın.

Kaçış dizilerini kelimenin tam anlamıyla yorumlamak [için, kelimenin tam anlamıyla](../language-reference/tokens/verbatim.md) bir dize harfi kullanın. İnterpolated verbatim dize `$` `@` karakter tarafından takip karakter ile başlar. C# 8.0 ile başlayarak, `$` `@` belirteçleri ve belirteçleri herhangi bir sırada kullanabilirsiniz: her ikisi de `$@"..."` ve `@$"..."` geçerli enterpolasyonlu kelime dizeleri vardır.

Bir sonuç dizesinde "{" veya "}" bir ayraç eklemek için iki ayraç kullanın: "{{" veya "}}". Daha fazla bilgi [için, Bileşik Biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Kaçan Ayraçlar](../../standard/base-types/composite-formatting.md#escaping-braces) bölümüne bakın.

Aşağıdaki örnek, bir sonuç dizesi parantez dahil etmek ve bir kelimenin tam olarak enterpolasyonlu dize oluşturmak nasıl gösterir:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Bir enterpolasyon ifadesinde üçüncül `?:` koşullu işleç nasıl kullanılır?

Bir ifadede [koşullu işleci](../language-reference/operators/conditional-operator.md) kullanmak için bir enterpolasyon ifadesi olan bir öğede üst üste (":") özel bir anlamı olduğundan, aşağıdaki örnekte görüldüğü gibi, onu parantez içine avurun:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Dize enterpolasyonu ile kültüre özgü bir sonuç dizesi nasıl oluşturulur?

Varsayılan olarak, enterpolasyonlu bir dize <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> tüm biçimlendirme işlemleri için özellik tarafından tanımlanan geçerli kültürü kullanır. Enterpolasyonlu bir dizenin <xref:System.FormattableString?displayProperty=nameWithType> bir örne <xref:System.FormattableString.ToString(System.IFormatProvider)> örtük dönüşümünü kullanın ve kültüre özgü bir sonuç dizesi oluşturmak için yöntemini çağırın. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Örnekte görüldüğü gibi, çeşitli <xref:System.FormattableString> kültürler için birden çok sonuç dizeleri oluşturmak için bir örnek kullanabilirsiniz.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Değişmez kültürü kullanarak sonuç dizesi nasıl oluşturulur?

<xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Yöntemle birlikte, interpollenmiş bir <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> dizeiçin <xref:System.Globalization.CultureInfo.InvariantCulture>bir sonuç dizesini çözmek için statik yöntemi kullanabilirsiniz. Aşağıdaki örnek, bunun nasıl yapılacağını gösterir:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Sonuç

Bu öğretici, dize enterpolasyon kullanımının yaygın senaryolarını açıklar. String enterpolasyonu hakkında daha fazla bilgi için [String enterpolasyon](../language-reference/tokens/interpolated.md) konusuna bakın. .NET'teki biçimlendirme türleri hakkında daha fazla bilgi için .NET ve [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) [konularındaki Biçimlendirme Türleri'ne](../../standard/base-types/formatting-types.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Dize](../programming-guide/strings/index.md)
