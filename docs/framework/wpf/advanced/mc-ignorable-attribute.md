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
ms.openlocfilehash: 40c1a8513608728a84b6b605f9ad18603123ea2e
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401535"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable Özniteliği
Bir biçimlendirme dosyasında karşılaşılan [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] adalanıöneklerinebirişlemcitarafındanyoksayılacağınıbelirtir.[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Öznitelik `mc:Ignorable` , hem özel ad alanı eşlemesi [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hem de sürüm oluşturma için biçimlendirme uyumluluğunu destekler.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML öznitelik kullanımı (tek ön ek)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML öznitelik kullanımı (Iki ön ek)  
  
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
|*ıgnorableprefix, ignorablePrefix1, vb.*|XML 1,0 belirtimine göre geçerli herhangi bir ön ek dizesi.|  
|*ıgnorableuri*|XML 1,0 belirtimine göre bir ad alanı atamak için geçerli bir URI.|  
|*Thiselementcanbeyoksayıldı*|Temel alınan tür çözümlenemiyorsa, işlemci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] uygulamaları tarafından yoksayılabilir bir öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ad alanı ön eki, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluk ad alanını [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)]eşlerken kullanılacak önerilen önek kuralıdır. `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]  
  
 Öğe adının `mc:Ignorable` önek kısmının, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcinin işlendiği sırada hata oluşturmayacağını, öğe veya öznitelikler. Bu öznitelik, temel alınan bir tür veya programlama yapısına çözümlenemiyorsa, bu öğe yok sayılır. Ancak yoksayılan öğelerin, bu öğenin işlenmediği yan etkileri olan ek öğe gereksinimleri için ek ayrıştırma hataları ürettiğine de devam edebileceğine unutmayın. Örneğin, belirli bir öğe içerik modeli tam olarak bir alt öğe gerektirebilir, ancak belirtilen alt öğe `mc:Ignorable` bir ön ekse ve belirtilen alt öğe bir tür [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] olarak çözümlenemiyorsa, işlemci bir hata oluştur.  
  
 `mc:Ignorable`yalnızca tanımlayıcı dizelerine ad alanı eşlemeleri için geçerlidir. `mc:Ignorable`, bir CLR ad alanı ve derleme (veya varsayılan olarak geçerli yürütülebilir dosya için derleme) belirten derlemelerdeki ad alanı eşlemeleri için geçerli değildir.  
  
 Bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci uygularsınız, işlemci uygulamanız, olarak `mc:Ignorable`tanımlanan bir ön ek tarafından nitelenen herhangi bir öğe veya öznitelik için tür çözünürlüğünde ayrıştırma veya işleme hatalarını yükseltmemelidir. Ancak işlemci uygulamanız, daha önce verilen tek alt öğe örneği gibi, yükleme veya işleme başarısız olan bir öğenin ikincil sonucu olan özel durumları yine de oluşturabilir.  
  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemci yoksayılan bir öğe içindeki içeriği yoksayar. Ancak, bir sonraki kullanılabilir üst öğe tarafından yoksayılan bir öğe içinde içeriğin sürekli işlenmesini gerektirmek için, [mc: ProcessContent özniteliği](mc-processcontent-attribute.md)ek özniteliğini belirtebilirsiniz.  
  
 Bir veya daha fazla boşluk karakteri ayırıcı olarak kullanılarak özniteliğinde birden çok önek belirtilebilir, örneğin: `mc:Ignorable="ignore1 ignore2"`.  

 Ad alanı, [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]öğesinin bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar. [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze Özniteliği](presentationoptions-freeze-attribute.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
