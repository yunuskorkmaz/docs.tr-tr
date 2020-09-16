---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 92d1eda62ff394df54d9607bab46d9950681e603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548214"
---
# <a name="xmllang-handling-in-xaml"></a>XAML'de xml:lang İşleme

`xml:lang`Özniteliği, XML içindeki bir öğe için dil ve kültür bilgilerini BILDIREN xml tanımlı bir özniteliktir. Özniteliğin bu anlamı XAML 'de devam ediyor; Ancak bazı ek konular geçerlidir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object xml:lang="rfc3066lang" />
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|*rfc3066lang*|[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standbundan türetilmiş ve bir dil ya da dil bölgesi tanımlayan bir dize. İkinci olduğunda, dil ve bölge tek bir tire ile ayrılır. <xref:System.Windows.Markup.XmlLanguage>Değerler ve biçim hakkında daha fazla bilgi için bkz..|

## <a name="remarks"></a>Açıklamalar

İçindeki özniteliği için tanımı, `xml:lang` [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] `xml:lang` XML IÇIN World Wide Web Konsorsiyumu (W3C) tarafından bir "özel öznitelik" olarak tanımlanan öğesinden türetilir. Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğelere göre farklı yollarla işlenir; Ancak, [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] özniteliği için varsayılan işlem yoktur `xml:lang` .

Özniteliğin varsayılan değeri, `xml:lang` öznitelik düzeyindeki boş bir dizedir.

Öznitelik `xml:lang` etkileri ve öznitelik değeri, değerler üzerinde işlem yapan sistemler tarafından yorumlandığında, genellikle alt öğelere işlenir `xml:lang` .

.NET XAML Hizmetleri 'nin XAML yazarları tarafından yorumlanırken bir `xml:lang` değer, <xref:System.Windows.Markup.XmlLanguage> <xref:System.Globalization.CultureInfo> temel alınan nesne gösteriminde oluşturabilir veya nesneleri oluşturabilir; ancak, bu davranış, için belirtilen değerin `xml:lang` Bu sınıflar için geçerli bir oluşturma olup olmamasına bağlıdır.

Çerçeveler `xml:lang` , özelliğine uygulayarak çerçeve tanımlı özellikler ve XML 'nin anlamı arasında ilişkiler oluşturabilir <xref:System.Windows.Markup.XmlLangPropertyAttribute> .

## <a name="wpf-usage-nodes"></a>WPF kullanım düğümleri

Ya da türetilmiş sınıfları olan öğeler için <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> , <xref:System.Windows.FrameworkElement.Language%2A> özniteliği yerine eşdeğer bağımlılık özelliğini kullanabilirsiniz `xml:lang` . Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği, özelliği aracılığıyla veya özniteliği işlenerek, aksi durumda ayarlanmamışsa "en-US" kullanır `xml:lang` .

## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](/dotnet/desktop/wpf/advanced/globalization-for-wpf)
