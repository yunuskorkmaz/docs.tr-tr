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
ms.openlocfilehash: abcc7c48c602aee742959b39bb5244563eaf4d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557595"
---
# <a name="expander-overview"></a>Genişleticiye Genel Bakış
Bir <xref:System.Windows.Controls.Expander> denetimi pencere benzeyen ve üst bilgi içeren genişletilebilir bir alanda içerik sağlamak için bir yol sağlar.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Basit bir Genişletici Oluşturma  
 Aşağıdaki örnekte basit bir oluşturulacağını gösterir <xref:System.Windows.Controls.Expander> denetim. Bu örnekte bir <xref:System.Windows.Controls.Expander> önceki resimde gibi görünüyor.  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> Ve <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> , bir <xref:System.Windows.Controls.Expander> de karmaşık içerik gibi içerebilir <xref:System.Windows.Controls.RadioButton> ve <xref:System.Windows.Controls.Image> nesneleri.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Genişleyen içerik alanının yönünü ayarlama  
 İçerik alanına ayarlayabileceğiniz bir <xref:System.Windows.Controls.Expander> dört yönden birinde genişletmek için denetim (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, veya <xref:System.Windows.Controls.ExpandDirection.Right>) kullanarak <xref:System.Windows.Controls.ExpandDirection> özelliği. Ne zaman içerik alanı daraltıldığında, yalnızca <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve iki durumlu düğmesi görünür. A <xref:System.Windows.Controls.Button> yönlü oku görüntüleyen denetimi iki durumlu düğme olarak içerik alanını genişletmek veya daraltmak için kullanılır. Genişletilmiş olduğunda <xref:System.Windows.Controls.Expander> tüm içeriği pencerede gibi alanında görüntülemek çalışır.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Bir Genişletici paneldeki boyutunu denetleme  
 Varsa bir <xref:System.Windows.Controls.Expander> denetimidir öğesinden devralınan düzen denetimi içinde <xref:System.Windows.Controls.Panel>, gibi <xref:System.Windows.Controls.StackPanel>, belirtmeyin bir <xref:System.Windows.FrameworkElement.Height%2A> üzerinde <xref:System.Windows.Controls.Expander> zaman <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği ayarlanmış <xref:System.Windows.Controls.ExpandDirection.Down> veya <xref:System.Windows.Controls.ExpandDirection.Up>. Benzer şekilde, belirtmeyin bir <xref:System.Windows.FrameworkElement.Width%2A> üzerinde <xref:System.Windows.Controls.Expander> zaman <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği ayarlanmış <xref:System.Windows.Controls.ExpandDirection.Left> veya <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Üzerinde bir boyutu boyut ayarlandığında bir <xref:System.Windows.Controls.Expander> denetimi genişletilmiş içeriği görüntülenen yönde <xref:System.Windows.Controls.Expander> içerik tarafından kullanılır ve çevresinde kenarlık görüntüler alanı denetimini alır. İçerik daraltıldığında bile kenarlık gösterir. Genişletilmiş içerik alanının boyutunu ayarlamak için belirtilmiş boyutu içeriğine ayarlayın <xref:System.Windows.Controls.Expander>, veya üzerinde kaydırma yeteneği, istiyorsanız <xref:System.Windows.Controls.ScrollViewer> içeriği alır.  
  
 Zaman bir <xref:System.Windows.Controls.Expander> denetimidir son öğesi bir <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] otomatik olarak ayarlar <xref:System.Windows.Controls.Expander> kalan alanı eşit boyutları <xref:System.Windows.Controls.DockPanel>. Bu varsayılan davranışı önlemek için ayarlayın <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> özelliği <xref:System.Windows.Controls.DockPanel> nesnesini `false`, ya da emin olun <xref:System.Windows.Controls.Expander> son öğesi değil bir <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Kaydırılabilir içerik oluşturma  
 İçerik için içerik alanının boyutu çok büyük ise içeriğini kayabilir bir <xref:System.Windows.Controls.Expander> içinde bir <xref:System.Windows.Controls.ScrollViewer> kaydırılabilir içeriği sağlamak için. <xref:System.Windows.Controls.Expander> Denetimi otomatik olarak kaydırma yeteneği sağlamaz. Aşağıdaki çizimde gösterildiği bir <xref:System.Windows.Controls.Expander> içeren denetimi bir <xref:System.Windows.Controls.ScrollViewer> denetim.  
  
 **ScrollViewer'da**  
  
 ![ScrollBar bulunan genişletici](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Yerleştirdiğinizde bir <xref:System.Windows.Controls.Expander> denetim bir <xref:System.Windows.Controls.ScrollViewer>ayarlayın <xref:System.Windows.Controls.ScrollViewer> boyut hangi yönde karşılık gelen özellik <xref:System.Windows.Controls.Expander> içeriği açar boyutuna <xref:System.Windows.Controls.Expander> içerik alanının. Örneğin ayarlarsanız <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği <xref:System.Windows.Controls.Expander> için <xref:System.Windows.Controls.ExpandDirection.Down> (içerik alanı açılır) ayarlamak <xref:System.Windows.FrameworkElement.Height%2A> özellikte <xref:System.Windows.Controls.ScrollViewer> içerik alanı için gerekli olan yüksekliğe denetimine. Yükseklik boyutu içeriğin kendisini, bunun yerine ayarlarsanız <xref:System.Windows.Controls.ScrollViewer> Bu ayar tanımıyor ve bu nedenle, kaydırılabilir içeriği sağlamaz.  
  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Controls.Expander> , karmaşık içeriğe sahip ve içeren denetimini bir <xref:System.Windows.Controls.ScrollViewer> denetim. Bu örnekte bir <xref:System.Windows.Controls.Expander> , bu bölümün başındaki çizim gibi olmasıdır.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Hizalama özelliklerini kullanma  
 Ayarlayarak içeriği hizalamak <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> ve <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özellikleri <xref:System.Windows.Controls.Expander> denetim. Bu özellikleri ayarladığınızda hizalama üstbilgi ve genişletilmiş içeriği uygulanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
