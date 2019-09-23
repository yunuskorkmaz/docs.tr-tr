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
ms.openlocfilehash: 1886703e089ed538f68a7221906d815a8ae72076
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182664"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Nasıl yapılır: UI Döndüren Eklenti Oluşturma
Bu örnek, bir konak WPF tek başına uygulamasına Windows Presentation Foundation (WPF) döndüren bir eklentinin nasıl oluşturulacağını gösterir.  
  
 Eklenti, WPF Kullanıcı denetimi olan bir kullanıcı arabirimi döndürür. Kullanıcı denetiminin içeriği, tıklandığında bir ileti kutusu görüntüleyen tek bir düğmedir. WPF tek başına uygulaması eklentiyi barındırır ve Kullanıcı denetimini (eklenti tarafından döndürülen) ana uygulama penceresinin içeriği olarak görüntüler.  
  
 **Önkoşullar  
  
 Bu örnek, WPF uzantılarını bu senaryoyu etkinleştiren .NET Framework eklenti modeline vurgular ve şunları varsayar:  
  
- İşlem hattı, eklenti ve konak geliştirme dahil .NET Framework eklenti modeli hakkında bilgi. Bu kavramları tanımıyorsanız, bkz. eklentiler [ve genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Bir işlem hattının, eklentinin ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için bkz [. İzlenecek yol: Genişletilebilir bir uygulama](../../add-ins/walkthrough-create-extensible-app.md)oluşturma.  
  
- .NET Framework eklenti modeli için WPF uzantıları hakkında bilgi edinebilirsiniz, burada bulunabilir: [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 WPF Kullanıcı arabirimini döndüren bir eklenti oluşturmak için her bir ardışık düzen segmenti, eklentisi ve ana bilgisayar uygulaması için belirli bir kod gerekir.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Bir yöntem, bir kullanıcı arabirimi döndürmek için sözleşme tarafından tanımlanmalıdır ve dönüş değeri türünde <xref:System.AddIn.Contract.INativeHandleContract>olmalıdır. Bu, aşağıdaki koddaki `GetAddInUI` `IWPFAddInContract` sözleşmenin yöntemi tarafından gösterilmiştir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü ardışık düzen segmentini uygulama  
 Eklenti, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] öğesinin <xref:System.Windows.FrameworkElement>alt sınıfları olarak sağladığından, ilişkili `IWPFAddInView.GetAddInUI` eklenti görünümündeki yöntemi türünde <xref:System.Windows.FrameworkElement>bir değer döndürmelidir. Aşağıdaki kod, bir arabirim olarak uygulanan, sözleşmenin eklenti görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Eklenti tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Anlaşma yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>döndürür, ancak eklenti bir <xref:System.Windows.FrameworkElement> (eklenti görünümü tarafından belirtildiği gibi) döndürür. Sonuç olarak, <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmeden <xref:System.AddIn.Contract.INativeHandleContract> önce ' a dönüştürülmesi gerekir. Bu iş, aşağıdaki kodda gösterildiği gibi, çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>eklenti bağdaştırıcısı tarafından gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Konak görünümü ardışık düzen segmentini uygulama  
 Konak uygulama bir <xref:System.Windows.FrameworkElement>olarak görüntüleyeceği için, konak görünümündeki, ile `IWPFAddInHostView.GetAddInUI` ilişkili olan yöntemi türünde <xref:System.Windows.FrameworkElement>bir değer döndürmelidir. Aşağıdaki kod, bir arabirim olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Anlaşma yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>döndürür, ancak konak uygulama bir <xref:System.Windows.FrameworkElement> (konak görünümü tarafından belirtildiği gibi) bekler. Sonuç olarak <xref:System.AddIn.Contract.INativeHandleContract> , yalıtım sınırı geçtikten <xref:System.Windows.FrameworkElement> sonra öğesine dönüştürülmelidir. Bu iş, aşağıdaki kodda gösterildiği gibi çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>konak tarafı bağdaştırıcısı tarafından gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklentiyi uygulama  
 Eklenti tarafı bağdaştırıcısı ve eklenti görünümü oluşturulduğunda,`WPFAddIn1.AddIn`eklenti () bir <xref:System.Windows.FrameworkElement> nesne <xref:System.Windows.Controls.UserControl> döndürmek için `IWPFAddInView.GetAddInUI` yöntemini uygulamalıdır (Bu örnekte,). ,, ' Nin <xref:System.Windows.Controls.UserControl> `AddInUI`uygulanması aşağıdaki kodla gösterilir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Eklenti `IWPFAddInView.GetAddInUI` tarafından uygulanması, aşağıdaki kodda gösterildiği gibi yalnızca yeni bir `AddInUI`örneğini döndürmelidir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamasını uygulama  
 Konak tarafı bağdaştırıcısı ve konak görünümü oluşturulduğunda konak uygulama, .NET Framework eklenti modelini kullanarak işlem hattını açabilir, eklentinin bir konak görünümünü alabilir ve `IWPFAddInHostView.GetAddInUI` metodunu çağırabilir. Bu adımlar aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
