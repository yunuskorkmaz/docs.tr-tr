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
ms.openlocfilehash: 03439a2c4a1a4de375e90d0e5121e690541e2f0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219336"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable Özniteliği
Belirten [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] biçimlendirme dosyasında karşılaşılan ad alanı öneklerini tarafından dikkate bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci. `mc:Ignorable` Özniteliği işaretleme uyumluluk destekler ve özel ad alanı eşlemesi için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürüm oluşturma.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML öznitelik kullanımı (tek ön ek)  
  
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
|*ignorablePrefix, ignorablePrefix1, vb.*|XML 1.0 belirtimi başına herhangi geçerli bir önek dizesi.|  
|*ignorableUri*|XML 1.0 belirtimi başına bir ad atamak için geçerli bir URI.|  
|*ThisElementCanBeIgnored*|Tarafından göz ardı edilebilir öğenin [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işlemcisi uygulamaları, temel alınan türü çözümlenemiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Ad alanı öneki olan eşlerken kullanılacak önerilen ön eki kuralı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluk ad [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Öğeler veya öznitelikleri burada öğe adı öneki bölümü olarak tanımlandığında `mc:Ignorable` tarafından işlendiğinde bir hata oluşturmaz bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci. Bu öznitelik için bir temel tür veya programlama yapısı çözümlenemedi varsa, o öğenin gözardı edilir. Ancak, yok sayılan öğeleri yan etkileri işlenmeyen o öğenin ek öğesi gereksinimleri için ek ayrıştırma hataları oluşturabilir unutmayın. Örneğin, belirli bir öğenin içerik modeli içinde belirtilen alt öğe bulunamadı, ancak tam olarak bir alt öğesi gerektirebilir bir `mc:Ignorable` öneki ve belirtilen alt öğesi bir türe çözümlenemedi sonra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci olabilir hata oluşturur.  
  
 `mc:Ignorable` yalnızca ad alanı eşlemeleri tanımlayıcısı dizeleri için geçerlidir. `mc:Ignorable` ad uzayı eşlemelerinden belirtin derlemeye uygulanamaz bir [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ad alanı ve bir derleme (veya varsayılan yürütülebilir dosyanın geçerli derleme gibi).  
  
 Uyguluyorsanız bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci, işlemci uygulamanız gerekir değil yükseltmek ayrıştırma veya herhangi bir öğe veya olarak tanımlanan bir ön eke göre koşullu öznitelik için tür çözümlemesi hataları işleme `mc:Ignorable`. Ancak, işlemci uygulamanız hala yüklenemiyor veya daha önce verilen bir alt öğe örneği gibi işlenmesi başarısız olan bir öğenin ikincil sonucunda oluşan özel durumlar oluşturabilir.  
  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan öğe içindeki içeriği yoksayar. Ancak, ek bir öznitelik belirtebilirsiniz [mc: ProcessContent özniteliği](mc-processcontent-attribute.md), devam eden işlemi sonraki kullanılabilir üst öğe tarafından yok sayıldı öğe içindeki içeriğinin gerektirecek şekilde.  
  
 Birden çok ön ek bir veya daha fazla boşluk karakterlerini ayırıcı olarak örneğin kullanarak özniteliği belirtilebilir: `mc:Ignorable="ignore1 ignore2"`.  

 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Diğer öğeleri ve bu alanı içinde belgelenmeyen öznitelikleri ad alanını tanımlayan [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Daha fazla bilgi için [XML işaretleme Uyumluluk Belirtimi](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze Özniteliği](presentationoptions-freeze-attribute.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
