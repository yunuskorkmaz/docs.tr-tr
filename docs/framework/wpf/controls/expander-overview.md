---
title: Genişleticiye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 29003779825b92402fa12b810c1a099731ac8af6
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409464"
---
# <a name="expander-overview"></a>Genişleticiye Genel Bakış
Bir <xref:System.Windows.Controls.Expander> denetim bir pencere benzer ve üst bilgi içeren genişletilebilir bir alanda içerik sağlamak için bir yol sağlar.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Basit bir Genişletici Oluşturma  
 Aşağıdaki örnek, basit bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.Expander> denetimi. Bu örnekte bir <xref:System.Windows.Controls.Expander> önceki çizim gibi görünüyor.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Ve <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> , bir <xref:System.Windows.Controls.Expander> karmaşık içerik gibi de içerebilen <xref:System.Windows.Controls.RadioButton> ve <xref:System.Windows.Controls.Image> nesneleri.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Genişleyen bir içerik alanı yönü ayarlama  
 Pencerenin içerik alanı ayarlayabileceğiniz bir <xref:System.Windows.Controls.Expander> dört yönergeleri birini genişletmek için denetim (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, veya <xref:System.Windows.Controls.ExpandDirection.Right>) kullanarak <xref:System.Windows.Controls.ExpandDirection> özelliği. Ne zaman içerik alanı daraltıldığında, yalnızca <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve iki durumlu düğmesi görünür. A <xref:System.Windows.Controls.Button> tek yönlü bir ok görüntüler denetimi, içerik alanını genişletmek veya daraltmak için iki durumlu düğme olarak kullanılır. Genişletildiğinde, <xref:System.Windows.Controls.Expander> penceresi gibi bir alanda içeriğini görüntülemek çalışır.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Bir Panel içinde bir genişletici boyutunu denetleme  
 Varsa bir <xref:System.Windows.Controls.Expander> denetimidir devralan bir düzen denetimi içinde <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.StackPanel>, belirtmeyin bir <xref:System.Windows.FrameworkElement.Height%2A> üzerinde <xref:System.Windows.Controls.Expander> olduğunda <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği <xref:System.Windows.Controls.ExpandDirection.Down> veya <xref:System.Windows.Controls.ExpandDirection.Up>. Benzer şekilde, belirtmeyin bir <xref:System.Windows.FrameworkElement.Width%2A> üzerinde <xref:System.Windows.Controls.Expander> olduğunda <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği <xref:System.Windows.Controls.ExpandDirection.Left> veya <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Şirket boyutu boyut ayarlarsanız bir <xref:System.Windows.Controls.Expander> genişletilmiş içeriği görüntülendiğini yönü denetiminde <xref:System.Windows.Controls.Expander> içerik tarafından kullanılan ve bir kenarlık görüntüler alanı denetimi gerçekleştirir. İçerik daraltıldığında bile kenarlık gösterilmektedir. Genişletilmiş içerik alanı boyutunu ayarlamak için boyut özellikleri içeriğine ayarlayın <xref:System.Windows.Controls.Expander>, veya üzerinde kaydırma yeteneği, isterseniz <xref:System.Windows.Controls.ScrollViewer> , içeriği alır.  
  
 Olduğunda bir <xref:System.Windows.Controls.Expander> denetimidir içindeki son öğeden bir <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] otomatik olarak ayarlar <xref:System.Windows.Controls.Expander> kalan alanı eşit boyutları <xref:System.Windows.Controls.DockPanel>. Bu varsayılan davranışı önleyecek şekilde ayarlanmış <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliği <xref:System.Windows.Controls.DockPanel> nesnesini `false`, veya emin olun <xref:System.Windows.Controls.Expander> içindeki son öğeden değil bir <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Kaydırılabilir içeriği oluşturma  
 İçerik için içerik alanı boyutu çok büyük ise, içeriği kaydırılabilir bir <xref:System.Windows.Controls.Expander> içinde bir <xref:System.Windows.Controls.ScrollViewer> kaydırılabilir içerik sağlamak için. <xref:System.Windows.Controls.Expander> Denetimi otomatik olarak kaydırma özelliği sağlamaz. Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.Expander> içeren denetimi bir <xref:System.Windows.Controls.ScrollViewer> denetimi.  
  
 **ScrollViewer içinde Genişleticisi**  
  
 ![Kaydırma çubuğu ile bir genişletici gösteren ekran görüntüsü.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Yerleştirdiğinizde bir <xref:System.Windows.Controls.Expander> denetimine bir <xref:System.Windows.Controls.ScrollViewer>ayarlayın <xref:System.Windows.Controls.ScrollViewer> boyut hangi yönde karşılık gelen özellik <xref:System.Windows.Controls.Expander> içeriği açılır boyutuna <xref:System.Windows.Controls.Expander> içerik alanı. Örneğin ayarlarsanız, <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği <xref:System.Windows.Controls.Expander> için <xref:System.Windows.Controls.ExpandDirection.Down> (içerik alanı açılır) ayarlama <xref:System.Windows.FrameworkElement.Height%2A> özelliği <xref:System.Windows.Controls.ScrollViewer> içerik alanı gerekli yüksekliğe denetimi. Yükseklik boyutu içeriğin kendisi, bunun yerine ayarlarsanız <xref:System.Windows.Controls.ScrollViewer> Bu ayar tanımıyor ve bu nedenle, kaydırılabilir içeriği sağlamaz.  
  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Controls.Expander> karmaşık içerik olan ve içeren denetimini bir <xref:System.Windows.Controls.ScrollViewer> denetimi. Bu örnekte bir <xref:System.Windows.Controls.Expander> bu bölümün başında çizim gibi olmasıdır.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Hizalama özelliklerini kullanma  
 İçerik ayarlayarak hizalayabilirsiniz <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özellikleri <xref:System.Windows.Controls.Expander> denetimi. Bu özellikleri ayarlama, üst bilgi ve genişletilmiş içeriği hizalaması geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Nasıl Yapılır Konuları](expander-how-to-topics.md)
