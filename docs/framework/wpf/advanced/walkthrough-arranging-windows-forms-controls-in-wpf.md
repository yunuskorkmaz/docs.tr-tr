---
title: "İzlenecek yol: WPF 'de Windows Forms denetimlerini düzenleme"
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 3a94ef65be99b01a9511f37872cbcacd6ec12264
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179431"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>İzlenecek yol: WPF 'de Windows Forms denetimlerini düzenleme

Bu izlenecek yol, karma uygulamada [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimleri düzenlemek için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzen özelliklerinin nasıl kullanılacağını gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Proje oluşturuluyor.
- Varsayılan düzen ayarlarını kullanma.
- İçeriğe boyutlandırma.
- Mutlak konumlandırmayı kullanma.
- Boyutu açıkça belirtme.
- Düzen özelliklerini ayarlama.
- Z düzeni sınırlamalarını anlama.
- Tanımlaya.
- Görünürlük ayarlanıyor.
- UZAMAYAN bir denetimi barındırma.
- Lemeyle.
- Döner.
- Doldurma ve kenar boşlukları ayarlanıyor.
- Dinamik Düzen kapsayıcıları kullanma.

Bu izlenecek yolda gösterilen görevlerin tüm kod listesi için bkz. [WPF örneğinde Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971).

İşiniz bittiğinde, @no__t -1 tabanlı uygulamalarda [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] düzen özelliklerinin anlaşılmasına sahip olacaksınız.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="creating-the-project"></a>Projeyi oluşturma

Projeyi oluşturmak ve ayarlamak için şu adımları izleyin:

1. @No__t-0 adlı bir WPF uygulaması projesi oluşturun.

2. Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin:

    - WindowsFormsIntegration
    - System. Windows. Forms
    - System. Drawing

3. *MainWindow. xaml* ' ye ÇIFT tıklayarak xaml görünümünde açın.

4. @No__t-0 öğesinde aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. @No__t-0 öğesinde <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini `true` olarak ayarlayın ve beş satırı ve üç sütunu tanımlayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanma

Varsayılan olarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi için düzeni işler.

Varsayılan düzen ayarlarını kullanmak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 <xref:System.Windows.Forms.Button?displayProperty=nameWithType> denetimi <xref:System.Windows.Controls.Canvas> ' de görünür. Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyutlandırılır.

## <a name="sizing-to-content"></a>Içeriğe boyutlandırma

@No__t-0 öğesi barındırılan denetimin içeriğini düzgün şekilde görüntülemesini sağlar.

İçeriğe göre boyut için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. İki yeni düğme denetimi daha uzun metin dizesi ve daha büyük yazı tipi boyutunu düzgün şekilde görüntüleyecek şekilde boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri barındırılan denetimlere uyum sağlayacak şekilde yeniden boyutlandırılır.

## <a name="using-absolute-positioning"></a>Mutlak konumlandırmayı kullanma

@No__t-0 öğesini Kullanıcı arabiriminde (UI) herhangi bir yere yerleştirmek için mutlak konumlandırmayı kullanabilirsiniz.

Mutlak konumlandırmayı kullanmak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi, kılavuz hücresinin üst tarafından 20 piksel ve soldan 20 piksel yerleştirilir.

## <a name="specifying-size-explicitly"></a>Boyutu açıkça belirtme

@No__t-1 ve <xref:System.Windows.FrameworkElement.Height%2A> özelliklerini kullanarak <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin boyutunu belirtebilirsiniz.

Boyutu açıkça belirtmek için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi, varsayılan düzen ayarlarından daha küçük olan 70 piksel yüksekliğinde 50 piksellik bir boyuta ayarlanır. @No__t-0 denetiminin içeriği buna göre yeniden düzenlenir.

## <a name="setting-layout-properties"></a>Düzen özelliklerini ayarlama

@No__t-0 öğesinin özelliklerini kullanarak barındırılan denetimde düzen ile ilgili özellikleri her zaman ayarlayın. Doğrudan barındırılan denetimde düzen özelliklerinin ayarlanması, istenmeyen sonuçlara neden olur.

 @No__t-0 ' da barındırılan denetimde düzen ile ilgili özelliklerin ayarlanması hiçbir etkiye sahip değildir.

Barındırılan denetimde özellikleri ayarlamanın etkilerini görmek için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. **Çözüm Gezgini**' de, *MainWindow. xaml. vb* veya *MainWindow.xaml.cs* ' ye çift tıklayarak kodu düzenleyici 'de açın.

3. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın:

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.

5. **Bana tıklama** düğmesine tıklayın. @No__t-0 olay işleyicisi barındırılan denetimde <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> özelliklerini ayarlar. Bu, barındırılan denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi içinde yeniden konumlandırılmasına neden olur. Konak aynı ekran alanını korur, ancak barındırılan denetim kırpılır. Bunun yerine, barındırılan denetim <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini her zaman doldurmalıdır.

## <a name="understanding-z-order-limitations"></a>Z düzeni sınırlamalarını anlama

Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeleri, her zaman diğer WPF öğelerinin üzerine çizilir ve z düzeninde etkilenirler. Bu z sırası davranışını görmek için aşağıdakileri yapın:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi etiket öğesi üzerinde boyanmıştır.

## <a name="docking"></a>Tanımlaya

<xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerleştirmeyi destekler. Barındırılan denetimi bir <xref:System.Windows.Controls.DockPanel> öğesinde yerleştirmek için <xref:System.Windows.Controls.DockPanel.Dock%2A> ekli özelliğini ayarlayın.

Barındırılan bir denetimi sabitlemek için aşağıdaki adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi <xref:System.Windows.Controls.DockPanel> öğesinin sağ tarafına yerleştirildi.

## <a name="setting-visibility"></a>Ayar görünürlüğü

@No__t-2 öğesinde <xref:System.Windows.UIElement.Visibility%2A> özelliğini ayarlayarak @no__t 0 denetimini görünmez yapabilir veya daraltabilirsiniz. Bir denetim görünmez olduğunda, görüntülenmez, ancak düzen alanı kaplar. Bir denetim daraltıldığında, görüntülenmez ve düzen alanı kaplar.

Barındırılan bir denetimin görünürlüğünü ayarlamak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. *MainWindow. xaml. vb* veya *MainWindow.xaml.cs*içinde, aşağıdaki kodu sınıf tanımına kopyalayın:

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın.

4. @No__t-1 öğesini görünmez hale getirmek için **görünmez** düğmesini tıklatın.

5. @No__t-1 öğesini düzenden tamamen gizlemek için **daraltmak Için tıklama** düğmesine tıklayın. @No__t-0 denetimi daraltıldığında, çevreleyen öğeler alanını kaplamak için yeniden düzenlenir.

## <a name="hosting-a-control-that-does-not-stretch"></a>UZAMAYAN bir denetimi barındırma

Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerinin sabit bir boyutu vardır ve mizanpajda kullanılabilir alanı dolduracak şekilde uzamayın. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetimi sabit bir alanda bir ay görüntüler.

UZAMAYAN bir denetimi barındırmak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi kılavuz satırında ortalanır, ancak kullanılabilir alanı doldurmak için uzatılmamıştır. Pencere yeterince büyükse, barındırılan <xref:System.Windows.Forms.MonthCalendar> denetiminde görüntülenen iki veya daha fazla ay görebilirsiniz, ancak bunlar satırda ortalanır. @No__t-0 düzen altyapısı, kullanılabilir alanı dolduracak şekilde boyutlandırılabilen öğeleri ortalar.

## <a name="scaling"></a>Ölçeklendirme

WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir. Özel ölçeklendirme sağlamak için <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız.

Barındırılan bir denetimi varsayılan davranışı kullanarak ölçeklendirmek için aşağıdaki adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörü ile ölçeklendirilir. Ancak, barındırılan denetimin yazı tipi ölçeklenmez.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Döner

WPF öğelerinden farklı olarak Windows Forms denetimleri döndürmeyi desteklemez. @No__t-0 öğesi, bir döndürme dönüştürmesi uygulandığında diğer WPF öğeleriyle birlikte döndürülmez. 180 derecenin dışındaki herhangi bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayını oluşturur.

Bir karma uygulamada döndürmenin etkisini görmek için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. Barındırılan denetim döndürülmez, ancak çevreleyen öğeleri 180 derece bir açıda döndürülür. Öğeleri görmek için pencereyi yeniden boyutlandırmanız gerekebilir.

## <a name="setting-padding-and-margins"></a>Doldurma ve kenar boşlukları ayarlama

@No__t-0 düzeninde doldurma ve kenar boşlukları [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ' deki doldurma ve kenar boşluklarına benzerdir. @No__t-0 ve <xref:System.Windows.FrameworkElement.Margin%2A> özelliklerini <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinde ayarlamanız yeterlidir.

Barındırılan bir denetimin doldurmasını ve kenar boşluklarını ayarlamak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. Doldurma ve kenar boşluğu ayarları, barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ' e uygulanacak şekilde uygulanır.

## <a name="using-dynamic-layout-containers"></a>Dinamik Düzen kapsayıcıları kullanma

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] iki dinamik düzen kapsayıcısı sağlar, <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>. Bu kapsayıcıları [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzeninde de kullanabilirsiniz.

Dinamik düzen kapsayıcısını kullanmak için şu adımları izleyin:

1. Aşağıdaki XAML <xref:System.Windows.Controls.Grid> öğesine kopyalayın:

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. *MainWindow. xaml. vb* veya *MainWindow.xaml.cs*içinde, aşağıdaki kodu sınıf tanımına kopyalayın:

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Oluşturucuda `InitializeFlowLayoutPanel` yöntemine bir çağrı ekleyin:

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Uygulamayı derlemek ve çalıştırmak için <kbd>F5</kbd> tuşuna basın. @No__t-0 öğesi <xref:System.Windows.Controls.DockPanel> ' i doldurur ve <xref:System.Windows.Forms.FlowLayoutPanel> alt denetimlerini varsayılan <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> olarak düzenler.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio 'da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost öğesi için düzen konuları](layout-considerations-for-the-windowsformshost-element.md)
- [WPF örneğindeki Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971)
- [İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
