---
title: Otomatik Düzen Kullanımına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: a43b3c0e008025171e3b1fdeba3bc514d01e28c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542630"
---
# <a name="use-automatic-layout-overview"></a>Otomatik Düzen Kullanımına Genel Bakış
Bu konu nasıl yazılacağı konusunda geliştiriciler için yönergeler tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yerelleştirilebilir uygulamalarla [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. Geçmişte, yerelleştirme bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] uzun süren bir işlemi yükleyemedi. Her dil, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] piksel piksel ayarlaması gereken için de uyarlanmıştır. Doğru tasarıma ve doğru kodlama standartları ile Bugün [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] yerelleştiriciler yeniden boyutlandırma ve yeniden konumlandırma yapmak için daha az olması oluşturulabilir. Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamalar yazma yaklaşım otomatik düzen olarak adlandırılır ve kullanarak gerçekleştirilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tasarım.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Otomatik Düzen kullanmanın avantajları  
 Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sunumda güçlü ve esnek, farklı dillerde gereksinimlerine uyacak şekilde ayarlanmış bir uygulamada düzen öğelerini olanağı sağlar. Aşağıdaki liste bazı otomatik düzen avantajları işaret eder.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] herhangi bir dilde de görüntüler.  
  
-   Metin çevrildikten sonra konumunu ve boyutunu denetimleri yeniden ayarlama gereksinimini azaltır.  
  
-   Pencere boyutu yeniden ayarlama gereksinimini azaltır.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] düzeni, herhangi bir dilde düzgün bir şekilde işler.  
  
-   Yerelleştirme, dize çevirisinden biraz daha fazla noktasına azaltılabilir.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Otomatik Düzen ve denetimler  
 Otomatik Düzen bir denetimin boyutunu otomatik olarak ayarlamasına olanak sağlar. Örneğin, bir denetimi, bir dizenin uzunluğunu uyum sağlayacak şekilde değiştirebilirsiniz. Bu özellik, dize çevrilecek yerelleştiriciler sağlar; Bunlar artık çevrilmiş metin sığdırmak için yeniden boyutlandırma gerekir. Aşağıdaki örnek, bir düğme ile İngilizce içeriği oluşturur.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 Örnekte, İspanyolca bir düğme oluşturmak için yapmanız gereken tek şey metni değiştirme. Örneğin,  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte, kod örnekleri çıktısını gösterir.  
  
 ![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Otomatik yeniden boyutlandırılabilir düğmesi  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Otomatik Düzen ve kodlama standartları  
 Otomatik düzen yaklaşımı kullanarak, kodlama ve tasarımın standartlar ve tam olarak yerelleştirilebilir üretmek için kurallar kümesi gerektirir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki yönergeler, kodlamanızı otomatik düzen yardımcı olur.  
  
| Kodlama standartları | Açıklama |
| ---------------------- | ----------------- |
| Mutlak Konumlar kullanmayın. | <ul><li>Kullanmayın <xref:System.Windows.Controls.Canvas> çünkü öğeleri mutlak konumlandırır.</li><li>Kullanım <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, ve <xref:System.Windows.Controls.Grid> denetimleri konumlandırmak için.</li><li>Çeşitli türlerde panolar hakkında bir tartışma için bkz. [panellere genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</li></ul> |
| Bir pencere için sabit bir boyuta ayarlamayın. | -Kullanma <xref:System.Windows.Window.SizeToContent%2A>.<br />Örneğin:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)] |
| Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A>. | <ul><li>Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A> uygulamanızın kök öğesine.</li><li>WPF yatay desteklemek için kullanışlı bir yol, çift yönlü ve dikey düzeni sağlar. Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir. Akış yönü modelleri şunlardır:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight> (LrTb) — Latin, Doğu Asya ve benzeri için yatay düzeni.</li><li><xref:System.Windows.FlowDirection.RightToLeft> (RlTb): Arapça, İbranice ve benzeri için çift yönlü.</li></ul></li></ul> |
| Bileşik yazı tiplerini yerine fiziksel yazı tipleri kullanın. | <ul><li>Bileşik yazı tipleriyle <xref:System.Windows.Controls.Control.FontFamily%2A> özelliği yerelleştirilmiş gerekmez.</li><li>Geliştiriciler, aşağıdaki yazı tipleri kullanın veya kendi oluşturun.<br /><br /> <ul><li>Genel kullanıcı arabirimi</li><li>Genel San Serif</li><li>Genel Serif</li></ul></li></ul> |
| XML: lang ekleyin. | <ul><li>Ekleme `xml:lang` kök öğesi özniteliği, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], gibi `xml:lang="en-US"` İngilizce bir uygulama için.</li><li>Bileşik yazı tipleri kullandığından `xml:lang` hangi yazı tipinin kullanılacağını belirlemek için çok dilli senaryoları desteklemek için bu özelliği ayarlayın.</li></ul> |
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Otomatik Düzen ve Kılavuzlar  
 <xref:System.Windows.Controls.Grid> Öğeleri konumlandırmak bir geliştirici sağladığından öğesi, otomatik düzen için yararlıdır. A <xref:System.Windows.Controls.Grid> denetimidir kullanılabilir alan bir sütun ve satır düzenlemeyi kullanarak, kendi alt öğeleri arasında dağıtma özelliğine sahiptir. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Öğeleri birden çok hücre yayılabilir ve Kılavuzlar Kılavuzlar içinde olması mümkündür. Kılavuzlar, oluşturmayı ve karmaşık konumlandırmayı etkinleştirmek için kullanışlıdır [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Aşağıdaki örnek, bazı düğme ve metin konumlandırmak için bir kılavuz kullanmayı gösterir. Hücre genişliği ve yüksekliği ayarlandığından bildirimi <xref:System.Windows.GridUnitType.Auto>; bu nedenle, resim sığacak şekilde düğmesi bir görüntü içeren hücreye ayarlanır.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Aşağıdaki grafikte önceki kod tarafından üretilen kılavuz gösterir.  
  
 ![Grid örneği](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Kılavuz  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Otomatik Düzen ve Kılavuzlar IsSharedSizeScope özelliğini kullanma  
 A <xref:System.Windows.Controls.Grid> öğesi, içeriğin sığacağı şekilde ayarlama denetimler oluşturmak için yerelleştirilebilir uygulamalarda kullanışlıdır. Ancak, denetimlerin içeriği ne olursa olsun, belirli bir boyutu korumak için istediğiniz zaman zaman. Örneğin, "Tamam" varsa, "İptal" ve "düğmeleri İçeriği sığdırmak için büyük olasılıkla istemezsiniz düğmeleri göz at". Bu durumda <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> ekli özellik aynı boyutlandırma birden çok kılavuz öğesinin arasında paylaşmak için yararlıdır. Aşağıdaki örnek, sütun ve satır boyutlandırma birden çok arasında veri paylaşmayı gösterilmiştir <xref:System.Windows.Controls.Grid> öğeleri.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Not** tam kod örneği için bkz. [arasında boyutlandırma özelliklerini Kılavuzlar paylaşımı](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için Genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Düğme Oluşturmak için Otomatik Düzeni Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Otomatik Düzen için Kılavuz Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
