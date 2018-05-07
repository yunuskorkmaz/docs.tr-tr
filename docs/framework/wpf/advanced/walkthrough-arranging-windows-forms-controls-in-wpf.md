---
title: "İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme"
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: f2cf82c54724a43a60fb9077c5731d4b4ad2cfd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme
Bu kılavuz size nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek için Düzen özelliklerinin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karma uygulama denetimlerinde.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi oluşturma.  
  
-   Varsayılan düzen ayarlarını kullanma.  
  
-   İçeriği boyutlandırma.  
  
-   Mutlak konumlandırmayı kullanma.  
  
-   Boyutu açıkça belirtme.  
  
-   Düzen özelliklerini ayarlama.  
  
-   Z düzeni sınırlamalarını anlama.  
  
-   Yerleştirme.  
  
-   Görünürlük ayarlama.  
  
-   Uzatma olmayan bir denetimi barındırma.  
  
-   Ölçeklendirme.  
  
-   Döndürme.  
  
-   Ayar doldurma ve kenar boşlukları.  
  
-   Dinamik düzen kapsayıcılarını kullanma.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [düzenleme Windows Forms denetimlerinde WPF örnek](http://go.microsoft.com/fwlink/?LinkID=159971).  
  
 İşiniz bittiğinde, anlaşılması gerekir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturun ve projeyi ayarlamak için  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `WpfLayoutHostingWf`.  
  
2.  Çözüm Gezgini'nde, aşağıdaki derlemeler başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  MainWindow.xaml XAML görünümünde açmak için çift tıklayın.  
  
4.  İçinde <xref:System.Windows.Window> öğesi, aşağıdaki ekleyin [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesi.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  İçinde <xref:System.Windows.Controls.Grid> öğe kümesi <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğine `true` ve beş satır ve üç sütun tanımlayın.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanma  
 Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi işler barındırılan düzenini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
#### <a name="to-use-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanmak için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Denetimi görünür <xref:System.Windows.Controls.Canvas>. Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyuta sahip.  
  
## <a name="sizing-to-content"></a>İçeriği boyutlandırma  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi sağlar barındırılan denetim içeriği düzgün görüntülemek için boyutlandırılır.  
  
#### <a name="to-size-to-content"></a>İçin içerik boyutu  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. İki yeni düğmesi denetimleri uzun metin dizesini ve büyük yazı tipi boyutunu düzgün görüntülemek için boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlerin sığması için yeniden boyutlandırılır.  
  
## <a name="using-absolute-positioning"></a>Mutlak konumlandırmayı kullanma  
 Yerleştirmek için mutlak konumlandırma kullanabilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini herhangi bir kullanıcı arabirimi (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Mutlak konumlandırma kullanmak için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz hücresinin üst tarafındaki 20 piksel ve soldan 20 piksel yerleştirilir.  
  
## <a name="specifying-size-explicitly"></a>Boyutu açıkça belirtme  
 Boyutu belirtebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi kullanılarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.  
  
#### <a name="to-specify-size-explicitly"></a>Boyutu açıkça belirtmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan düzen ayarlarından daha küçük olan 50 piksel genişliğinde 70 piksel yüksek boyutunu ayarlanır. İçeriği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim uygun şekilde düzenlenmeyecek.  
  
## <a name="setting-layout-properties"></a>Düzen özelliklerini ayarlama  
 Her zaman Düzen ilgili özelliklerini ayarlama barındırılan denetimde özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Doğrudan barındırılan denetimde düzen özelliklerini ayarlama, istenmeyen sonuçlar verir.  
  
 Düzen ilgili özellikler barındırılan denetimi ayarı [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiçbir etkisi olmaz.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Üzerinde barındırılan denetim özelliklerini ayarlama etkilerini görmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  Çözüm Gezgini'nde MainWindow.xaml çift tıklayın. vb veya MainWindow.xaml.cs kod düzenleyicisinde açın.  
  
3.  Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımının.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
5.  Tıklatın **Click me** düğmesi. `button1_Click` Olay işleyicisi kümeleri <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> barındırılan denetim özellikleri. Bu içinde konumlandırılmasına denetimden neden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Ana bilgisayar aynı ekran alanını korur, ancak barındırılan denetim kırpılır. Bunun yerine, barındırılan denetim daima doldurmanız <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
## <a name="understanding-z-order-limitations"></a>Z düzeni sınırlamalarını anlama  
 Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman en üstünde diğer WPF öğeleri çizileceğini ve z düzeni tarafından etkilenmez. Bu z düzeni davranışı görmek için aşağıdakileri yapın:

1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiket öğesinde boyanır.  


## <a name="docking"></a>Yerleştirme  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi tarafından desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme. Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> barındırılan denetimi sabitlemek için özelliği eklenmiş bir <xref:System.Windows.Controls.DockPanel> öğesi.  
  
#### <a name="to-dock-a-hosted-control"></a>Barındırılan denetimi sabitlemek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi için sağ tarafındaki yerleşik <xref:System.Windows.Controls.DockPanel> öğesi.  
  
## <a name="setting-visibility"></a>Görünürlüğü ayarlama  
 Yapabileceğiniz, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez veya ayarlayarak Daralt <xref:System.Windows.UIElement.Visibility%2A> özellikte <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Bir denetim görünmez olduğunda, görüntülenmez, ancak düzeni yer kaplar. Bir denetim daraltıldığında görüntülenmez veya düzeni alan kaplar yapar.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Barındırılan denetimi görünürlüğünü ayarlamak için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb veya MainWindow.xaml.cs, sınıf tanımının içine aşağıdaki kodu kopyalayın.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Tıklatın **görünmez yapmak için tıklatın** yapmak için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi görünmez.  
  
5.  Tıklatın **daraltmak için tıklatın** gizlemek için düğmesi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini düzenden tamamen. Zaman [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanı kaplaması için düzenlenir.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Uzatma olmayan bir denetimi barındırma  
 Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve yerleşiminde kullanılabilir alanı dolduracak şekilde uzatılır değil. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi, sabit bir alanda bir ay görüntüler.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>Uzatılamayan denetimi barındırma  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi kılavuz satırında ortalanır, ancak bunu kullanılabilir alanı dolduracak şekilde genişletilir değil. Pencere yeterince büyük ise, barındırılan tarafından görüntülenen iki veya daha fazla ayı görebilirsiniz <xref:System.Windows.Forms.MonthCalendar> denetimi, ancak bunlar satır içinde ortalanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerleşim altyapısı merkezleri kullanılabilir alanı dolduracak şekilde boyutlandırılmış olamaz öğeleri.  
  
## <a name="scaling"></a>ölçeklendirme  
 WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir. Özel ölçeklendirme sağlamak için geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemi. 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Varsayılan davranış kullanarak barındırılan denetimi ölçeklendirmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim ve onun çevresindeki öğeler 0,5 faktörüyle ölçeklendirilir. Ancak, barındırılan denetimin yazı tipi ölçeklenmez.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Döndürme  
 WPF öğelerinden farklı olarak, Windows Forms denetimleri döndürmeyi desteklemez. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi döndürme dönüşümü uygulandığında diğer WPF öğelerle döndürülmez. 180 derece başlatır dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Karma uygulamada döndürme etkisini görmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür. Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.  
 

## <a name="setting-padding-and-margins"></a>Ayar doldurma ve kenar boşlukları  
 Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Basitçe <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Doldurma ve barındırılan denetim kenar boşluklarını ayarlama  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bunların uygulanacağı aynı şekilde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Dinamik düzen kapsayıcılarını kullanma  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] iki dinamik düzeni kapsayıcıyı sağlar <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>. Bu kapsayıcı de kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Dinamik düzen kapsayıcısını kullanmak için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb veya MainWindow.xaml.cs sınıf tanımının içine aşağıdaki kodu kopyalayın.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Bir çağrı ekleyin `InitializeFlowLayoutPanel` oluşturucuda yöntemi.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi doldurur <xref:System.Windows.Controls.DockPanel>, ve <xref:System.Windows.Forms.FlowLayoutPanel> varsayılan alt öğe denetimlerini düzenler <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [WPF örnek Forms denetimlerini pencereleri düzenleme](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
