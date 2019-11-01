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
ms.openlocfilehash: c8a83dd3f7327d00979431ca7fa801ff642a4eef
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197804"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme

Bu izlenecek yol, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki ilgili özelliklerle eşlemek için <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> özelliğini nasıl kullanacağınızı gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Proje oluşturuluyor.

- Uygulama yerleşimini tanımlama.

- Yeni özellik eşlemesi tanımlama.

- Varsayılan özellik eşlemesi kaldırılıyor.

- Varsayılan özellik eşlemesini değiştirme.

- Varsayılan özellik eşlemesini genişletme.

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [WindowsFormsHost öğesi örneği kullanılarak özellikleri eşleme](https://go.microsoft.com/fwlink/?LinkID=160019).

İşiniz bittiğinde, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özelliklerini barındırılan bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimindeki ilgili özelliklerle eşleyebilirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Projeyi oluşturma ve ayarlama

1. `PropertyMappingWithWfhSample`adlı bir **WPF uygulaması** projesi oluşturun.

2. **Çözüm Gezgini**' de, WindowsFormsIntegration. dll adlı WindowsFormsIntegration derlemesine bir başvuru ekleyin.

3. **Çözüm Gezgini**, System. Drawing ve System. Windows. Forms derlemelerine başvuruları ekleyin.

## <a name="defining-the-application-layout"></a>Uygulama yerleşimini tanımlama

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]tabanlı uygulama bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetimini barındırmak için <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesini kullanır.

### <a name="to-define-the-application-layout"></a>Uygulama yerleşimini tanımlamak için

1. [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]Window1. xaml ' i açın.

2. Mevcut kodu aşağıdaki kodla değiştirin.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Kod düzenleyicisinde Window1.xaml.cs öğesini açın.

4. Dosyanın en üstüne aşağıdaki ad alanlarını içeri aktarın.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Yeni özellik eşlemesi tanımlama

<xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesi, çeşitli varsayılan özellik eşlemeleri sağlar. <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemini çağırarak yeni bir özellik eşlemesi eklersiniz.

### <a name="to-define-a-new-property-mapping"></a>Yeni bir özellik eşlemesi tanımlamak için

- Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     `AddClipMapping` yöntemi <xref:System.Windows.UIElement.Clip%2A> özelliği için yeni bir eşleme ekler.

     `OnClipChange` yöntemi, <xref:System.Windows.UIElement.Clip%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.Region%2A> özelliğine çevirir.

     `Window1_SizeChanged` yöntemi pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olayını işler ve kırpma bölgesini uygulama penceresine uyacak şekilde boyutlandırır.

## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırma

<xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemini çağırarak varsayılan özellik eşlemesini kaldırın.

### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için

- Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     `RemoveCursorMapping` yöntemi <xref:System.Windows.FrameworkElement.Cursor%2A> özelliğinin varsayılan eşlemesini siler.

## <a name="replacing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini değiştirme

Varsayılan eşlemeyi kaldırarak ve <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğesinin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi çağırarak varsayılan özellik eşlemesini değiştirin.

### <a name="to-replace-a-default-property-mapping"></a>Varsayılan bir özellik eşlemesini değiştirmek için

- Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     `ReplaceFlowDirectionMapping` yöntemi <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğinin varsayılan eşlemesinin yerini alır.

     `OnFlowDirectionChange` yöntemi, <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.Control.RightToLeft%2A> özelliğine çevirir.

     `cb_CheckedChanged` yöntemi <xref:System.Windows.Forms.CheckBox> denetimindeki <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayını işler. <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğinin değerine göre <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğini atar

## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletme

Varsayılan bir özellik eşlemesini kullanabilir ve ayrıca kendi eşlemesiyle genişletebilirsiniz.

### <a name="to-extend-a-default-property-mapping"></a>Varsayılan bir özellik eşlemesini genişletmek için

- Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     `ExtendBackgroundMapping` yöntemi, varolan <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesine özel bir özellik Çeviricisi ekler.

     `OnBackgroundChange` yöntemi, barındırılan denetimin <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliğine belirli bir görüntü atar. `OnBackgroundChange` yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.

## <a name="initializing-your-property-mappings"></a>Özellik Eşlemelerinizi Başlatma

Daha önce açıklanan yöntemleri <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisinde çağırarak özellik eşlemelerinizi ayarlayın.

### <a name="to-initialize-your-property-mappings"></a>Özellik Eşlemelerinizi başlatmak için

1. Aşağıdaki kodu `Window1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     `WindowLoaded` yöntemi <xref:System.Windows.FrameworkElement.Loaded> olayını işler ve aşağıdaki başlatmayı gerçekleştirir.

    - Bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.CheckBox> denetimi oluşturur.

    - Özellik eşlemelerini ayarlamak için izlenecek yolda daha önce tanımladığınız yöntemleri çağırır.

    - Eşlenen özelliklere ilk değerleri atar.

2. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın. <xref:System.Windows.FrameworkElement.FlowDirection%2A> eşlemenin etkisini görmek için onay kutusuna tıklayın. Onay kutusuna tıkladığınızda, düzen sol sağ yönünü tersine çevirir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
