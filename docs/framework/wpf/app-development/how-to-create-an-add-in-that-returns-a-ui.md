---
title: 'Nasıl yapılır: UI Döndüren Eklenti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that returns a UI [WPF]
- implementing add-in pipeline segments [WPF]
- add-in [WPF], returns a UI
ms.assetid: 57f274b7-4c66-4b72-92eb-81939a393776
ms.openlocfilehash: faed11bb02037ea42b31402d431e1bcdd8b70339
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115758"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Nasıl yapılır: UI Döndüren Eklenti Oluşturma
Bu örnek, bir Windows Presentation Foundation (WPF) bir konak WPF tek başına uygulama döndüren bir eklenti oluşturma işlemi gösterilmektedir.  
  
 Eklentinin bir WPF kullanıcı denetimi olan bir kullanıcı Arabirimi döndürür. Tek bir düğme, tıklandığında, kullanıcı denetiminin içeriği olan bir ileti kutusu görüntüler. WPF tek başına uygulama eklenti barındırır ve (eklenti tarafından döndürülen) kullanıcı denetimi ana uygulama penceresini içeriğini görüntüler.  
  
 **Önkoşullar**  
  
 Bu örnekte, bu senaryoyu WPF uzantıları için .NET Framework eklenti modeli vurgular ve aşağıdaki varsayar:  
  
-   Bilgi işlem hattı, eklenti ve konak geliştirme gibi .NET Framework eklenti modeli, sahibi. Bu kavramları alışkın değilseniz bkz [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Bir işlem hattı, bir eklenti ve ana bilgisayar uygulamasına uygulanışı gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](../../add-ins/walkthrough-create-extensible-app.md).  
  
-   WPF uzantıları için burada bulunan .NET Framework eklenti modeli bilgi: [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 Bir WPF UI döndüren eklenti oluşturmak için her işlem hattı segment, eklenti ve ana bilgisayar uygulaması için özel kod gerektirir.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Bir yöntem tarafından bir kullanıcı Arabirimi döndürmek için anlaşma tanımlanmalıdır ve dönüş değerinin türü olmalıdır <xref:System.AddIn.Contract.INativeHandleContract>. Bu tarafından gösterilmiştir `GetAddInUI` yöntemi `IWPFAddInContract` aşağıdaki kodda.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü işlem hattı segmentini uygulama  
 Eklenti uyguladığından [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] alt sınıfları sağlar <xref:System.Windows.FrameworkElement>, belirtilirler eklenti görünümü metodunda `IWPFAddInView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>. Aşağıdaki kod, bir arabirim uygulanan sözleşme, eklenti görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Ekleme tarafı bağdaştırıcısı işlem hattı segmentini uygulama  
 Sözleşme yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti döndürür bir <xref:System.Windows.FrameworkElement> (eklenti görünümü belirtildiği gibi). Sonuç olarak, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce. Bu iş tarafından Ekle tarafı bağdaştırıcısı çağrılarak gerçekleştirilir <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana görünüm ardışık düzen segmentini uygulama  
 Ana bilgisayar uygulaması görüntüleyeceği için bir <xref:System.Windows.FrameworkElement>, yöntem için karşılık gelen ana görünümünde `IWPFAddInHostView.GetAddInUI` türünde bir değer döndürmelidir <xref:System.Windows.FrameworkElement>. Aşağıdaki kod, bir arabirim uygulanan sözleşme ana görünümünde gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı işlem hattı segmentini uygulama  
 Sözleşme yöntemi döndürür bir <xref:System.AddIn.Contract.INativeHandleContract>, ana bilgisayar uygulaması bekliyor, ancak bir <xref:System.Windows.FrameworkElement> (ana görünümünde tarafından belirtildiği gibi). Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> yalıtım sınırı geçmesinden sonra. Bu iş tarafından konak tarafı bağdaştırıcısı çağrılarak gerçekleştirilir <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklenti uygulama  
 Oluşturulan, eklenti görünümü eklenti ve Ekle tarafı bağdaştırıcısı (`WPFAddIn1.AddIn`) uygulamalıdır `IWPFAddInView.GetAddInUI` döndürülecek yöntemi bir <xref:System.Windows.FrameworkElement> nesne (bir <xref:System.Windows.Controls.UserControl> Bu örnekte). Uygulamasını <xref:System.Windows.Controls.UserControl>, `AddInUI`, aşağıdaki kodda gösterilmiştir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Uygulamasını `IWPFAddInView.GetAddInUI` eklenti tarafından yeni bir örneğini döndürülecek yalnızca erişmesi `AddInUI`aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama  
 Konak tarafı bağdaştırıcısı ile oluşturulan ana görünümünde, konak uygulama .NET Framework eklenti modeli kullanabileceğiniz işlem hattı açmak için bir ana bilgisayar görünümü eklenti ve çağrı alma `IWPFAddInHostView.GetAddInUI` yöntemi. Aşağıdaki kodda adımları gösterilmektedir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
