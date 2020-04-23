---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b5a06adbb7cb874bc09899118f13b91fbec7a85e
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071446"
---
# <a name="xmllang-handling-in-xaml"></a>XAML'de xml:lang İşleme

Öznitelik, `xml:lang` XML'deki bir öğenin dil ve kültür bilgilerini bildiren XML tanımlı bir özniteliktir. Özniteliğin bu aynı anlamı XAML'de devam eder; ancak, bazı ek hususlar geçerlidir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*rfc3066lang*|[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standardından türetilen ve bir dili veya dil bölgesini tanımlayan dize. Ne zaman ikincisi, dil ve bölge tek bir tire ile ayrılır. Değerler <xref:System.Windows.Markup.XmlLanguage> ve biçim hakkında daha fazla bilgi için bkz.|

## <a name="remarks"></a>Açıklamalar

Özellik teki `xml:lang` öznitelik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] tanımı, `xml:lang` XML için World Wide Web Konsorsiyumu (W3C) tarafından "özel öznitelik" olarak tanımlanan türetilmiştir. Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğeler tarafından potansiyel olarak farklı şekillerde işlenir; ancak, öznitelik [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] hiçbir varsayılan `xml:lang` işleme yoktur.

Öznitelik varsayılan `xml:lang` değeri öznitelik düzeyinde boş bir dize.

Öznitelik `xml:lang` efektleri ve öznitelik değeri genellikle alt öğelere, değerler üzerinde `xml:lang` hareket sistemleri tarafından yorumlandığında sürdürülür.

.NET XAML Services'In XAML yazarları `xml:lang` tarafından yorumlandığında, bir değer temel nesne gösteriminde oluşturabilir <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> nesneleroluşturabilir; ancak, bu davranış, belirtilen `xml:lang` değerin bu sınıflar için geçerli bir yapı olup olmadığına bağlıdır.

Çerçeveler, özellik için uygulayarak `xml:lang` <xref:System.Windows.Markup.XmlLangPropertyAttribute> çerçeve tanımlı özellikleri ve XML içinde anlamı arasında ilişkiler oluşturabilirsiniz.

## <a name="wpf-usage-nodes"></a>WPF Kullanım Düğümleri

Türemiş sınıflar <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, öznitelik yerine <xref:System.Windows.FrameworkElement.Language%2A> eşdeğer bağımlılık özelliği `xml:lang` kullanabilirsiniz öğeler için. Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özellik, özellik aracılığıyla veya özniteliği işleyerek `xml:lang` başka türlü ayarlanmazsa "en-US" kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](../../framework/wpf/advanced/globalization-for-wpf.md)
