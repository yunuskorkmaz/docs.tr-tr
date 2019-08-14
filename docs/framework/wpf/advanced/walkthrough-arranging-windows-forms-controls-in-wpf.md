---
title: 'İzlenecek yol: WPF’de Windows Forms Denetimlerini Düzenleme'
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: fa0181e95a03324c4cfa9395ae57439c260d1c23
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972304"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>İzlenecek yol: WPF’de Windows Forms Denetimlerini Düzenleme

Bu izlenecek yol, karma uygulamadaki denetimleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] düzenlemek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] için Düzen özelliklerinin nasıl kullanılacağını gösterir.

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

İşiniz bittiğinde, temel [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]özellikli uygulamalardaki düzen özelliklerinin anlaşılmasına sahip olacaksınız.

## <a name="prerequisites"></a>Önkoşullar

Bu yönergeyi tamamlamak için Visual Studio gerekir.

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-and-set-up-the-project"></a>Projeyi oluşturmak ve ayarlamak için

1. Adlı `WpfLayoutHostingWf`bir WPF uygulaması projesi oluşturun.

2. Çözüm Gezgini, aşağıdaki derlemelere başvurular ekleyin.

    - WindowsFormsIntegration

    - System.Windows.Forms

    - System.Drawing

3. MainWindow. xaml ' ye çift tıklayarak XAML görünümünde açın.

4. Öğesinde, aşağıdaki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ad alanı eşlemesini ekleyin. <xref:System.Windows.Window>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <xref:System.Windows.Controls.Grid> Öğesinde <xref:System.Windows.Controls.Grid.ShowGridLines%2A> özelliğini olarak`true` ayarlayın ve beş satırı ve üç sütunu tanımlayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanma

Varsayılan olarak, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimin yerleşimini işler.

### <a name="to-use-default-layout-settings"></a>Varsayılan düzen ayarlarını kullanmak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimiçinde<xref:System.Windows.Controls.Canvas>görüntülenir. <xref:System.Windows.Forms.Button?displayProperty=nameWithType> Barındırılan denetim içeriğine göre boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi barındırılan denetimi kapsayacak şekilde boyutlandırılır.

## <a name="sizing-to-content"></a>Içeriğe boyutlandırma

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi barındırılan denetimin içeriğini düzgün şekilde görüntülemesini sağlar.

### <a name="to-size-to-content"></a>İçeriğe göre boyut

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. İki yeni düğme denetimi daha uzun metin dizesi ve daha büyük yazı tipi boyutunu düzgün şekilde görüntüleyecek şekilde boyutlandırılır ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeler barındırılan denetimlere uyum sağlayacak şekilde yeniden boyutlandırılır.

## <a name="using-absolute-positioning"></a>Mutlak konumlandırmayı kullanma

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi Kullanıcı arabiriminde (UI) herhangi bir yere yerleştirmek için mutlak konumlandırmayı kullanabilirsiniz.

### <a name="to-use-absolute-positioning"></a>Mutlak konumlandırmayı kullanmak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, kılavuz hücresinin üst tarafından 20 piksel ve soldan 20 piksel yerleştirilir.

## <a name="specifying-size-explicitly"></a>Boyutu açıkça belirtme

Ve<xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> özelliklerinikullanarak<xref:System.Windows.FrameworkElement.Height%2A> öğenin boyutunu belirtebilirsiniz.

### <a name="to-specify-size-explicitly"></a>Boyutu açıkça belirtmek için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, varsayılan düzen ayarlarından daha küçük olan 50 piksel genişliğinde, 70 piksel yüksekliğinde bir boyut olarak ayarlanır. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetimin içeriği buna göre yeniden düzenlenir.

## <a name="setting-layout-properties"></a>Düzen özelliklerini ayarlama

Barındırılan denetimde, <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin özelliklerini kullanarak her zaman düzenle ilgili özellikleri ayarlayın. Doğrudan barındırılan denetimde düzen özelliklerinin ayarlanması, istenmeyen sonuçlara neden olur.

 İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] barındırılan denetimde düzen ile ilgili özelliklerin ayarlanması hiçbir etkiye sahip değildir.

### <a name="to-see-the-effects-of-setting-properties-on-the-hosted-control"></a>Barındırılan denetimde özellikleri ayarlamanın etkilerini görmek için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. Çözüm Gezgini, MainWindow. xaml ' ye çift tıklayın. vb veya MainWindow.xaml.cs, kod düzenleyicisinde açmak için.

3. Aşağıdaki kodu `MainWindow` sınıf tanımına kopyalayın.

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

5. **Bana tıklama** düğmesine tıklayın. Olay işleyicisi barındırılan denetimdeki <xref:System.Windows.Forms.Control.Top%2A> ve <xref:System.Windows.Forms.Control.Left%2A> özelliklerini ayarlar. `button1_Click` Bu, barındırılan denetimin <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğe içinde yeniden konumlandırılmasına neden olur. Konak aynı ekran alanını korur, ancak barındırılan denetim kırpılır. Bunun yerine, barındırılan denetim her zaman <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeyi doldurmalıdır.

## <a name="understanding-z-order-limitations"></a>Z düzeni sınırlamalarını anlama

Görünür <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğeler her zaman diğer WPF öğelerinin üzerine çizilir ve z düzeninde etkilenirler. Bu z sırası davranışını görmek için aşağıdakileri yapın:

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi, etiket öğesi üzerinde boyanmıştır.

## <a name="docking"></a>Tanımlaya

<xref:System.Windows.Forms.Integration.WindowsFormsHost>öğe yerleştirmeyi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] destekler. Barındırılan denetimi bir <xref:System.Windows.Controls.DockPanel> öğede sabitlemek için iliştirilmişözelliğiayarlayın.<xref:System.Windows.Controls.DockPanel.Dock%2A>

### <a name="to-dock-a-hosted-control"></a>Barındırılan bir denetimi sabitlemek için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Öğesi, <xref:System.Windows.Controls.DockPanel> öğesinin sağ tarafına yerleştirildi. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="setting-visibility"></a>Ayar görünürlüğü

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Öğesinde özelliğini<xref:System.Windows.UIElement.Visibility%2A> ayarlayarak denetiminizi görünmez hale getirebilirsiniz veya daraltabilirsiniz. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Bir denetim görünmez olduğunda, görüntülenmez, ancak düzen alanı kaplar. Bir denetim daraltıldığında, görüntülenmez ve düzen alanı kaplar.

### <a name="to-set-the-visibility-of-a-hosted-control"></a>Barındırılan bir denetimin görünürlüğünü ayarlamak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. MainWindow. xaml. vb veya MainWindow.xaml.cs içinde, aşağıdaki kodu sınıf tanımına kopyalayın.

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

4. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi görünmez hale getirmek için **tıkla, görünmeyen** düğmeye tıklayın.

5. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğeyi düzenden tamamen gizlemek için **daraltmak için tıklama** düğmesine tıklayın. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Denetim daraltıldığında, çevreleyen öğeler alanını kaplamak için yeniden düzenlenir.

## <a name="hosting-a-control-that-does-not-stretch"></a>UZAMAYAN bir denetimi barındırma

Bazı [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlerin sabit bir boyutu vardır ve mizanpajda kullanılabilir alanı dolduracak şekilde uzamayın. Örneğin, <xref:System.Windows.Forms.MonthCalendar> denetim bir ayı sabit bir alanda görüntüler.

### <a name="to-host-a-control-that-does-not-stretch"></a>UZAMAYAN bir denetimi barındırmak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe, kılavuz satırında ortalanır, ancak kullanılabilir alanı doldurmak için uzatılmamıştır. Pencere yeterince büyükse, barındırılan <xref:System.Windows.Forms.MonthCalendar> denetim tarafından iki veya daha fazla ay görüntülenmiş olabilir, ancak bunlar satırda ortalanır. Yerleşim [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] altyapısı, kullanılabilir alanı dolduracak şekilde boyutlandırılabilen öğeleri ortalar.

## <a name="scaling"></a>Ölçeklendirme

WPF öğelerinden farklı olarak, çoğu Windows Forms denetimleri sürekli ölçeklenebilir değildir. Özel ölçeklendirme sağlamak için <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız.

### <a name="to-scale-a-hosted-control-by-using-the-default-behavior"></a>Barındırılan bir denetimi varsayılan davranışı kullanarak ölçeklendirmek için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Barındırılan denetim ve çevreleyen öğeleri 0,5 faktörü ile ölçeklendirilir. Ancak, barındırılan denetimin yazı tipi ölçeklenmez.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Döner

WPF öğelerinden farklı olarak Windows Forms denetimleri döndürmeyi desteklemez. Bir döndürme dönüştürmesi uygulandığında öğesidiğerWPFöğeleriylebirliktedöndürülmez.<xref:System.Windows.Forms.Integration.WindowsFormsHost> 180 dereceden başka bir döndürme değeri <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError> olayı başlatır.

### <a name="to-see-the-effect-of-rotation-in-a-hybrid-application"></a>Karma uygulamada döndürmenin etkisini görmek için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Barındırılan denetim döndürülmez, ancak çevreleyen öğeleri 180 derece bir açıda döndürülür. Öğeleri görmek için pencereyi yeniden boyutlandırmanız gerekebilir.

## <a name="setting-padding-and-margins"></a>Doldurma ve kenar boşlukları ayarlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Düzendeki doldurma ve kenar boşlukları, içindeki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]doldurma ve kenar boşluklarıyla benzerdir. Öğesi üzerinde <xref:System.Windows.Controls.Control.Padding%2A> <xref:System.Windows.FrameworkElement.Margin%2A> ve özelliklerini ayarlamanız yeterlidir. <xref:System.Windows.Forms.Integration.WindowsFormsHost>

### <a name="to-set-padding-and-margins-for-a-hosted-control"></a>Barındırılan bir denetim için doldurma ve kenar boşluklarını ayarlamak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Doldurma ve kenar boşluğu ayarları, barındırılan [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimlere, içinde [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]uygulandıkları şekilde uygulanır.

## <a name="using-dynamic-layout-containers"></a>Dinamik Düzen kapsayıcıları kullanma

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]iki dinamik düzen kapsayıcısı <xref:System.Windows.Forms.FlowLayoutPanel> sağlar ve. <xref:System.Windows.Forms.TableLayoutPanel> Bu kapsayıcıları mizanpajlar halinde [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de kullanabilirsiniz.

### <a name="to-use-a-dynamic-layout-container"></a>Dinamik düzen kapsayıcısını kullanmak için

1. Aşağıdaki XAML 'yi <xref:System.Windows.Controls.Grid> öğesine kopyalayın.

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. MainWindow. xaml. vb veya MainWindow.xaml.cs içinde aşağıdaki kodu sınıf tanımına kopyalayın.

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Kurucudaki `InitializeFlowLayoutPanel` yöntemine bir çağrı ekleyin.

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın. Öğesi öğesini <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>doldurur ve alt<xref:System.Windows.Forms.FlowLayoutPanel> denetimlerini varsayılan olarak düzenler. <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Forms.Integration.WindowsFormsHost>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [WindowsFormsHost Öğesi için Düzen Konusunda Dikkat Edilmesi Gereken Noktalar](layout-considerations-for-the-windowsformshost-element.md)
- [WPF örneğindeki Windows Forms denetimlerini düzenleme](https://go.microsoft.com/fwlink/?LinkID=159971)
- [İzlenecek yol: WPF 'de Windows Forms Bileşik denetim barındırma](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [İzlenecek yol: Windows Forms WPF bileşik denetimini barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
