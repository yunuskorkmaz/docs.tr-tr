---
title: 'İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: 771c0d972420b929ac757ced684de70d2dc7a58d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>İzlenecek yol: WindowsFormsHost Öğesi Kullanarak Özellikleri Eşleme
Bu kılavuz size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi oluşturma.  
  
-   Uygulama düzenini tanımlama.  
  
-   Yeni bir özellik eşlemesi tanımlama.  
  
-   Varsayılan özellik eşlemesini kaldırma.  
  
-   Varsayılan özellik eşlemesini değiştirme.  
  
-   Varsayılan özellik eşlemesini genişletme.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [WindowsFormsHost Öğesi örneğini kullanarak eşleme özellikleri](http://go.microsoft.com/fwlink/?LinkID=160019).  
  
 İşiniz bittiğinde, eşleme kuramaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-and-set-up-the-project"></a>Oluşturun ve projeyi ayarlamak için  
  
1.  Adlı bir WPF uygulaması projesi oluşturduğunuzda `PropertyMappingWithWfhSample`.  
  
2.  Çözüm Gezgininde WindowsFormsIntegration.dll adlı WindowsFormsIntegration derlemesine başvuru ekleyin.  
  
3.  Çözüm Gezgini'nde System.Drawing ve System.Windows.Forms derlemelerine başvurular ekleyin.  
  
## <a name="defining-the-application-layout"></a>Uygulama düzenini tanımlama  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Uygulamanız tarafından kullanılan temel <xref:System.Windows.Forms.Integration.WindowsFormsHost> konak öğesine bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] denetim.  
  
#### <a name="to-define-the-application-layout"></a>Uygulama düzeni tanımlamak için  
  
1.  Window1.XAML içinde açmak [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
2.  Var olan kodu aşağıdaki kodla değiştirin.  
  
     [!code-xaml[PropertyMappingWithWfhSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]  
  
3.  Window1.xaml.cs'i Kod düzenleyicisinde açın.  
  
4.  Dosyanın üst kısmında, şu ad alanlarından içe aktarın.  
  
     [!code-csharp[PropertyMappingWithWfhSample#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]  
  
## <a name="defining-a-new-property-mapping"></a>Yeni bir özellik eşlemesi tanımlama  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Öğesi birkaç varsayılan özellik eşlemelerini sağlar. Yeni bir özellik eşlemesi çağırarak eklemek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-define-a-new-property-mapping"></a>Yeni bir özellik eşlemesi tanımlamak için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithWfhSample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]  
  
     `AddClipMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.UIElement.Clip%2A> özelliği.  
  
     `OnClipChange` Yöntemi çevirir <xref:System.Windows.UIElement.Clip%2A> özelliğine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> özelliği.  
  
     `Window1_SizeChanged` Yöntemi işler pencerenin <xref:System.Windows.FrameworkElement.SizeChanged> olay ve kırpma bölgesinin uygulama penceresine sığacak şekilde boyutlandırır.  
  
## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırma  
 Varsayılan özellik eşlemesini çağırarak kaldırın <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithWfhSample#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]  
  
     `RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.FrameworkElement.Cursor%2A> özelliği.  
  
## <a name="replacing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini değiştirme  
 Varsayılan eşleme ve arama kaldırarak varsayılan özellik eşlemesini değiştirmek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.WindowsFormsHost> öğenin <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.  
  
#### <a name="to-replace-a-default-property-mapping"></a>Varsayılan özellik eşlemesini değiştirmek için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithWfhSample#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]  
  
     `ReplaceFlowDirectionMapping` Yöntemi için varsayılan eşlemeyi değiştirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği.  
  
     `OnFlowDirectionChange` Yöntemi çevirir <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliğine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> özelliği.  
  
     `cb_CheckedChanged` Yöntemi tanıtıcıları <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayda <xref:System.Windows.Forms.CheckBox> denetim. Atar <xref:System.Windows.FrameworkElement.FlowDirection%2A> özellik değeri temel alarak <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği  
  
## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletme  
 Varsayılan özellik eşleme kullanabilir ve ayrıca kendi eşlemesi ile genişletir.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletmek için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithWfhSample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]  
  
     `ExtendBackgroundMapping` Yöntemi, varolan bir özel özellik Çeviricisi ekler <xref:System.Windows.Controls.Control.Background%2A> özellik eşlemesi.  
  
     `OnBackgroundChange` Yöntemi barındırılan denetimin için belirli bir resim atar <xref:System.Windows.Forms.Control.BackgroundImage%2A> özelliği. `OnBackgroundChange` Yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.  
  
## <a name="initializing-your-property-mappings"></a>Özellik eşlemelerinizin başlatılıyor  
 Daha önce açıklanan yöntemleri çağırarak, özellik eşlemelerini ayarlamak <xref:System.Windows.FrameworkElement.Loaded> olay işleyicisi.  
  
#### <a name="to-initialize-your-property-mappings"></a>Özellik eşlemelerinizin başlatmak için  
  
1.  Tanımı aşağıdaki kodu kopyalayın `Window1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithWfhSample#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]  
  
     `WindowLoaded` Yöntemi tanıtıcıları <xref:System.Windows.FrameworkElement.Loaded> olay ve aşağıdaki başlatmayı gerçekleştirir.  
  
    -   Oluşturur bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> denetim.  
  
    -   Özellik eşlemelerini ayarlamak için önceki örnekte tanımlanan yöntemleri çağırır.  
  
    -   Eşlenen özelliklere ilk değerleri atar.  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın. Etkisini görmek için bu onay kutusuna tıklayın <xref:System.Windows.FrameworkElement.FlowDirection%2A> eşleme. Onay kutusunu işaretlediğinizde düzenini soldan sağa yönünü tersine çevirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: WPF'de Windows Forms Denetimini Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
