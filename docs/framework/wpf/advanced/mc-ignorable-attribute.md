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
ms.openlocfilehash: d8fdeec8784c9a44c9b272a0a5a8b9c56ace5230
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458824"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable Özniteliği
Biçimlendirme dosyasında karşılaşılan [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı öneklerinin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından yoksayılacağını belirtir. `mc:Ignorable` özniteliği, hem özel ad alanı eşlemesi hem de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sürümü oluşturma için biçimlendirme uyumluluğunu destekler.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>XAML öznitelik kullanımı (tek ön ek)  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>XAML öznitelik kullanımı (Iki ön ek)  
  
```xaml  
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
|*Thiselementcanbeyoksayıldı*|Temel alınan tür çözümlenemiyorsa, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işlemci uygulamaları tarafından yoksayılabilir bir öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ad alanı ön eki, `http://schemas.openxmlformats.org/markup-compatibility/2006`[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uyumluluğu ad alanını eşlerken kullanılması önerilen ön ek kuralıdır.  
  
 Öğe adının önek kısmının `mc:Ignorable`, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi tarafından işlendiğinde hata oluşturmaz. Bu öznitelik, temel alınan bir tür veya programlama yapısına çözümlenemiyorsa, bu öğe yok sayılır. Ancak yoksayılan öğelerin, bu öğenin işlenmediği yan etkileri olan ek öğe gereksinimleri için ek ayrıştırma hataları ürettiğine de devam edebileceğine unutmayın. Örneğin, belirli bir öğe içerik modeli tam olarak bir alt öğe gerektirebilir, ancak belirtilen alt öğe bir `mc:Ignorable` ön eki ise ve belirtilen alt öğe bir tür olarak çözülemezse, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi bir hata oluşturabilir.  
  
 `mc:Ignorable` yalnızca tanımlayıcı dizelerine ad alanı eşlemeleri için geçerlidir. `mc:Ignorable`, bir CLR ad alanı ve derleme (veya varsayılan olarak geçerli yürütülebilir dosya için derleme) belirten derlemelerdeki ad alanı eşlemeleri için geçerli değildir.  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemciyi uygularsınız, işlemci uygulamanız, `mc:Ignorable`olarak tanımlanan bir ön ek tarafından nitelenen herhangi bir öğe veya öznitelik için tür çözünürlüğünde ayrıştırma veya işleme hatalarını yükseltmemelidir. Ancak işlemci uygulamanız, daha önce verilen tek alt öğe örneği gibi, yükleme veya işleme başarısız olan bir öğenin ikincil sonucu olan özel durumları yine de oluşturabilir.  
  
 Varsayılan olarak, bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işlemcisi yoksayılan bir öğe içindeki içeriği yoksayar. Ancak, bir sonraki kullanılabilir üst öğe tarafından yoksayılan bir öğe içinde içeriğin sürekli işlenmesini gerektirmek için, [mc: ProcessContent özniteliği](mc-processcontent-attribute.md)ek özniteliğini belirtebilirsiniz.  
  
 Bir veya daha fazla boşluk karakteri ayırıcı olarak kullanılarak özniteliğinde birden çok önek belirtilebilir, örneğin: `mc:Ignorable="ignore1 ignore2"`.  

 `http://schemas.openxmlformats.org/markup-compatibility/2006` ad alanı, SDK 'nın bu alanı içinde belgelenmeyen diğer öğeleri ve öznitelikleri tanımlar. Daha fazla bilgi için bkz. [XML biçimlendirme uyumluluğu belirtimi](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze Özniteliği](presentationoptions-freeze-attribute.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
