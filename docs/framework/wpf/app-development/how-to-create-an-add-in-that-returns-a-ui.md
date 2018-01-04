---
title: "Nasıl yapılır: UI Döndüren Eklenti Oluşturma"
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
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 361983c4e2b392cdf8410fdb1193a56f6d26d067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Nasıl yapılır: UI Döndüren Eklenti Oluşturma
Bu örnek döndüren bir eklenti oluşturmak nasıl gösterir bir [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] bir ana bilgisayara [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] tek başına uygulama.  
  
 Eklenti döndürür bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] diğer bir deyişle bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kullanıcı denetimi. Tek bir düğme, tıklatıldığında, kullanıcı denetimi içeriği olan bir ileti kutusu görüntüler. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Bağımsız uygulaması eklentiyi barındırır ve (eklenti tarafından döndürülen) kullanıcı denetimini ana uygulama penceresi içeriği olarak görüntüler.  
  
 **Önkoşullar**  
  
 Bu örnek vurgular [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aşağıdakileri varsayar ve bu senaryo etkinleştiren eklenti modeli:  
  
-   Bilgisi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ardışık düzen, eklenti ve konak geliştirme de dahil olmak üzere eklenti modeli. Bu kavramları tanımıyorsanız bkz [eklentiler ve genişletilebilirlik](../../../../docs/framework/add-ins/index.md). Bir ardışık düzen, eklenti ve bir ana bilgisayar uygulaması uygulanmasını gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](../../../../docs/framework/add-ins/walkthrough-create-extensible-app.md).  
  
-   Bilgisi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] uzantıları [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] , burada bulunabilir eklenti modeli: [WPF eklentileri genel bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 Döndüren bir eklenti oluşturmak için bir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , her ardışık düzen segmenti, eklenti ve konak uygulama için belirli bir kod gerekir.  
    
  
<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Bir yöntem döndürmek için anlaşma tarafından tanımlanmalıdır bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ve onun dönüş değeri türü olmalıdır <xref:System.AddIn.Contract.INativeHandleContract>. Bu tarafından gösterilen `GetAddInUI` yöntemi `IWPFAddInContract` aşağıdaki kodda sözleşme.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü ardışık düzen segmentini uygulama  
 Eklenti uyguladığından [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] alt sınıflarının sağlar <xref:System.Windows.FrameworkElement>, için karşılık gelen eklenti görünümü üzerindeki yöntem `IWPFAddInView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>. Aşağıdaki kodu arabirim uygulanan anlaşmanın eklenti görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Ekleme tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Anlaşma yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti döndürür bir <xref:System.Windows.FrameworkElement> (eklenti görünümü tarafından belirtildiği gibi). Sonuç olarak, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce. Bu iş çağırarak Ekle tarafı bağdaştırıcı tarafından gerçekleştirilen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana görünüm ardışık düzen segmentini uygulama  
 Ana bilgisayar uygulamasını görüntüler çünkü bir <xref:System.Windows.FrameworkElement>, için karşılık gelen ana görünümü üzerindeki yöntem `IWPFAddInHostView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>. Aşağıdaki kodu arabirim uygulanan anlaşmanın konak görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Anlaşma yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak konak uygulama bekler bir <xref:System.Windows.FrameworkElement> (ana görünümü tarafından belirtildiği gibi). Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmesinden sonra. Bu iş çağırarak konak tarafı bağdaştırıcı tarafından gerçekleştirilen <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklenti uygulama  
 Oluşturulan, eklenti görünümü eklenti ve Ekle tarafı bağdaştırıcı (`WPFAddIn1.AddIn`) uygulamalıdır `IWPFAddInView.GetAddInUI` döndürülecek yöntemi bir <xref:System.Windows.FrameworkElement> nesne (bir <xref:System.Windows.Controls.UserControl> Bu örnekte). Uygulaması <xref:System.Windows.Controls.UserControl>, `AddInUI`, aşağıdaki kodda gösterilir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Uygulaması `IWPFAddInView.GetAddInUI` eklenti tarafından yalnızca yeni bir örneğini döndürmesi gerekir `AddInUI`aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama  
 Konak tarafı bağdaştırıcısı ile oluşturulan ana görünüm, ana bilgisayar uygulamasını kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Eklenti ardışık düzeni açın, eklenti ve çağrı konak görünümünü edinmek için model `IWPFAddInHostView.GetAddInUI` yöntemi. Bu adımları aşağıdaki kodda gösterilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eklentiler ve Genişletilebilirlik](../../../../docs/framework/add-ins/index.md)  
 [WPF Eklentilerine Genel Bakış](../../../../docs/framework/wpf/app-development/wpf-add-ins-overview.md)
