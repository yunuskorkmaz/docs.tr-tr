---
title: "İzlenecek yol: WPF'de Windows Forms Denetimlerini Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f78da83657c4c1bd913f67c9e612264cc5dbdf99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 Varsayılan olarak görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri her zaman çizilir diğer üstünde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri ve z düzeni tarafından etkilenmez. Z sıralamasını etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-default-z-order-behavior"></a>Z düzeni davranışı görmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi etiket öğesinde boyanır.  
  
#### <a name="to-see-the-z-order-behavior-when-isredirected-is-true"></a>Z düzeni davranışını IsRedirected true olduğunda görmek için  
  
1.  Önceki z düzeni örnek aşağıdaki XAML ile değiştirin.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#8b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#8b)]  
  
     Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Label öğesi üzerinden boyanır <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
## <a name="docking"></a>Yerleştirme  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>öğesi tarafından desteklenen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirme. Ayarlama <xref:System.Windows.Controls.DockPanel.Dock%2A> barındırılan denetimi sabitlemek için özelliği eklenmiş bir <xref:System.Windows.Controls.DockPanel> öğesi.  
  
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
 Farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeler, çoğu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri sürekli ölçeklenebilir değildir. Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, barındırılan denetimi mümkün olduğunda ölçeklendirir.  Tam özellikli ölçeklendirmeyi etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Varsayılan davranış kullanarak barındırılan denetimi ölçeklendirmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim ve onun çevresindeki öğeler 0,5 faktörüyle ölçeklendirilir. Ancak, barındırılan denetimin yazı tipi ölçeklenmez.  
  
#### <a name="to-scale-a-hosted-control-by-setting-isredirected-to-true"></a>IsRedirected true olarak ayarlayarak barındırılan denetimi ölçeklendirmek için  
  
1.  Önceki ölçeklendirme örnek aşağıdaki XAML ile değiştirin.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#12b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#12b)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetimi, çevreleyen öğeleri ve barındırılan denetimin yazı tipi 0,5 faktörüyle ölçeklendirilir.  
  
## <a name="rotating"></a>Döndürme  
 Farklı [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğeleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri döndürmeyi desteklemez. Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi diğer döndürülmez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] döndürme dönüşümü uygulandığında öğeleri. 180 derece başlatır dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olay.  Herhangi bir açıyla döndürme etkinleştirmek için ayarlanmış <xref:System.Windows.Interop.HwndHost.IsRedirected%2A> özelliği <xref:System.Windows.Forms.Integration.WindowsFormsHost> true ve <xref:System.Windows.Interop.HwndHost.CompositionMode%2A> özelliğine <xref:System.Windows.Interop.CompositionMode.Full> veya <xref:System.Windows.Interop.CompositionMode.OutputOnly>.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Karma uygulamada döndürme etkisini görmek için  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim değil döndürülür, ancak çevreleyen öğeleri 180 derece açının tarafından döndürülür. Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.  
  
#### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application-when-isredirected-is-true"></a>IsRedirected true olduğunda karma uygulamada döndürme etkisini görmek için  
  
1.  Önceki döndürme örneği aşağıdaki XAML ile değiştirin.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#13b](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml#13b)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Barındırılan denetim döndürülür.  Unutmayın <xref:System.Windows.Media.RotateTransform.Angle%2A> özelliği herhangi bir değere ayarlanabilir. Öğeleri görmek için pencereyi yeniden boyutlandırmak olabilir.  
  
## <a name="setting-padding-and-margins"></a>Ayar doldurma ve kenar boşlukları  
 Doldurma ve kenar boşlukları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeni doldurma ve kenar boşlukları benzer [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Basitçe <xref:System.Windows.Controls.Control.Padding%2A> ve <xref:System.Windows.FrameworkElement.Margin%2A> özellikleri <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi.  
  
#### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Doldurma ve barındırılan denetim kenar boşluklarını ayarlama  
  
1.  Aşağıdaki XAML içine kopyalamak <xref:System.Windows.Controls.Grid> öğesi.  
  
     [!code-xaml[WpfLayoutHostingWfWithXaml#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]  
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Doldurma ve kenar boşluğu ayarlar uygulanır barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri bunların uygulanacağı aynı şekilde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="using-dynamic-layout-containers"></a>Dinamik düzen kapsayıcılarını kullanma  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]iki dinamik düzeni kapsayıcıyı sağlar <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>. Bu kapsayıcı de kullanabilirsiniz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenler.  
  
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
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WindowsFormsHost Öğesi için yerleşim konuları](../../../../docs/framework/wpf/advanced/layout-considerations-for-the-windowsformshost-element.md)  
 [WPF örnek Forms denetimlerini pencereleri düzenleme](http://go.microsoft.com/fwlink/?LinkID=159971)  
 [İzlenecek yol: bir Windows Forms Bileşik Denetimi WPF barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [İzlenecek yol: Windows Forms içerisinde WPF bileşik denetimi barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
