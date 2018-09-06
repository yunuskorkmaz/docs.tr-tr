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
ms.openlocfilehash: 98b108be518a9fef03ee299d43ed591cf736f68f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786089"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme
Bu izlenecek yol size nasıl kullanılacağını gösterir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek için düzen özelliklerini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karma uygulamada denetimleri.  
  
 Bu kılavuzda gösterilen görevler aşağıdakileri içerir:  
  
-   Proje oluşturuluyor.  
  
-   Varsayılan düzen ayarları kullanıyor.  
  
-   İçeriği boyutlandırma.  
  
-   Konumlandırmayı mutlak kullanma.  
  
-   Açıkça boyutunu belirtme.  
  
-   Düzen özelliklerini ayarlama.  
  
-   Z düzenini sınırlamaları anlama.  
  
-   Yerleştirme.  
  
-   Görünürlük ayarlama.  
  
-   Esnetme değil bir denetim barındırma.  
  
-   Ölçeklendirme.  
  
-   Döndürme.  
  
-   Ayar doldurma ve kenar boşlukları.  
  
-   Dinamik düzen kapsayıcıları kullanma.  
  
 Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WPF Örneği'nde Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971).  
  
 İşlemi tamamladığınızda, bir anlayışa sahip [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-tabanlı uygulamaları.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturma ve projesi kurun  
  
1.  Adlı bir WPF uygulaması projesi oluşturmak `WpfLayoutHostingWf`.  
  
2.  Çözüm Gezgini'nde, aşağıdaki derlemelere başvurular ekleyin.  
  
    -   WindowsFormsIntegration  
  
    -   System.Windows.Forms  
  
    -   System.Drawing  
  
3.  MainWindow.xaml XAML görünümünde açmak için çift tıklayın.  
  
4.  İçinde <xref:System.Windows.Window> öğesi, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesi.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  İçinde <xref:System.Windows.Controls.Grid> öğe kümesi <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini `true` ve beş satır ve üç sütun tanımlayın.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]  
  
## <a name="using-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanma  
 Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan düzenini işler [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.  
  
#### <a name="to-use-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanmak için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Denetimi görünür <xref:System.Windows.Controls.Canvas>. Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi boyutta denetimden uyum sağlamak için.  
  
## <a name="sizing-to-content"></a>İçerik boyutu  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesini denetimden içeriği düzgün görüntülenmesi için boyutlandırılır sağlar.  
  
#### <a name="to-size-to-content"></a>İçerik boyutu  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. İki yeni düğme denetimleri düzgün bir şekilde, daha büyük yazı tipi boyutu ve uzun metin dizesini görüntülemek için boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlerin sığması için yeniden boyutlandırılır.  
  
## <a name="using-absolute-positioning"></a>Mutlak konumlandırmayı kullanma  
 Mutlak konumlandırma yerleştirmek için kullanabileceğiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini herhangi bir kullanıcı arabirimi (UI).  
  
#### <a name="to-use-absolute-positioning"></a>Mutlak konumlandırma kullanmak için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz hücresi üst tarafındaki 20 piksel ve 20 piksel soldan yerleştirilir.  
  
## <a name="specifying-size-explicitly"></a>Açıkça boyutunu belirtme  
 Boyutunu belirtebilirsiniz <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini kullanarak <xref:System.Windows.FrameworkElement.Width%2A> ve <xref:System.Windows.FrameworkElement.Height%2A> özellikleri.  
  
#### <a name="to-specify-size-explicitly"></a>Boyutu açıkça belirtmek için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi varsayılan düzen ayarlarından daha küçük olan bir boyutu 50 piksel genişliğinde ve 70 piksel yüksekliğinde, ayarlanır. İçeriği [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi uygun şekilde düzenlenmeyecek.  
  
## <a name="setting-layout-properties"></a>Düzen özelliklerini ayarlama  
 Her zaman düzen ile ilgili özellikleri ayarlamak üzerinde barındırılan denetim özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Doğrudan barındırılan denetimde düzen özelliklerini ayarlama, istenmeyen sonuçlar verir.  
  
 Düzen ilgili özellikler barındırılan denetimi ayarını [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] hiçbir etkisi olmaz.  
  
#### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Üzerinde barındırılan denetim özelliklerini ayarlama etkilere bakın  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]  
  
2.  Çözüm Gezgini içinde MainWindow.xaml çift tıklayın. vb veya MainWindow.xaml.cs Kod Düzenleyicisi'nde açın.  
  
3.  Aşağıdaki kodu kopyalayın `MainWindow` sınıf tanımını.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]  
  
4.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
5.  Tıklayın **me tıklayın** düğmesi. `button1_Click` Olay işleyicisi kümeleri <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> barındırılan denetim özellikleri. Bu içinde konumlandırılmasına denetimden neden <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Konak aynı ekran alanını korur, ancak denetimden kırpılır. Bunun yerine barındırılan denetimi her zaman dolması gerektiğini <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
## <a name="understanding-z-order-limitations"></a>Z düzenini sınırlamaları anlama  
 Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman diğer WPF öğeleri üzerine çizilmiş ve z-düzeni tarafından etkilenmez. Bu z düzenini davranışını görmek için aşağıdakileri yapın:

1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
 
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiketi öğenin boyanır.  


## <a name="docking"></a>Yerleştirme  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin desteklediği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme. Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> ekli özellik barındırılan denetimi sabitlemek için bir <xref:System.Windows.Controls.DockPanel> öğesi.  
  
#### <a name="to-dock-a-hosted-control"></a>Barındırılan bir denetim sabitlemek için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi sağ tarafına yerleştirilmiş <xref:System.Windows.Controls.DockPanel> öğesi.  
  
## <a name="setting-visibility"></a>Görünürlük ayarlama  
 Yapabileceğiniz, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetiminizi görünmez veya ayarlayarak Daralt <xref:System.Windows.UIElement.Visibility%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi. Bir denetim görünmez olduğunda görüntülenmez, ancak düzen yer kaplar. Bir denetim daraltıldığında görüntülenmez veya Düzen boşluk kaplamaz.  
  
#### <a name="to-set-the-visibility-of-a-hosted-control"></a>Barındırılan bir denetim görünürlüğünü ayarlamak için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]  
  
2.  MainWindow.xaml.vb veya MainWindow.xaml.cs seçeneğinde, sınıf tanımının içine aşağıdaki kodu kopyalayın.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]  
  
3.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
4.  Tıklayın **görünmez yapmak için tıklatın** düğmesini <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe görünmez.  
  
5.  Tıklayın **daraltmak için tıklatın** gizlemek için düğme <xref:System.Windows.Forms.Integration.WindowsFormsHost> düzenini öğesinden tamamen. Zaman [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi daraltıldığında, çevreleyen öğeler alanı kaplaması için düzenlenir.  
  
## <a name="hosting-a-control-that-does-not-stretch"></a>Esnetme değil bir denetimi barındırma  
 Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sabit bir boyuta sahiptir ve düzendeki kullanılabilir alanı dolduracak şekilde uzatılır değil. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi, bir ay sabit boşluk görüntüler.  
  
#### <a name="to-host-a-control-that-does-not-stretch"></a>Esnetme değil bir denetimi barındırma  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz satırı içinde ortalanır, ancak bunu kullanılabilir alanı dolduracak şekilde genişletilir değil. Pencerenin yeterince büyük ise, iki veya daha fazla aylık barındırılan tarafından görüntülenen görebilirsiniz <xref:System.Windows.Forms.MonthCalendar> denetimidir, ancak bu satırda ortalanır. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerleşim altyapısı kullanılabilir alanı dolduracak şekilde boyutlandırılmalıdır olamaz öğeleri ortalar.  
  
## <a name="scaling"></a>Ölçeklendirme  
 WPF öğesinin aksine, çoğu Windows Forms denetimlerini sürekli olarak ölçeklenebilir değildir. Özel bir ölçekleme sağlamak için geçersiz kılma <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemi. 
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Barındırılan bir denetimin varsayılan davranışını kullanarak ölçeklendirme  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörüyle ölçeklenir. Ancak, barındırılan denetim yazı tipi ölçeklenmez.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Döndürme  
 WPF öğesinin aksine, Windows Forms denetimleri döndürmeyi desteklemez. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi döndürme dönüşümü uygulandığı zaman diğer WPF öğelerle döndürülmez. 180 derece harekete geçirirse dışındaki herhangi bir dönüş değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.
 
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Döndürme karma uygulamada etkisini görmek için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür. Öğeleri görmek için pencereyi boyutlandırmak olabilir.  
 

## <a name="setting-padding-and-margins"></a>Ayar doldurma ve kenar boşlukları  
 Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzen doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Ayarlamanız yeterlidir <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Doldurma ve barındırılan denetim kenar boşluklarını ayarlama  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] uygulanacağı de aynı şekilde denetimleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Dinamik düzen kapsayıcılarını kullanma  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] iki dinamik düzen kapsayıcılar sağlayarak <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>. Bu kapsayıcıları da kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.  
  
#### <a name="to-use-a-dynamic-layout-container"></a>Dinamik düzen kapsayıcısı kullanmak için  
  
1.  İçine aşağıdaki XAML kopyalama <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]  
  
2.  MainWindow.xaml.vb veya MainWindow.xaml.cs içinde sınıf tanımının içine aşağıdaki kodu kopyalayın.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]  
  
3.  Bir çağrı ekleyin `InitializeFlowLayoutPanel` oluşturucuda yöntemi.  
  
     [!code-csharp[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]  
  
4.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi doldurur <xref:System.Windows.Controls.DockPanel>, ve <xref:System.Windows.Forms.FlowLayoutPanel> varsayılan, alt denetimlerini düzenler <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)  
 [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [Düzenleme Windows Forms denetimleri örneği](https://go.microsoft.com/fwlink/?LinkID=159971)  
 [İzlenecek yol: WPF'de Windows Forms Bileşik Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
