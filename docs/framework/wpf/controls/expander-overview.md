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
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187118"
---
# <a name="expander-overview"></a>Genişleticiye Genel Bakış
Denetim, <xref:System.Windows.Controls.Expander> pencereye benzeyen ve üstbilgi içeren genişletilebilir bir alanda içerik sağlamanın bir yolunu sağlar.  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>Basit Genişletici Oluşturma  
 Aşağıdaki örnek, basit <xref:System.Windows.Controls.Expander> bir denetimin nasıl oluşturulabildiğini gösterir. Bu örnek, <xref:System.Windows.Controls.Expander> önceki çizime benzeyen bir örnek oluşturur.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 Bir <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ve bir de karmaşık içerik <xref:System.Windows.Controls.RadioButton> içerebilir, gibi ve <xref:System.Windows.Controls.Image> nesneler.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Genişleyen İçerik Alanının Yönünü Ayarlama  
 Bir <xref:System.Windows.Controls.Expander> denetimin içerik alanını özelliği kullanarak<xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.Controls.ExpandDirection.Up> <xref:System.Windows.Controls.ExpandDirection.Left> <xref:System.Windows.Controls.ExpandDirection.Right> <xref:System.Windows.Controls.ExpandDirection> dört yönden birinde (, , , veya ) genişletecek şekilde ayarlayabilirsiniz. İçerik alanı daraltıldığında, yalnızca <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> geçiş düğmesi görüntülenir. İçerik <xref:System.Windows.Controls.Button> alanını genişletmek veya daraltmak için geçiş düğmesi olarak yön oku görüntüleyen bir denetim kullanılır. Genişletildiğinde, <xref:System.Windows.Controls.Expander> tüm içeriğini pencere benzeri bir alanda görüntülemeye çalışır.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Panelde Genişleticinin Boyutunu Denetleme  
 Denetim, <xref:System.Windows.Controls.Expander> devralan bir düzen denetiminin <xref:System.Windows.Controls.Panel>içindeyse, <xref:System.Windows.Controls.StackPanel>örneğin, <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliğin ayarlandığında <xref:System.Windows.Controls.ExpandDirection.Down> veya <xref:System.Windows.Controls.ExpandDirection.Up>. Benzer şekilde, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliğin ayarlandığında <xref:System.Windows.Controls.ExpandDirection.Left> veya <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Genişletilmiş içeriğin görüntülendiği <xref:System.Windows.Controls.Expander> yönde bir denetimüzerinde boyut boyutu ayarladığınızda, içerik tarafından kullanılan alanın denetimini <xref:System.Windows.Controls.Expander> alır ve çevresinde bir kenarlık görüntüler. Kenarlık, içerik daraltıldığında bile gösterir. Genişletilmiş içerik alanının boyutunu ayarlamak için, içeriğin <xref:System.Windows.Controls.Expander>içeriğine boyut boyutları ayarlayın veya içeriği <xref:System.Windows.Controls.ScrollViewer> içine alan içerikte kaydırma özelliği istiyorsanız.  
  
 <xref:System.Windows.Controls.Expander> Bir denetim, <xref:System.Windows.Controls.DockPanel>bir 'deki [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] son öğe <xref:System.Windows.Controls.Expander> olduğunda, boyutları otomatik olarak <xref:System.Windows.Controls.DockPanel>kalan alana eşit olarak ayarlar. Bu varsayılan davranışı önlemek <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> için, <xref:System.Windows.Controls.DockPanel> `false`nesne üzerindeki özelliği ayarla <xref:System.Windows.Controls.Expander> , ya da <xref:System.Windows.Controls.DockPanel>bir ' deki son öğe olmadığından emin olun  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>Kaydırılabilir İçerik Oluşturma  
 İçerik içerik alanının boyutu için çok büyükse, kaydırılabilir <xref:System.Windows.Controls.Expander> içerik <xref:System.Windows.Controls.ScrollViewer> sağlamak için içeriği bir olarak satamam. Denetim <xref:System.Windows.Controls.Expander> otomatik olarak kaydırma özelliği sağlamaz. Aşağıdaki resimde denetim <xref:System.Windows.Controls.Expander> içeren bir <xref:System.Windows.Controls.ScrollViewer> denetim gösterilmektedir.  
  
 **ScrollViewer'da Genişletici**  
  
 ![ScrollBar ile bir genişletici gösteren ekran görüntüsü.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Bir <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.ScrollViewer>denetime , <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.Expander> içeriğin <xref:System.Windows.Controls.Expander> içerik alanının boyutuna açıldığı yöne karşılık gelen boyut özelliğini ayarlayın. Örneğin, <xref:System.Windows.Controls.Expander.ExpandDirection%2A> özelliği <xref:System.Windows.Controls.Expander> (içerik <xref:System.Windows.Controls.ExpandDirection.Down> alanı açılır) üzerine ayarlarsanız, <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.ScrollViewer> denetimdeki özelliği içerik alanı için gerekli yüksekliğe ayarlayın. Bunun yerine içeriğin kendisi üzerinde yükseklik <xref:System.Windows.Controls.ScrollViewer> boyutunu ayarlarsanız, bu ayarı tanımıyor ve bu nedenle, kaydırılabilir içerik sağlamaz.  
  
 Aşağıdaki örnek, karmaşık içeriğe sahip ve denetim içeren <xref:System.Windows.Controls.ScrollViewer> bir <xref:System.Windows.Controls.Expander> denetimin nasıl oluşturulabildiğini gösterir. Bu örnek, <xref:System.Windows.Controls.Expander> bu bölümün başındaki çizime benzer bir örnek oluşturur.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>Hizalama Özelliklerini Kullanma  
 Denetimi ve <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> özelliklerini ayarlayarak içeriği hizalayabilirsiniz. <xref:System.Windows.Controls.Expander> Bu özellikleri ayarladığınızda, hizalama üstbilgi ve genişletilmiş içeriğe de uygulanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Nasıl Dır Konular](expander-how-to-topics.md)
