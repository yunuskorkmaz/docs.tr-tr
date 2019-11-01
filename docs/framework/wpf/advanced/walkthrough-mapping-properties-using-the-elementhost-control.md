---
title: 'İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7d1cf353f7e6c4b87c13598e7e6029960cd0f715
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197822"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme

Bu izlenecek yol, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özelliklerini barındırılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesinde karşılık gelen özelliklerle eşlemek için <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> özelliğini nasıl kullanacağınızı gösterir.

Bu izlenecek yolda gösterilen görevler şunlardır:

- Proje oluşturuluyor.

- Yeni özellik eşlemesi tanımlama.

- Varsayılan özellik eşlemesi kaldırılıyor.

- Varsayılan özellik eşlemesini genişletme.

Bu kılavuzda gösterilen görevlerin tüm kod listesi için bkz. [ElementHost denetim örneğini kullanarak özellikleri eşleme](https://go.microsoft.com/fwlink/?LinkID=160018).

İşiniz bittiğinde, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özelliklerini barındırılan bir öğede karşılık gelen [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleriyle eşleyebilirsiniz.

## <a name="prerequisites"></a>Prerequisites

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Visual Studio 2017

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-the-project"></a>Proje oluşturmak için

1. `PropertyMappingWithElementHost`adlı **Windows Forms bir uygulama** projesi oluşturun.

2. **Çözüm Gezgini**, aşağıdaki [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemelerine başvuruları ekleyin.

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. Aşağıdaki kodu `Form1` kod dosyasının en üstüne kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Windows Form Tasarımcısı `Form1` açın. <xref:System.Windows.Forms.Form.Load> olayına bir olay işleyicisi eklemek için forma çift tıklayın.

5. Windows Form Tasarımcısı dönüp formun <xref:System.Windows.Forms.Control.Resize> olayı için bir olay işleyicisi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: tasarımcı kullanarak olay Işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. `Form1` sınıfında bir <xref:System.Windows.Forms.Integration.ElementHost> alanı bildirin.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Yeni özellik eşlemelerini tanımlama

<xref:System.Windows.Forms.Integration.ElementHost> denetimi, çeşitli varsayılan özellik eşlemeleri sağlar. <xref:System.Windows.Forms.Integration.ElementHost> denetiminin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemini çağırarak yeni bir özellik eşlemesi eklersiniz.

### <a name="to-define-new-property-mappings"></a>Yeni özellik eşlemelerini tanımlamak için

1. Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping` yöntemi <xref:System.Windows.Forms.Control.Margin%2A> özelliği için yeni bir eşleme ekler.

     `OnMarginChange` yöntemi, <xref:System.Windows.Forms.Control.Margin%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> özelliğine çevirir.

2. Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping` yöntemi <xref:System.Windows.Forms.Control.Region%2A> özelliği için yeni bir eşleme ekler.

     `OnRegionChange` yöntemi, <xref:System.Windows.Forms.Control.Region%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> özelliğine çevirir.

     `Form1_Resize` yöntemi, formun <xref:System.Windows.Forms.Control.Resize> olayını işler ve kırpma bölgesini barındırılan öğeye uyacak şekilde boyutlandırır.

## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırma

<xref:System.Windows.Forms.Integration.ElementHost> denetiminin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A><xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemini çağırarak varsayılan özellik eşlemesini kaldırın.

### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için

- Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping` yöntemi <xref:System.Windows.Forms.Control.Cursor%2A> özelliğinin varsayılan eşlemesini siler.

## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletme

Varsayılan bir özellik eşlemesini kullanabilir ve ayrıca kendi eşlemesiyle genişletebilirsiniz.

### <a name="to-extend-a-default-property-mapping"></a>Varsayılan bir özellik eşlemesini genişletmek için

- Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping` yöntemi, varolan <xref:System.Windows.Forms.Control.BackColor%2A> özellik eşlemesine özel bir özellik Çeviricisi ekler.

     `OnBackColorChange` yöntemi, barındırılan denetimin <xref:System.Windows.Controls.Control.Background%2A> özelliğine belirli bir görüntü atar. `OnBackColorChange` yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.

## <a name="initialize-your-property-mappings"></a>Özellik Eşlemelerinizi başlatın

1. Aşağıdaki kodu `Form1` sınıfının tanımına kopyalayın.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load` yöntemi <xref:System.Windows.Forms.Form.Load> olayını işler ve aşağıdaki başlatmayı gerçekleştirir.

    - Bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> öğesi oluşturur.

    - Özellik eşlemelerini ayarlamak için izlenecek yolda daha önce tanımladığınız yöntemleri çağırır.

    - Eşlenen özelliklere ilk değerleri atar.

2. Uygulamayı derlemek ve çalıştırmak için F5 tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms ve WPF Özelliğini Eşleme](windows-forms-and-wpf-property-mapping.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
