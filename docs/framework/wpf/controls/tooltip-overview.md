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
ms.openlocfilehash: 08b30d8be83ef9d814d17c5d4ec0c95a26bacdad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790734"
---
# <a name="tooltip-overview"></a>ToolTip Genel Bakışı
Kullanıcı fare işaretçisini bir öğenin üzerinden, gibi üzerinde durakladığında görüntülenen küçük bir açılır pencere bir araç ipucu olan bir <xref:System.Windows.Controls.Button>. Bu konu, araç ipucu tanıtır ve oluşturmak ve araç ipucu içeriğini özelleştirmek nasıl açıklar.  

<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>Bir araç ipucu nedir?  
 Bir kullanıcı bir araç ipucu sahip bir öğe üzerinde fare işaretçisi hareket ettirdiğinde belirtilen bir zaman miktarı için araç ipucu içeriği (bir denetimin işlevi tanımlayan Örneğin, metin içeriğini) içeren bir pencere görüntülenir. Kullanıcı, fare işaretçisini denetim taşınırsa, araç ipucu içerik odak kazandığı penceresi kaybolur.  
  
 İçeriği bir araç ipucu, metin, resimler, şekiller veya diğer görsel içerik bir veya daha fazla satır içerebilir. Araç ipucu içeriği ayarlayarak bir denetimin aşağıdaki özelliklerden biri için bir araç ipucu tanımlarsınız.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Kullandığınız hangi özelliğinin bağlı olup olmadığını tanımlar araç ipucu denetimi devraldığı üzerinde <xref:System.Windows.FrameworkContentElement> veya <xref:System.Windows.FrameworkElement> sınıfı.  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>Araç ipucu oluşturma  
 Aşağıdaki örnek, basit bir araç ipucu ayarlayarak oluşturma işlemi gösterilmektedir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği için bir <xref:System.Windows.Controls.Button> denetimine bir metin dizesi.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Ayrıca, araç ipucu olarak tanımlayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> nesne. Aşağıdaki örnekte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtmek için bir <xref:System.Windows.Controls.ToolTip> nesnesi araç ipucu olarak bir <xref:System.Windows.Controls.TextBox> öğesi. Örnek belirten Not <xref:System.Windows.Controls.ToolTip> ayarlayarak <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Aşağıdaki örnek kod üretmek için kullanır. bir <xref:System.Windows.Controls.ToolTip> nesne. Örnek bir <xref:System.Windows.Controls.ToolTip> (`tt`) ve onunla ilişkilendirir bir <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Tanımlanmamış araç ipucu içeriği de oluşturabileceğiniz bir <xref:System.Windows.Controls.ToolTip> araç ipucu içeriği gibi bir düzen öğesi içinde kapsayan nesne bir <xref:System.Windows.Controls.DockPanel>. Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir <xref:System.Windows.Controls.TextBox> sınırlanan içerik için bir <xref:System.Windows.Controls.DockPanel> denetimi.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Araç ipucu ve araç ipucu servisi sınıflarının özelliklerini kullanma  
 Araç ipucu içeriği, görsel özelliklerini ayarlamaktan ve stilleri uygulayarak özelleştirebilirsiniz. Araç İpucu olarak içerik tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesne görsel özelliklerini ayarlayabileceğiniz <xref:System.Windows.Controls.ToolTip> nesne. Aksi takdirde, üzerinde eşdeğer iliştirilmiş özellikler ayarlamalısınız <xref:System.Windows.Controls.ToolTipService> sınıfı.  
  
 Kullanarak araç ipucu içeriğinin konumunu belirtmek için özellikleri ayarlama örneği için <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> özellikleri görmek [ToolTip konumlandırma](how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>Bir araç ipucu stil oluşturma  
 Stil uygulayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> özel tanımlayarak <xref:System.Windows.Style>. Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Style> adlı `Simple` nasıl yerleşimini uzaklığı gösteren <xref:System.Windows.Controls.ToolTip> ve ayarlayarak görünümünü değiştirmek <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Araç İpucu servisinin zaman aralığı özelliklerini kullanma  
 <xref:System.Windows.Controls.ToolTipService> Sınıfı görüntüleme zamanlarını araç ipucu ayarlamak aşağıdaki özellikleri sağlar: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.  
  
 Kullanım <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> bir gecikme belirtmek için özellikleri önce genellikle kısa bir <xref:System.Windows.Controls.ToolTip> görünür ve ayrıca ne kadar süreyle belirtmek için bir <xref:System.Windows.Controls.ToolTip> görünür kalır. Daha fazla bilgi için [nasıl yapılır: Bir araç ipucu görüntülenmesini geciktirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özelliği, farklı denetimler için araç ipuçları, fare işaretçisini hızlı bir şekilde bunlar arasında taşıdığınızda ilk bir gecikme olmadan görüntülenip görüntülenmediğine belirler. Hakkında daha fazla bilgi için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> özelliğine bakın [BetweenShowDelay özelliğini kullanma](how-to-use-the-betweenshowdelay-property.md).  
  
 Aşağıdaki örnek, bir araç ipucu için bu özelliklerin nasıl ayarlanacağını gösterir.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Nasıl Yapılır Konuları](tooltip-how-to-topics.md)
