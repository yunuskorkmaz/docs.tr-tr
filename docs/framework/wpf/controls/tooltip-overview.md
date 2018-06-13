---
title: ToolTip Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: b70387e604b0917d154fc056b904e9ee05f6fbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557244"
---
# <a name="tooltip-overview"></a>ToolTip Genel Bakışı
Bir kullanıcı bir öğe üzerinde gibi üzerinde fare işaretçisini durduğu zaman görüntülenen küçük bir açılır pencere bir araç ipucu olan bir <xref:System.Windows.Controls.Button>. Bu konu, araç ipucu tanıtır ve nasıl oluşturulacağı ve araç ipucu içeriğini özelleştirmek açıklanır.  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Bir araç ipucu nedir?  
 Bir kullanıcı bir araç ipucu olan bir öğeyi fare işaretçisini geçtiğinde, belirtilen bir süre için araç ipucu içeriği (bir denetim işlevini açıklayan Örneğin, metin içeriği) içeren bir pencere görüntülenir. Kullanıcı denetimi fare işaretçisini geçerse, araç ipucu içeriği odak aldıklarından pencere kaybolur.  
  
 İçeriği bir araç ipucu, bir veya birkaç satırlık metin, görüntüler, şekiller veya diğer görsel içerik içerebilir. Araç ipucu içeriği ayarlayarak bir denetim aşağıdaki özelliklerden biri için bir araç ipucu tanımlayın.  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Hangi özelliği kullandığınız bağlı olup olmadığını tanımlar araç ipucu denetimi devraldığı üzerinde <xref:System.Windows.FrameworkContentElement> veya <xref:System.Windows.FrameworkElement> sınıfı.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Araç ipucu oluşturma  
 Aşağıdaki örnek ayarlayarak basit bir araç ipucu oluşturulacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği için bir <xref:System.Windows.Controls.Button> denetlemek için bir metin dizesi.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Araç İpucu olarak da tanımlayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> nesnesi. Aşağıdaki örnek kullanır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtmek için bir <xref:System.Windows.Controls.ToolTip> nesnesi araç ipucu olarak bir <xref:System.Windows.Controls.TextBox> öğesi. Örnek belirtir Not <xref:System.Windows.Controls.ToolTip> ayarlayarak <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Aşağıdaki örnek kod oluşturmak için kullanılır. bir <xref:System.Windows.Controls.ToolTip> nesnesi. Örnekte bir <xref:System.Windows.Controls.ToolTip> (`tt`) ve ile ilişkilendirir bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Ayrıca olarak tanımlanmamış araç ipucu içeriği oluşturabilirsiniz bir <xref:System.Windows.Controls.ToolTip> gibi bir düzen öğesi içinde araç ipucu içeriği kapsayan nesne bir <xref:System.Windows.Controls.DockPanel>. Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir <xref:System.Windows.Controls.TextBox> sınırlanan içerik için bir <xref:System.Windows.Controls.DockPanel> denetim.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Araç ipucu ve araç ipucu servisi sınıflarının özelliklerini kullanma  
 Araç ipucu içeriği görsel özelliklerini ayarlamaktan ve stiller uygulayarak özelleştirebilirsiniz. Araç İpucu olarak içeriği tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesne görsel özelliklerini ayarlayabilirsiniz <xref:System.Windows.Controls.ToolTip> nesnesi. Aksi takdirde, eşdeğer ekli özellikler üzerinde ayarlamanız gerekir <xref:System.Windows.Controls.ToolTipService> sınıfı.  
  
 Kullanarak araç ipucu içeriğinin konumunu belirtmek için özelliklerini ayarlamak nasıl bir örnek için <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> özellikleri, görmek [bir araç ipucu, konum](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Bir araç ipucu stil oluşturma  
 Stil ekleyebilirsiniz bir <xref:System.Windows.Controls.ToolTip> özel tanımlayarak <xref:System.Windows.Style>. Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Style> adlı `Simple` nasıl yerleşimini uzaklığı gösterir <xref:System.Windows.Controls.ToolTip> ve ayarlayarak görünümünü değiştirme <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Araç İpucu servisi zaman aralığı özelliklerini kullanma  
 <xref:System.Windows.Controls.ToolTipService> Sınıfı sağlar, araç ipucu ayarlamak aşağıdaki özellikleri görüntüleme zamanlarını: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Kullanım <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> bir gecikme belirtmek için özellikleri önce genellikle kısa bir <xref:System.Windows.Controls.ToolTip> görünür ve ayrıca ne kadar süreyle belirtmek için bir <xref:System.Windows.Controls.ToolTip> görünür kalır. Daha fazla bilgi için bkz: [nasıl yapılır: araç ipucu görüntüsünü gecikme](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özelliği, fare işaretçisini hızla arasında taşıdığınızda farklı denetimler için araç ipuçları ilk gecikme olmadan görünür olmadığını belirler. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> özelliği, bkz: [BetweenShowDelay özelliğini kullanma](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).  
  
 Aşağıdaki örnek, bir araç ipucu için bu özelliklerin nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
