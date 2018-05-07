---
title: mc:Ignorable Özniteliği
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 7b8a2ef6e27bc6b25776157e59bef04b883fcb1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mcignorable-attribute"></a>mc:Ignorable Özniteliği
Belirten [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] biçimlendirme dosyasında karşılaşılan ad alanı öneklerini dikkate tarafından bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci. `mc:Ignorable` Özniteliği, hem hem de özel ad alanı eşlemesi için biçimlendirme uyumluluğunu destekler [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML öznitelik kullanımı (tek önek)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML öznitelik kullanımı (iki önek)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1, vb.*|XML 1.0 belirtimi başına herhangi geçerli önek dizesi.|  
|*ignorableUri*|XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.|  
|*ThisElementCanBeIgnored*|Tarafından göz ardı edilebilir bir öğe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] temel alınan tür çözümlenemiyorsa işlemcisi uygulamaları.|  
  
## <a name="remarks"></a>Açıklamalar  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Ad alanı öneki olan eşlenirken kullanmak için önerilen öneki kuralı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluk ad alanı [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Öğeleri veya burada öğesi adının öneki bölümü olarak tanımlandığında öznitelikleri `mc:Ignorable` tarafından işlendiğinde hata oluşturmaz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci. Bir temel alınan tür veya programlama yapı bu öznitelik çözümlenemedi, o öğeye göz ardı edilir. Ancak yoksayılan öğelerin işlenmeyen o öğenin yan etkileri olan ek öğe gereksinimleri için ek ayrıştırma hataları oluşturabilir unutmayın. Örneğin, belirli bir öğenin içerik modeli belirtilen alt öğe içinde olup olmadığını ancak tam olarak bir alt öğe gerektirebilir bir `mc:Ignorable` öneki ve belirtilen alt öğe bir türe çözümlenemedi sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci olabilir bir hata oluştur.  
  
 `mc:Ignorable` yalnızca ad alanı tanımlayıcı dizelere eşlemeleri için geçerlidir. `mc:Ignorable` ad alanı eşlemesi belirtmek derlemeye uygulanmaz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı ve bir derleme (veya varsayılan derleme gibi geçerli yürütülebilir).  
  
 Uyguluyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci, işlemci uygulamanız gerekir değil Yükselt ayrıştırma veya herhangi bir öğe veya olarak tanımlanan bir önek nitelenen öznitelik türü çözümlenmek hatalarda işlem `mc:Ignorable`. Ancak, işlemci uygulamanız yüklenemiyor veya daha önce verilen bir alt öğe örneği gibi işlenmesi başarısız olan bir öğenin ikincil sonucunda oluşan özel durumlar ortaya çıkarabilir.  
  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar. Bununla birlikte, ek bir öznitelik belirtebilirsiniz [mc: ProcessContent özniteliği](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md)sonraki kullanılabilir üst öğe tarafından yoksayılan öğe içindeki içeriğin sürekli işlenmesini gerektirmek için.  
  
 Birden çok ön eklerin bir veya daha fazla boşluk karakterleri ayırıcı olarak örneğin kullanarak özniteliği belirtilebilir: `mc:Ignorable="ignore1 ignore2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Ad alanını tanımlayan diğer öğeleri ve bu alanda belgelenmemiş öznitelikleri [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Daha fazla bilgi için bkz: [XML Biçimlendirmesi Uyumluluk Belirtimi](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Markup.XamlReader>  
 [PresentationOptions:Freeze Özniteliği](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [XAML'ye Genel Bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
