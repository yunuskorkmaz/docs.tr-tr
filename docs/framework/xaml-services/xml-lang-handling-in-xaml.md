---
title: "XAML'de xml:lang İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:lang attribute
- xml:lang attribute [XAML Services]
- RFC 3066 standard [XAML Services]
- standards [XAML Services], RFC 3066
ms.assetid: 7aac0078-a1c5-41f8-b8b0-975510d9dca0
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 47dd34db82e796418b68fcf9b28ef3e4d4eaca4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xmllang-handling-in-xaml"></a>XAML'de xml:lang İşleme
`xml:lang` Özniteliği bir [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]-XML'deki bir öğenin dil ve kültür bilgilerini bildiren tanımlı öznitelik. Bu öznitelik ile aynı anlamı XAML'de devam ederse; Ancak, bazı ek hususlar geçerlidir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object xml:lang="rfc3066lang" />  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*rfc3066lang*|Türetilen bir dize [RFC 3066](http://go.microsoft.com/fwlink/?LinkId=132454) standart ve bir dil veya dil bölge tanımlar. İkincisi, bölge ve dil tek bir çizgi ile ayrılır. Bkz: <xref:System.Windows.Markup.XmlLanguage> değerler ve biçimi hakkında daha fazla bilgi için.|  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımı `xml:lang` özniteliğini [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] türetildiği `xml:lang` "özel özniteliği" tarafından tanımlanan [!INCLUDE[TLA#tla_w3c](../../../includes/tlasharptla-w3c-md.md)] için [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)]. Dil ve kültür bilgilerini potansiyel olarak kendi uygulamalarını bağlı olarak öğeler tarafından farklı şekillerde işlenir; Ancak, varsayılan yok [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] işlenmesi `xml:lang` özniteliği.  
  
 Varsayılan değer olan `xml:lang` boş bir dize özniteliği düzeyinde bir özniteliktir.  
  
 `xml:lang` Özniteliği etkiler ve öznitelik değeri genellikle perpetuated alt öğelerine hareket sistemler tarafından yorumlanan zaman `xml:lang` değerleri.  
  
 .NET Framework XAML hizmetlerinde XAML yazarlar tarafından yorumlanan olduğunda bir `xml:lang` değeri oluşturabilir <xref:System.Windows.Markup.XmlLanguage> veya <xref:System.Globalization.CultureInfo> temel nesneleri nesne gösterimi; ancak, bu davranışı bağlıdır içinbelirtilendeğer`xml:lang`bu sınıfların geçerli bir yapıdır.  
  
 Çerçeveler framework tarafından tanımlanan özellikler ve anlamını arasındaki ilişkilendirmeleri oluşturma `xml:lang` uygulayarak XML <xref:System.Windows.Markup.XmlLangPropertyAttribute> özelliğine.  
  
## <a name="wpf-usage-nodes"></a>WPF kullanım düğümler  
 Türetilmiş sınıflar, öğeleri için <xref:System.Windows.FrameworkElement> veya <xref:System.Windows.FrameworkContentElement>, eşdeğer kullanabilirsiniz <xref:System.Windows.FrameworkElement.Language%2A> yerine bağımlılık özelliği `xml:lang` özniteliği. Varsayılan olarak, <xref:System.Windows.FrameworkElement.Language%2A> özelliği "en-US" kullanır, aksi takdirde, özellik veya işlem aracılığıyla ayarlanmamışsa `xml:lang` özniteliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için genelleştirme](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
