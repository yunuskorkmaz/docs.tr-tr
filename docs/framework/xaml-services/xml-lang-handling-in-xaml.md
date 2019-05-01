---
title: XAML'de xml:lang İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
ms.openlocfilehash: 6495e980beea8731c47a774589919f160b4551ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053606"
---
# <a name="xmllang-handling-in-xaml"></a>XAML'de xml:lang İşleme
`xml:lang` Özniteliği bir [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-XML'deki bir öğenin dil ve kültür bilgilerini bildiren tanımlı öznitelik. Bu öznitelik aynı anlamı devam ederse XAML; Ancak, bazı ek hususlar geçerlidir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*rfc3066lang*|Türetilen bir dize [RFC 3066](https://go.microsoft.com/fwlink/?LinkId=132454) standart bir dili veya dil bölge tanımlar. İkincisi, dil ve bölge tek bir çizgi ile ayrılır. Bkz: <xref:System.Windows.Markup.XmlLanguage> değerleri ve biçimi hakkında daha fazla bilgi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımı `xml:lang` özniteliğini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] türetilir `xml:lang` "özel özniteliği" tarafından tanımlanan [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] için [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Dil ve kültür bilgilerini, potansiyel olarak kendi uygulamalarını bağlı olarak, öğeleri tarafından farklı şekillerde işlenir; Bununla birlikte, varsayılan yok [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlenmesi `xml:lang` özniteliği.  
  
 Varsayılan değer olan `xml:lang` özniteliktir özniteliği düzeyinde boş bir dize.  
  
 `xml:lang` Özniteliği etkiler ve öznitelik değeri genellikle perpetuated alt öğeler üzerinde işlem sistemleri tarafından yorumlandığında `xml:lang` değerleri.  
  
 .NET Framework XAML hizmetlerinde, XAML yazarlar tarafından yorumlandığında bir `xml:lang` değer oluşturabilir <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> nesneleri temel nesne gösterimi; ancak, bu davranışı bağlıdır içinbelirtilendeğer`xml:lang`sınıflar için geçerli bir yapıdır.  
  
 Çerçeveler, çerçeve tarafından tanımlanmış özellikler ve anlamını arasındaki ilişkileri oluşturabilir `xml:lang` uygulayarak XML <xref:System.Windows.Markup.XmlLangPropertyAttribute> özelliğine.  
  
## <a name="wpf-usage-nodes"></a>WPF kullanım düğümleri  
 Öğeleri türetilmiş sınıfları için <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, eşdeğer kullanabileceğiniz <xref:System.Windows.FrameworkElement.Language%2A> bağımlılık özelliği yerine `xml:lang` özniteliği. Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliğini "en-US" kullanır, aksi takdirde, özelliği veya işleme yoluyla ayarlanmazsa `xml:lang` özniteliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](../wpf/advanced/globalization-for-wpf.md)
