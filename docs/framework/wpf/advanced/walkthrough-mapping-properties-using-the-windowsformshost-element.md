---
title: 'İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: edd9d6f698ba27cacb5e9a5eecab43f58d47b8e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007141"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme

Bu izlenecek yol size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan karşılık gelen özelliklere özellikleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- Proje oluşturuluyor.

- Uygulama düzenini tanımlama.

- Yeni bir özellik eşlemesi tanımlama.

- Varsayılan özellik eşlemesi kaldırılıyor.

- Varsayılan özellik eşlemesi değiştiriliyor.

- Varsayılan özellik eşlemesi genişletme.

Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [WindowsFormsHost öğesi örneği kullanarak eşleme özelliklerini](https://go.microsoft.com/fwlink/?LinkID=160019).

Bitirdiğiniz zaman, eşlemek mümkün olmayacak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan karşılık gelen özelliklere özellikleri [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Oluşturma ve projesi kurun

1. Oluşturma bir **WPF uygulaması** adlı proje `PropertyMappingWithWfhSample`.

2. İçinde **Çözüm Gezgini**, WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3. İçinde **Çözüm Gezgini**, System.Drawing ve System.Windows.Forms öğelerini derlemelere başvurular ekleyin.

## <a name="defining-the-application-layout"></a>Uygulama düzenini tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Uygulamanız tarafından kullanılan temel <xref:System.Windows.Forms.Integration.WindowsFormsHost> ana öğesine bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimi.

### <a name="to-define-the-application-layout"></a>Uygulama düzenini tanımlamak için

1. Window1.XAML içinde açın [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2. Varolan kodu aşağıdaki kodla değiştirin.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Window1.xaml.cs Kod Düzenleyicisi'nde açın.

4. Dosyasının en üstüne aşağıdaki ad alanlarını içeri aktarın.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Yeni bir özellik eşlemesi tanımlama

<xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğe birkaç varsayılan özellik eşlemeleri sağlar. Çağırarak yeni bir özellik eşlemesi Ekle <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-define-a-new-property-mapping"></a>Yeni bir özellik eşlemesi tanımlamak için

- Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.UIElement.Clip%2A> özelliği.

     `OnClipChange` Yöntemi çevirir <xref:System.Windows.UIElement.Clip%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> özelliği.

     `Window1_SizeChanged` Yöntemi işler pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olay ve uygulama penceresine sığacak şekilde kırpma bölgesini boyutları.

## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesi kaldırılıyor

Çağırarak varsayılan özellik eşlemesini kaldırma <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için

- Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği.

## <a name="replacing-a-default-property-mapping"></a>Varsayılan özellik eşlemesi değiştiriliyor

Varsayılan eşleme ve arama kaldırarak bir varsayılan özellik eşlemesini değiştirmek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodunda <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-replace-a-default-property-mapping"></a>Varsayılan özellik eşlemesini değiştirmek için

- Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping` Yöntemi için varsayılan eşlemeyi değiştirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği.

     `OnFlowDirectionChange` Yöntemi çevirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği.

     `cb_CheckedChanged` Yöntemi tanıtıcıları <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayda <xref:System.Windows.Forms.CheckBox> denetimi. Buna atar <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik değerini temel alarak <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği

## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesi genişletme

Varsayılan özellik eşlemesini ve ayrıca kendi eşleme ile genişletmek kullanabilirsiniz.

### <a name="to-extend-a-default-property-mapping"></a>Varsayılan özellik eşlemesi genişletmek için

- Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping` Yöntemi, varolan bir özel özellik translator ekler <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.

     `OnBackgroundChange` Yöntemi barındırılan denetim için belirli bir görüntünün atar <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği. `OnBackgroundChange` Yöntemi, varsayılan özellik eşlemesi uygulandıktan sonra çağrılır.

## <a name="initializing-your-property-mappings"></a>Özellik eşlemelerinizin başlatılıyor

Özelliği daha önce açıklandığı gibi yöntemleri çağırarak eşlemelerinizi <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.

### <a name="to-initialize-your-property-mappings"></a>Özellik eşlemelerinizin başlatmak için

1. Tanımı aşağıdaki kodu kopyalayarak `Window1` sınıfı.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded` Yöntemi tanıtıcıları <xref:System.Windows.FrameworkElement.Loaded> olay ve aşağıdaki başlatmaya gerçekleştirir.

    - Oluşturur bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> denetimi.

    - Özellik eşlemelerini ayarlamak için daha önce izlenecek içinde tanımlanan yöntemleri çağırır.

    - Eşlenen özelliklere başlangıç değerleri atar.

2. Tuşuna **F5** oluşturun ve uygulamayı çalıştırın. Etkisini görmek için bu onay kutusuna tıklayın <xref:System.Windows.FrameworkElement.FlowDirection%2A> eşleme. Düzen onay kutusuna tıklayın, soldan sağa yönünü tersine çevirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms denetimini barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)