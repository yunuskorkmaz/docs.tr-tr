---
title: "İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme"
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
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0db7b9677b5c8c415b6d0b3f49bd149c06843a33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>İzlenecek yol: ElementHost Denetimini Kullanarak Özellikleri Eşleme
Bu kılavuz size nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> eşlemek için özellik [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] özellikleri barındırılan karşılık gelen özelliklere [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] öğesi.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Projeyi oluşturma.  
  
-   Yeni bir özellik eşlemesi tanımlama.  
  
-   Varsayılan özellik eşlemesini kaldırma.  
  
-   Varsayılan özellik eşlemesini genişletme.  
  
 Bu örneklerde gösterilen görevlerin tam kod listesi için bkz: [ElementHost denetimi örneğini kullanarak eşleme özellikleri](http://go.microsoft.com/fwlink/?LinkID=160018).  
  
 İşiniz bittiğinde, eşleme kuramaz [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] karşılık gelen özellikleri [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] barındırılan öğe özellikleri.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:  
  
-   [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
  
#### <a name="to-create-the-project"></a>Proje oluşturmak için  
  
1.  Oluşturma bir [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] adlı uygulama projesi `PropertyMappingWithElementHost`. Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Çözüm Gezgini'nde, aşağıdaki başvurular ekleyin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] derlemeler.  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   WindowsFormsIntegration  
  
3.  Üstüne aşağıdaki kodu kopyalayın `Form1` kod dosyası.  
  
     [!code-csharp[PropertyMappingWithElementHost#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]  
  
4.  Açık `Form1` Windows Forms Tasarımcısı'nda. Bir olay işleyicisi eklemek için form çift <xref:System.Windows.Forms.Form.Load> olay.  
  
5.  Dönmek için Windows Form Tasarımcısı ve form için bir olay işleyicisi ekleme <xref:System.Windows.Forms.Control.Resize> olay. Daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri kullanarak Tasarımcı](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
6.  Bildirme bir <xref:System.Windows.Forms.Integration.ElementHost> alanındaki `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]  
  
## <a name="defining-new-property-mappings"></a>Yeni özellik eşlemesi tanımlama  
 <xref:System.Windows.Forms.Integration.ElementHost> Denetimi birkaç varsayılan özellik eşlemelerini sağlar. Yeni bir özellik eşlemesi çağırarak eklemek <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> yöntemi <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-define-new-property-mappings"></a>Yeni Özellik eşlemeleri tanımlamak için  
  
1.  Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]  
  
     `AddMarginMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Margin%2A> özelliği.  
  
     `OnMarginChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Margin%2A> özelliğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement.Margin%2A> özelliği.  
  
2.  Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]  
  
     `AddRegionMapping` Yöntemi ekler için yeni bir eşleme <xref:System.Windows.Forms.Control.Region%2A> özelliği.  
  
     `OnRegionChange` Yöntemi çevirir <xref:System.Windows.Forms.Control.Region%2A> özelliğine [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.Clip%2A> özelliği.  
  
     `Form1_Resize` Yöntemi işler formun <xref:System.Windows.Forms.Control.Resize> olay ve barındırılan öğeyi sığdıracak şekilde kırpma bölgesini boyutlandırır.  
  
## <a name="removing-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırma  
 Varsayılan özellik eşlemesini çağırarak kaldırın <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> yöntemi <xref:System.Windows.Forms.Integration.ElementHost> denetimin <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>.  
  
#### <a name="to-remove-a-default-property-mapping"></a>Varsayılan özellik eşlemesini kaldırmak için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]  
  
     `RemoveCursorMapping` Yöntemi için varsayılan eşlemeyi siler <xref:System.Windows.Forms.Control.Cursor%2A> özelliği.  
  
## <a name="extending-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletme  
 Varsayılan özellik eşleme kullanabilir ve ayrıca kendi eşlemesi ile genişletir.  
  
#### <a name="to-extend-a-default-property-mapping"></a>Varsayılan özellik eşlemesini genişletmek için  
  
-   Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]  
  
     `ExtendBackColorMapping` Yöntemi, varolan bir özel özellik Çeviricisi ekler <xref:System.Windows.Forms.Control.BackColor%2A> özellik eşlemesi.  
  
     `OnBackColorChange` Yöntemi barındırılan denetimin için belirli bir resim atar <xref:System.Windows.Controls.Control.Background%2A> özelliği. `OnBackColorChange` Yöntemi, varsayılan özellik eşleme uygulandıktan sonra çağrılır.  
  
## <a name="initializing-your-property-mappings"></a>Özellik eşlemelerinizin başlatılıyor  
  
#### <a name="to-initialize-your-property-mappings"></a>Özellik eşlemelerinizin başlatmak için  
  
1.  Tanımı aşağıdaki kodu kopyalayın `Form1` sınıfı.  
  
     [!code-csharp[PropertyMappingWithElementHost#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]  
  
     `Form1_Load` Yöntemi tanıtıcıları <xref:System.Windows.Forms.Form.Load> olay ve aşağıdaki başlatmayı gerçekleştirir.  
  
    -   Oluşturur bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> öğesi.  
  
    -   Özellik eşlemelerini ayarlamak için önceki örnekte tanımlanan yöntemleri çağırır.  
  
    -   Eşlenen özelliklere ilk değerleri atar.  
  
2.  Derleme ve uygulamayı çalıştırmak için F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Windows Forms ve WPF Özelliğini Eşleme](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)  
 [WPF Tasarımcısı](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [İzlenecek yol: WPF Bileşik Denetimini Windows Forms İçinde Barındırma](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
