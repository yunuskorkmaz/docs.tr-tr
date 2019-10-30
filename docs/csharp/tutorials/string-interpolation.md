---
title: Öğesinde dize ilişkilendirmeC#
description: Dize ilişkilendirimiyle içindeki C# bir sonuç dizesinde biçimlendirilen ifade sonuçlarının nasıl ekleneceğini öğrenin.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039205"
---
# <a name="string-interpolation-in-c"></a>C\# 'da dize ilişkilendirme

Bu öğretici, bir sonuç dizesinde ifade sonuçlarını biçimlendirmek ve dahil etmek için [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) nasıl kullanacağınızı gösterir. Örneklerde temel C# kavramlar ve .net tür biçimlendirmesi hakkında bilgi sahibi olduğunuz varsayılır. Dize ilişkilendirme veya .NET tür biçimlendirmesi için yeni bir adım kullanıyorsanız, önce [etkileşimli dize ilişkilendirme öğreticisine](exploration/interpolated-strings.yml) göz atın. .NET 'teki biçimlendirme türleri hakkında daha fazla bilgi için bkz. [.net konusundaki biçimlendirme türleri](../../standard/base-types/formatting-types.md) .

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Giriş

[Dize ilişkilendirme](../language-reference/tokens/interpolated.md) özelliği, [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin üzerine kurulmuştur ve biçimlendirilmiş ifade sonuçlarının bir sonuç dizesinde yer almasını sağlayan daha okunabilir ve uygun bir sözdizimi sağlar.

Bir dize sabit değerini, enterpolasyonlu bir dize olarak tanımlamak için `$` simgesiyle önüne ekleyin. Enterpolasyonlu bir C# dizede değer döndüren herhangi bir geçerli ifadeyi gömebilirsiniz. Aşağıdaki örnekte, bir ifade değerlendirildiği anda, sonucu bir dizeye dönüştürülür ve sonuç dizesine dahil edilir:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Örnekte gösterildiği gibi, araya alınmış dizeye bir ifadeyi küme ayraçları ile çevreleyerek dahil edersiniz:

```csharp
{<interpolationExpression>}
```

Enterpolasyonlu dizeler, [dize bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) özelliğinin tüm yeteneklerini destekler. Bu, <xref:System.String.Format%2A?displayProperty=nameWithType> yönteminin kullanımına daha okunabilir bir alternatif sağlar.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>İlişkilendirme ifadesi için biçim dizesi belirtme

İki nokta üst üste (":") ve biçim dizesiyle ilişkilendirme ifadesini izleyerek, ifade sonucunun türü tarafından desteklenen bir biçim dizesi belirtirsiniz:

```csharp
{<interpolationExpression>:<formatString>}
```

Aşağıdaki örnek, tarih ve saat veya sayısal sonuçlar üreten ifadeler için standart ve özel biçim dizelerinin nasıl kullanılacağını gösterir:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Biçim dizesi bileşeni](../../standard/base-types/composite-formatting.md#format-string-component) bölümüne bakın. Bu bölüm, .NET temel türleri tarafından desteklenen standart ve özel biçim dizelerini tanımlayan konulara bağlantılar sağlar.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Biçimlendirilen enterpolasyon ifadesinin alan genişliğini ve hizalamasını denetleme

Bir virgül (",") ve sabit ifade ile ilişkilendirme ifadesini izleyerek, biçimlendirilen ifade sonucunun en düşük alan genişliğini ve hizalamasını belirtirsiniz:

```csharp
{<interpolationExpression>,<alignment>}
```

*Hizalama* değeri pozitifse, biçimlendirilen ifade sonucu sağa hizalanır; negatifse, sola hizalanır.

Hem hizalama hem de bir biçim dizesi belirtmeniz gerekiyorsa, hizalama bileşeniyle başlayın:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

Aşağıdaki örnek, hizalama belirtme ve metin alanlarını sınırlandırmak için kanal karakterlerinin ("|") nasıl kullanılacağını gösterir:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Örnek çıktıda gösterildiği gibi, biçimlendirilen ifade sonucunun uzunluğu belirtilen alan genişliğini aşarsa, *Hizalama* değeri yok sayılır.

Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [Hizalama bileşeni](../../standard/base-types/composite-formatting.md#alignment-component) bölümüne bakın.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Enterpolasyonlu bir dizede kaçış dizileri kullanma

Enterpolasyonlu dizeler, normal dize değişmez değerlerinde kullanılabilen tüm kaçış dizilerini destekler. Daha fazla bilgi için bkz. [dize kaçış dizileri](../programming-guide/strings/index.md#string-escape-sequences).

Kaçış dizilerini [bire bir yorumlamak](../language-reference/tokens/verbatim.md) için, tam bir dize sabiti kullanın. Enterpolasyonlu bir dize `$` karakteriyle başlar ve ardından `@` karakteri gelir. 8,0 ile C# başlayarak,`$`ve`@`belirteçlerini dilediğiniz sırada kullanabilirsiniz: her iki `$@"..."`ve`@$"..."`geçerli bir ara değerli dizelerdir.

Bir küme ayracı eklemek için, "{" veya "}", bir sonuç dizesinde, "{{" veya "}}" iki küme ayracı kullanın. Daha fazla bilgi için [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konusunun [kaçış ayraçları](../../standard/base-types/composite-formatting.md#escaping-braces) bölümüne bakın.

Aşağıdaki örnek, bir sonuç dizesinde küme ayracın nasıl ekleneceğini ve tam bir enterpolasyonlu dize nasıl oluşturulacağını gösterir:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Enterpolasyon ifadesinde Üçlü koşullu işleç `?:` kullanma

İki nokta üst üste (":") enterpolasyon ifadesi içeren bir öğe için özel anlam içerdiğinden, bir ifadede [koşullu bir işleç](../language-reference/operators/conditional-operator.md) kullanmak için aşağıdaki örnekte gösterildiği gibi, parantez içine alın:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Dize ilişkilendirme ile kültüre özgü sonuç dizesi oluşturma

Varsayılan olarak, bir enterpolasyonlu dize, tüm biçimlendirme işlemleri için <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> özelliği tarafından tanımlanan geçerli kültürü kullanır. Bir <xref:System.FormattableString?displayProperty=nameWithType> örneğine enterpolasyonlu bir dizenin örtük dönüşümünü kullanın ve kültüre özgü bir sonuç dizesi oluşturmak için <xref:System.FormattableString.ToString(System.IFormatProvider)> metodunu çağırın. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Örnekte gösterildiği gibi, çeşitli kültürler için birden çok sonuç dizesi oluşturmak üzere bir <xref:System.FormattableString> örneğini kullanabilirsiniz.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Sabit kültür kullanarak sonuç dizesi oluşturma

<xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> yöntemiyle birlikte, <xref:System.Globalization.CultureInfo.InvariantCulture>için bir sonuç dizesine bir ara değerli dizeyi çözümlemek üzere statik <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Sonuç

Bu öğreticide, dize ilişkilendirme kullanımının yaygın senaryoları açıklanmaktadır. Dize ilişkilendirme hakkında daha fazla bilgi için bkz. [dize ilişkilendirme](../language-reference/tokens/interpolated.md) konusu. .NET 'teki biçimlendirme türleri hakkında daha fazla bilgi için bkz. .NET ve [Bileşik biçimlendirme](../../standard/base-types/composite-formatting.md) konularında [biçimlendirme türleri](../../standard/base-types/formatting-types.md) .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Dizeler](../programming-guide/strings/index.md)
