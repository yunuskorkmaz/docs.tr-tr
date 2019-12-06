---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: b3f236b2378d6af78f034856e3ba0f7a9e17993c
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837148"
---
# <a name="xmllang-handling-in-xaml"></a>XAML'de xml:lang İşleme
`xml:lang` özniteliği, XML içindeki bir öğe için dil ve kültür bilgilerini bildiren XML tanımlı bir özniteliktir. Özniteliğin bu anlamı XAML 'de devam ediyor; Ancak bazı ek konular geçerlidir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*rfc3066lang*|[RFC 3066](https://www.ietf.org/rfc/rfc3066.txt) standbundan türetilmiş ve bir dil ya da dil bölgesi tanımlayan bir dize. İkinci olduğunda, dil ve bölge tek bir tire ile ayrılır. Değerler ve biçim hakkında daha fazla bilgi için bkz. <xref:System.Windows.Markup.XmlLanguage>.|  
  
## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] `xml:lang` özniteliğinin tanımı, XML için World Wide Web Konsorsiyumu (W3C) tarafından bir "özel öznitelik" olarak tanımlanan `xml:lang` türetilir. Dil ve kültür bilgileri, uygulamalarına bağlı olarak, öğelere göre farklı yollarla işlenir; Ancak, `xml:lang` özniteliğinde varsayılan [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işleme yoktur.  
  
 `xml:lang` özniteliğin varsayılan değeri, öznitelik düzeyindeki boş bir dizedir.  
  
 `xml:lang` öznitelik etkileri ve öznitelik değeri, `xml:lang` değerler üzerinde işlem gören sistemler tarafından yorumlandığında genellikle alt öğelere işlenir.  
  
 .NET Framework XAML hizmetlerinin XAML yazarları tarafından yorumlanırken, `xml:lang` bir değer temel alınan nesne gösteriminde <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> nesneleri oluşturabilir; Ancak, bu davranış, `xml:lang` için belirtilen değerin bu sınıflar için geçerli bir oluşturma olup olmamasına bağlıdır.  
  
 Çerçeveler, özelliğe <xref:System.Windows.Markup.XmlLangPropertyAttribute> uygulayarak çerçeve tanımlı özellikler ve XML 'deki `xml:lang` anlamı arasında ilişkiler oluşturabilir.  
  
## <a name="wpf-usage-nodes"></a>WPF kullanım düğümleri  
 <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>türetilmiş sınıfları olan öğeler için `xml:lang` özniteliği yerine eşdeğer <xref:System.Windows.FrameworkElement.Language%2A> bağımlılık özelliğini kullanabilirsiniz. Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği, başka bir şekilde ayarlanmamışsa, özelliği aracılığıyla veya `xml:lang` özniteliği işlenerek "en-US" kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](../wpf/advanced/globalization-for-wpf.md)
