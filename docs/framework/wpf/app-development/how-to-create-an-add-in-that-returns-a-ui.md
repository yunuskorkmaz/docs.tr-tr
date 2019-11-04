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
ms.openlocfilehash: d799c91b9abdf7882a0fcd3f0b656eac553b188c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460152"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Nasıl yapılır: UI Döndüren Eklenti Oluşturma
Bu örnek, bir konak WPF tek başına uygulamasına Windows Presentation Foundation (WPF) döndüren bir eklentinin nasıl oluşturulacağını gösterir.  
  
 Eklenti, WPF Kullanıcı denetimi olan bir kullanıcı arabirimi döndürür. Kullanıcı denetiminin içeriği, tıklandığında bir ileti kutusu görüntüleyen tek bir düğmedir. WPF tek başına uygulaması eklentiyi barındırır ve Kullanıcı denetimini (eklenti tarafından döndürülen) ana uygulama penceresinin içeriği olarak görüntüler.  
  
 **Önkoşullar**  
  
 Bu örnek, WPF uzantılarını bu senaryoyu etkinleştiren .NET Framework eklenti modeline vurgular ve şunları varsayar:  
  
- İşlem hattı, eklenti ve konak geliştirme dahil .NET Framework eklenti modeli hakkında bilgi. Bu kavramları tanımıyorsanız, bkz. eklentiler [ve genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Bir işlem hattının, eklentinin ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için bkz. [Izlenecek yol: Genişletilebilir uygulama oluşturma](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- .NET Framework eklenti modeli için WPF uzantıları hakkında bilgi, burada bulunabilir: [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 WPF Kullanıcı arabirimini döndüren bir eklenti oluşturmak için her bir ardışık düzen segmenti, eklentisi ve ana bilgisayar uygulaması için belirli bir kod gerekir.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Bir yöntem, Kullanıcı arabirimi döndürmek için anlaşma tarafından tanımlanmalıdır ve dönüş değeri <xref:System.AddIn.Contract.INativeHandleContract> türünde olmalıdır. Bu, aşağıdaki kodda `IWPFAddInContract` sözleşmesinin `GetAddInUI` yöntemi tarafından gösterilmiştir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü ardışık düzen segmentini uygulama  
 Eklenti Usıs 'yi <xref:System.Windows.FrameworkElement> ' ın alt sınıfları olarak sağladığından, `IWPFAddInView.GetAddInUI` ' i ile ilişkili eklenti görünümündeki Yöntem <xref:System.Windows.FrameworkElement> türünde bir değer döndürmelidir. Aşağıdaki kod, bir arabirim olarak uygulanan, sözleşmenin eklenti görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Eklenti tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract> döndürür, ancak eklenti bir <xref:System.Windows.FrameworkElement> döndürür (eklenti görünümü tarafından belirtilen şekilde). Sonuç olarak, yalıtım sınırını geçmeden önce <xref:System.Windows.FrameworkElement> ' ı bir <xref:System.AddIn.Contract.INativeHandleContract> ' e dönüştürmelidir. Bu iş, aşağıdaki kodda gösterildiği gibi <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>çağırarak, eklenti tarafı bağdaştırıcısı tarafından gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Konak görünümü ardışık düzen segmentini uygulama  
 Ana bilgisayar uygulaması <xref:System.Windows.FrameworkElement> olarak görüntüleyeceği için, konak görünümündeki `IWPFAddInHostView.GetAddInUI` ile ilişkili Yöntem <xref:System.Windows.FrameworkElement> türünde bir değer döndürmelidir. Aşağıdaki kod, bir arabirim olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama  
 Anlaşma yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>döndürür, ancak konak uygulama bir <xref:System.Windows.FrameworkElement> bekler (konak görünümü tarafından belirtildiği gibi). Sonuç olarak, yalıtım sınırını geçirdikten sonra <xref:System.AddIn.Contract.INativeHandleContract> ' ı bir <xref:System.Windows.FrameworkElement> ' e dönüştürülmesi gerekir. Bu iş, aşağıdaki kodda gösterildiği gibi <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>çağırarak konak tarafı bağdaştırıcısı tarafından gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklentiyi uygulama  
 Eklenti tarafı bağdaştırıcısı ve eklenti görünümü oluşturulduğunda, eklenti (`WPFAddIn1.AddIn`), bir <xref:System.Windows.FrameworkElement> nesnesi (Bu örnekte bir <xref:System.Windows.Controls.UserControl>) döndürmek için `IWPFAddInView.GetAddInUI` metodunu uygulamalıdır. <xref:System.Windows.Controls.UserControl>, `AddInUI`uygulanması aşağıdaki kodla gösterilir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Aşağıdaki kodda gösterildiği gibi, eklenti tarafından `IWPFAddInView.GetAddInUI` uygulamasının yeni bir `AddInUI`örneğini döndürmesi gerekir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamasını uygulama  
 Konak tarafı bağdaştırıcısı ve konak görünümü oluşturulduğunda konak uygulama, .NET Framework eklenti modelini kullanarak işlem hattını açabilir, eklentinin bir konak görünümünü alabilir ve `IWPFAddInHostView.GetAddInUI` yöntemini çağırabilir. Bu adımlar aşağıdaki kodda gösterilmiştir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
