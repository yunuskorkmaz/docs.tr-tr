---
title: "Otomatik Düzen Kullanımına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c9f5b9a6665778bc313febb039aeeeb2e484a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="use-automatic-layout-overview"></a>Otomatik Düzen Kullanımına Genel Bakış
Bu konu yazma konusunda geliştiricilere yönelik yönergeleri tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yerelleştirilebilir uygulamalarla [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. Geçmişte, yerelleştirme bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uzun süren bir işlem. Her dil, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] piksel piksel ayarlama gerekli uyarlanmıştır. Bugün doğru tasarım ve doğru kodlama standartları ile [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] çevirmenler küçük yapmak için yeniden konumlandırma ve yeniden boyutlandırma böylece oluşturulabilir. Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımına otomatik düzeni olarak adlandırılır ve kullanarak elde edilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tasarımı.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Otomatik düzeni kullanmanın yararları  
 Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sunum sistemi güçlü ve esnek, farklı diller gereksinimlerine uyacak şekilde ayarlanmış bir uygulamada düzen öğelerini olanağı sağlar. Aşağıdaki listede bazı otomatik düzen avantajları işaret eder.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]herhangi bir dilde de görüntüler.  
  
-   Metin çevrilen sonra konum ve boyut denetimlerini yeniden ayarlama gereksinimini azaltır.  
  
-   Pencere boyutunu yeniden ayarlama gereksinimini azaltır.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]düzeni herhangi bir dilde düzgün bir şekilde işler.  
  
-   Yerelleştirme, dize çeviri biraz daha fazla noktasına azaltılabilir.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Otomatik Düzen ve denetimler  
 Otomatik Düzen denetimin boyutunu otomatik olarak ayarlamak bir uygulama sağlar. Örneğin, bir denetim bir dizenin uzunluğunu uyacak şekilde değiştirebilirsiniz. Bu özellik dize çevirmek çevirmenler sağlar; artık denetimi çevrilmiş metnin sığması için yeniden boyutlandırmak ihtiyaç duyar. Aşağıdaki örnek İngilizce içerikli bir düğme oluşturur.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 Örnekte, İspanyolca düğme sağlamak için yapmanız gereken tek şey metni değiştirin. Örneğin,  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte kod örnekleri çıktısını gösterir.  
  
 ![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Otomatik yeniden boyutlandırılabilir düğmesi  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Otomatik Düzen ve kodlama standartları  
 Otomatik düzen yaklaşımı kullanılması kodlama ve tasarımın standartları ve tam olarak yerelleştirilebilir üretmek için kurallar kümesi [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki yönergeler, otomatik düzen kodlamanıza yardımcı olur.  
  
|Kodlama standartları|Açıklama|  
|----------------------|-----------------|  
|Mutlak Konumlar kullanmayın.|-Kullanmayın <xref:System.Windows.Controls.Canvas> çünkü öğeleri mutlak konumlandırır.<br />-Kullanın <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, ve <xref:System.Windows.Controls.Grid> denetimleri konumlandırmak için.<br />-Bir hakkında tartışma için çeşitli türlerde panolar, bkz: [paneller genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).|  
|Bir pencere için sabit bir boyut ayarlamayın.|-Kullanın <xref:System.Windows.Window.SizeToContent%2A>.<br />-Örneğin:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A>.|<ul><li>Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A> , uygulamanızın kök öğesi için.</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Yatay desteklemek için kullanışlı bir yol, çift yönlü ve dikey düzenleri sağlar. Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü modelleri şunlardır:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight>(LrTb) — Latin, Doğu Asya ve benzeri için yatay düzen.</li><li><xref:System.Windows.FlowDirection.RightToLeft>(RlTb) — Arapça, İbranice ve benzeri için çift yönlü.</li></ul></li></ul>|  
|Bileşik yazı tiplerini yerine fiziksel yazı tipleri kullanın.|<ul><li>Bileşik yazı tipleriyle <xref:System.Windows.Controls.Control.FontFamily%2A> özellik yerelleştirilmesi gerekmez.</li><li>Geliştiriciler, aşağıdaki yazı tipleri kullanın veya kendi oluşturun.<br /><br /> <ul><li>Genel kullanıcı arabirimi</li><li>Genel San Serif</li><li>Genel Serif</li></ul></li></ul>|  
|XML: lang ekleyin.|-Add `xml:lang` kök öğesinin özniteliğinde, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], gibi `xml:lang="en-US"` İngilizce bir uygulama için.<br />-Bileşik yazı tipleri kullandığından `xml:lang` hangi yazı tipinin kullanılacağını belirlemek için çok dilli senaryoları desteklemek için bu özelliği ayarlayın.|  
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Otomatik Düzen ve Kılavuzlar  
 <xref:System.Windows.Controls.Grid> Öğeleri yerleştirmek bir geliştirici sağladığından öğesi, otomatik yerleşim için yararlıdır. A <xref:System.Windows.Controls.Grid> denetimi bir sütun ve satır düzenlemesini kullanarak, kendi alt öğeleri arasında kullanılabilir alanı dağıtma özelliğine sahiptir. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğeleri birden çok hücreyi yayılabilir ve Kılavuzlar içinde kılavuzların olması mümkündür. Oluşturma ve karmaşık konumlandırmak etkinleştirmek için kılavuzları yararlı [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki örnek, bazı düğmeler ve metin konumlandırmak için kılavuz kullanmayı gösterir. Hücrelerin genişliği ve yüksekliği ayarlanır bildirimi <xref:System.Windows.GridUnitType.Auto>; bu nedenle, bir görüntü ile düğmeyi içeren hücre Resmi sığacak şekilde ayarlanır.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte önceki kod tarafından üretilen Kılavuzu gösterir.  
  
 ![Kılavuz örnek](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Kılavuz  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Otomatik Düzen ve Kılavuzlar IsSharedSizeScope özelliğini kullanma  
 A <xref:System.Windows.Controls.Grid> öğesi içeriğin sığması için ayarlama denetimleri oluşturmak için yerelleştirilebilir uygulamalarda yararlıdır. Ancak, bazen içerik bakmaksızın belirli bir boyutu korumak için denetimleri istediğiniz. Örneğin, "Tamam" varsa, "İptal" ve "Gözat" düğmelerine içeriğin sığması için boyutta düğmeleri büyük olasılıkla istemezsiniz. Bu durumda <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> ekli özellik birden çok kılavuz öğesi arasında aynı boyutlandırmayı paylaşım için yararlıdır. Aşağıdaki örnek, sütun ve satır birden çok arasında veri boyutlandırma paylaşmak gösterilmiştir <xref:System.Windows.Controls.Grid> öğeleri.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Not** tam kod örneği için bkz: [arasındaki paylaşım boyutlandırma özellikleri kılavuzları](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Bir düğme oluşturmak için otomatik düzenini kullanın](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Bir kılavuz için otomatik düzenini kullanın](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
