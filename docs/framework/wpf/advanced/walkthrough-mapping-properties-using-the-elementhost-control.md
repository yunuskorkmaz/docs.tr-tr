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
ms.openlocfilehash: 34119d889c8d6600fdda12cac33192c32d8e0fa6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467130"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme

Bu izlenecek yol size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] barındırılan karşılık gelen özelliklere özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

-   Proje oluşturuluyor.

-   Yeni bir özellik eşlemesi tanımlama.

-   Varsayılan özellik eşlemesi kaldırılıyor.

-   Varsayılan özellik eşlemesi genişletme.

Bu izlenecek yolda gösterilen görevler tam kod listesi için bkz. [ElementHost denetimi örneğini kullanarak eşleme özelliklerini](https://go.microsoft.com/fwlink/?LinkID=160018).

Bitirdiğiniz zaman, eşlemek mümkün olmayacak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karşılık gelen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan bir öğedeki özellikleri.

## <a name="prerequisites"></a>Önkoşullar

Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

-   Visual Studio 2017

## <a name="creating-the-project"></a>Projeyi Oluşturma

### <a name="to-create-the-project"></a>Proje oluşturmak için

1.  Oluşturma bir **Windows Forms uygulaması** adlı proje `PropertyMappingWithElementHost`.

2.  İçinde **Çözüm Gezgini**, aşağıdaki başvuruları ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler.

    -   PresentationCore

    -   PresentationFramework

    -   WindowsBase

    -   WindowsFormsIntegration

3.  Üstüne aşağıdaki kodu kopyalayın `Form1` kod dosyası.

     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4.  Açık `Form1` Windows Forms Tasarımcısı'nda. Bir olay işleyicisi eklemek için formu <xref:System.Windows.Forms.Form.Load> olay.

5.  Windows Forms Tasarımcısı'na dönün ve form için bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Resize> olay. Daha fazla bilgi için [nasıl yapılır: olay işleyicileri kullanarak Tasarımcı](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).

6.  Bildirme bir <xref:System.Windows.Forms.Integration.ElementHost> alanındaki `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Yeni Özellik eşlemeleri tanımlama

<xref:System.Windows.Forms.Integration.ElementHost> Denetim birkaç varsayılan özellik eşlemeleri sağlar. Çağırarak yeni bir özellik eşlemesi Ekle <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> metodunda <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-define-new-property-mappings"></a>Yeni Özellik eşlemeleri tanımlamak için

1.  Tanımı aşağıdaki kodu kopyalayarak `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     `AddMarginMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Margin%2A> özelliği.

     `OnMarginChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Margin%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> özelliği.

2.  Tanımı aşağıdaki kodu kopyalayarak `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     `AddRegionMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Region%2A> özelliği.

     `OnRegionChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Region%2A> özelliğini [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> özelliği.

     `Form1_Resize` Yöntemi işler formun <xref:System.Windows.Forms.Control.Resize> olay ve kırpma bölgesinin barındırılan uyacak şekilde boyutları.

## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesi kaldırılıyor

Çağırarak varsayılan özellik eşlemesini kaldırma <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> metodunda <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için

-   Tanımı aşağıdaki kodu kopyalayarak `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     `RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.Forms.Control.Cursor%2A> özelliği.

## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesi genişletme

Varsayılan özellik eşlemesini ve ayrıca kendi eşleme ile genişletmek kullanabilirsiniz.

### <a name="to-extend-a-default-property-mapping"></a>Varsayılan özellik eşlemesi genişletmek için

-   Tanımı aşağıdaki kodu kopyalayarak `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     `ExtendBackColorMapping` Yöntemi, varolan bir özel özellik translator ekler <xref:System.Windows.Forms.Control.BackColor%2A> özellik eşlemesi.

     `OnBackColorChange` Yöntemi barındırılan denetim için belirli bir görüntünün atar <xref:System.Windows.Controls.Control.Background%2A> özelliği. `OnBackColorChange` Yöntemi, varsayılan özellik eşlemesi uygulandıktan sonra çağrılır.

## <a name="initialize-your-property-mappings"></a>Özellik eşlemelerinizin Başlat

1.  Tanımı aşağıdaki kodu kopyalayarak `Form1` sınıfı.

     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     `Form1_Load` Yöntemi tanıtıcıları <xref:System.Windows.Forms.Form.Load> olay ve aşağıdaki başlatmaya gerçekleştirir.

    -   Oluşturur bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> öğesi.

    -   Özellik eşlemelerini ayarlamak için daha önce izlenecek içinde tanımlanan yöntemleri çağırır.

    -   Eşlenen özelliklere başlangıç değerleri atar.

2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
- [Visual Studio’da XAML tasarlama](/visualstudio/designers/designing-xaml-in-visual-studio)
- [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)