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
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181944"
---
# <a name="tooltip-overview"></a>ToolTip Genel Bakışı
Araç ipucu, kullanıcı fare işaretçisini bir öğenin üzerinde duraklattığında görünen küçük bir <xref:System.Windows.Controls.Button>açılır penceredir. Bu konu araç ucunu tanıtır ve araç ipucu içeriğinin nasıl oluşturulup özelleştirilebildiğini tartışır.  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>Araç İpucu Nedir?  
 Bir kullanıcı fare işaretçisini araç ipucu olan bir öğenin üzerine taşırsa, araç ipucu içeriği (örneğin, denetimin işlevini açıklayan metin içeriği) içeren bir pencere belirli bir süre için görüntülenir. Kullanıcı fare işaretçisini denetimden uzağa taşırsa, araç ipucu içeriği netleme alamadığı için pencere kaybolur.  
  
 Araç ucunun içeriği bir veya daha fazla metin, resim, şekil veya diğer görsel içerik satırı içerebilir. Aşağıdaki özelliklerden birini araç ipucu içeriğine ayarlayarak denetim için bir araç ipucu tanımlarsınız.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 Hangi özelliği kullandığınız, araç ucunu tanımlayan denetimin sınıftan <xref:System.Windows.FrameworkContentElement> mı <xref:System.Windows.FrameworkElement> devraldığına bağlıdır.  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>Araç İpucu Oluşturma  
 Aşağıdaki örnekte, bir denetim için <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir metin <xref:System.Windows.Controls.Button> dizesine ayarlayarak basit bir araç ipucunasıl oluşturulacak gösterilmektedir.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Araç ucunu <xref:System.Windows.Controls.ToolTip> nesne olarak da tanımlayabilirsiniz. Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir <xref:System.Windows.Controls.ToolTip> öğeyi bir <xref:System.Windows.Controls.TextBox> öğenin araç ucu olarak belirtmek için kullanır. Örneğin <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği ayarlayarak belirtir unutmayın.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 Aşağıdaki örnekte bir <xref:System.Windows.Controls.ToolTip> nesne oluşturmak için kod kullanır. Örnek a <xref:System.Windows.Controls.ToolTip> oluşturur`tt`( ) ve <xref:System.Windows.Controls.Button>bir ile ilişkilendirer .  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Ayrıca, araç ipucu içeriğini bir düzen <xref:System.Windows.Controls.ToolTip> öğesine ekleyerek nesne olarak tanımlanmayan araç ipucu <xref:System.Windows.Controls.DockPanel>içeriği de oluşturabilirsiniz. Aşağıdaki örnek, denetimle <xref:System.Windows.FrameworkElement.ToolTip%2A> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.DockPanel> kapatılan bir içeriğe nasıl ayarlanılmayı gösterir.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Araç İpucu ve ToolTipService Sınıflarının Özelliklerini Kullanma  
 Görsel özellikler ayarlayarak ve stilleri uygulayarak araç ipucu içeriğini özelleştirebilirsiniz. Araç ipucu içeriğini bir <xref:System.Windows.Controls.ToolTip> nesne olarak tanımlarsanız, nesnenin <xref:System.Windows.Controls.ToolTip> görsel özelliklerini ayarlayabilirsiniz. Aksi takdirde, <xref:System.Windows.Controls.ToolTipService> sınıf üzerinde eşdeğer ekli özellikleri ayarlamanız gerekir.  
  
 Özellikleri ve <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> özelliklerini kullanarak araç ipucu içeriğinin konumunu belirtmek için özellikleri nasıl ayarlayalanın bir örneği için, bir Araç İpucu [Konumlandır'a](how-to-position-a-tooltip.md)bakın.  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>Araç İpucu Oluşturma  
 Bir özel <xref:System.Windows.Style> <xref:System.Windows.Controls.ToolTip> tanımlayarak a stili yapabilirsiniz. Aşağıdaki <xref:System.Windows.Style> örnek, `Simple` yerleşiminnasıl dengeleneceğini <xref:System.Windows.Controls.ToolTip> gösteren ve <xref:System.Windows.Controls.Control.Background%2A>, , <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>ve <xref:System.Windows.Controls.Control.FontWeight%2A>.  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>ToolTipService'in Zaman Aralığı Özelliklerini Kullanma  
 <xref:System.Windows.Controls.ToolTipService> Sınıf, araç ucu görüntüleme sürelerini ayarlamanız <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>aşağıdaki <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>özellikleri sağlar: , ve .  
  
 Bir görünmeden önce <xref:System.Windows.Controls.ToolTip> genellikle kısa bir gecikme belirtmek ve ayrıca ne <xref:System.Windows.Controls.ToolTip> kadar süre görünür kaldığını belirtmek için ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> özellikleri kullanın. <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> Daha fazla bilgi için [bkz: Araç İpucunun Görüntülenmesini Geciktirin.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))  
  
 Özellik, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> fare işaretçisini aralarında hızlı bir şekilde hareket ettirdiğinizde, farklı denetimler için araç uçlarının ilk gecikme olmadan görünip görünmeyecektir belirler. <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özellik hakkında daha fazla bilgi için Bkz. [BetweenShowDelay Özelliği'ni kullanın.](how-to-use-the-betweenshowdelay-property.md)  
  
 Aşağıdaki örnekte, bu özelliklerin bir araç ipucu için nasıl ayarlanılabildiğini gösterilmektedir.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Nasıl Dır Konular](tooltip-how-to-topics.md)
