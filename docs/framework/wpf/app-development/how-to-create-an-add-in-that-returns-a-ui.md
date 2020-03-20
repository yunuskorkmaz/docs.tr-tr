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
ms.openlocfilehash: f8323fe35555a56d39c1efed649c2aa3fcf17e43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174595"
---
# <a name="how-to-create-an-add-in-that-returns-a-ui"></a>Nasıl yapılır: UI Döndüren Eklenti Oluşturma
Bu örnek, ana bilgisayar WPF bağımsız uygulamasına Windows Sunu Temeli (WPF) döndüren bir eklentinin nasıl oluşturulacağınÝ gösterir.  
  
 Eklenti, WPF kullanıcı denetimi olan bir Kullanıcı Aracı döndürür. Kullanıcı denetiminin içeriği, tıklatıldığında bir ileti kutusu görüntüleyen tek bir düğmedir. WPF bağımsız uygulaması eklentiyi barındırAr ve kullanıcı denetimini (eklenti tarafından döndürülür) ana uygulama penceresinin içeriği olarak görüntüler.  
  
 **Önkoşullar**  
  
 Bu örnek, bu senaryoyu etkinleştiren .NET Framework eklentisi modelindeki WPF uzantılarını vurgular ve aşağıdakileri varsayar:  
  
- Boru hattı, eklenti ve ana bilgisayar geliştirme dahil olmak üzere .NET Framework eklentisi modeli hakkında bilgi. Bu kavramlara aşina değilseniz, [Eklentiler ve Genişletilebilirlik'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))bakın. Bir ardışık hatlar, eklenti ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için [bkz.](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))  
  
- .NET Framework eklenti modeline WPF uzantıları hakkında bilgi, burada bulunabilir: [WPF Eklentiler Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 WPF Kullanıcı Arabirimi döndüren bir eklenti oluşturmak için her bir dizi nial, eklenti ve ana bilgisayar uygulaması için belirli bir kod gerektirir.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme Boru Hattı Segmentinin Uygulanması  
 Bir yöntem, ui'yi döndürmek için sözleşme tarafından tanımlanmalı ve <xref:System.AddIn.Contract.INativeHandleContract>iade değeri türde olmalıdır. Bu, aşağıdaki kodda `GetAddInUI` `IWPFAddInContract` sözleşme yöntemi ile gösterilmiştir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
 [!code-vb[SimpleAddInReturnsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]  
  
<a name="AddInView"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti Görünüm Ardışık Bölüm'e Uygulama  
 Eklenti alt sınıflar olarak sağladığı UIs'leri <xref:System.Windows.FrameworkElement>uyguladığından, eklenti görünümünde ilişkili olan yöntem `IWPFAddInView.GetAddInUI` intifa <xref:System.Windows.FrameworkElement>türünde bir değer döndürmesi gerekir. Aşağıdaki kod, arabirim olarak uygulanan sözleşmenin eklenti görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInViews/IWPFAddInView.cs#addinviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInViews/IWPFAddInView.vb#addinviewcode)]  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Eklenti Bağdaştırıcı Boru Hattı Segmentinin Uygulanması  
 Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak eklenti bir <xref:System.Windows.FrameworkElement> döndürür (eklenti görünümünde belirtildiği gibi). Sonuç olarak, <xref:System.Windows.FrameworkElement> izolasyon sınırını geçmeden <xref:System.AddIn.Contract.INativeHandleContract> önce bir dönüştürülmelidir. Bu çalışma, aşağıdaki kodda gösterildiği gibi, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>yan add-in-side bağdaştırıcı tarafından çağrılar tarafından gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]  
  
<a name="HostView"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana Bilgisayar Görünümü Ardışık Bölüm'e Uygulama  
 Ana bilgisayar uygulaması, <xref:System.Windows.FrameworkElement>ana bilgisayar görünümünde ilişkili olan yöntem `IWPFAddInHostView.GetAddInUI` in türünün <xref:System.Windows.FrameworkElement>bir değerini döndürmesi gerekir. Aşağıdaki kod, arabirim olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostViews/IWPFAddInHostView.cs#hostviewcode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostViews/IWPFAddInHostView.vb#hostviewcode)]  
  
<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Ana Bilgisayar-Yan Bağdaştırıcı Boru Hattı Segmentinin Uygulanması  
 Sözleşme yöntemi bir <xref:System.AddIn.Contract.INativeHandleContract>, ancak ana <xref:System.Windows.FrameworkElement> bilgisayar uygulaması (ana bilgisayar görünümünde belirtildiği gibi) bir bekliyor. Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> izolasyon sınırını geçtikten sonra a <xref:System.Windows.FrameworkElement> dönüştürülmelidir. Bu çalışma, aşağıdaki kodda gösterildiği gibi, ana bilgisayar tarafı bağdaştırıcısı tarafından çağrılarek <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>gerçekleştirilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#hostsideadaptercode)]
 [!code-vb[SimpleAddInReturnsAUISample#HostSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#hostsideadaptercode)]  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Eklentinin Uygulanması  
 Eklenti tarafı bağdaştırıcısı ve oluşturulan eklenti görünümüyle,`WPFAddIn1.AddIn`eklenti ( `IWPFAddInView.GetAddInUI` ) bir <xref:System.Windows.FrameworkElement> nesneyi <xref:System.Windows.Controls.UserControl> (bu örnekte) döndürmek için yöntemi uygulamalıdır. " <xref:System.Windows.Controls.UserControl>, , `AddInUI`uygulanması aşağıdaki kodla gösterilir.  
  
 [!code-xaml[SimpleAddInReturnsAUISample#AddInUIMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml#addinuimarkup)]  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#addinuicodebehind)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#addinuicodebehind)]  
  
 Eklenti `IWPFAddInView.GetAddInUI` tarafından uygulanması sadece aşağıdaki kod da gösterildiği `AddInUI`gibi, yeni bir örnek döndürmek gerekir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/WPFAddIn1/AddIn.cs#addincode)]
 [!code-vb[SimpleAddInReturnsAUISample#AddInCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/WPFAddIn1/AddIn.vb#addincode)]  
  
<a name="App"></a>
## <a name="implementing-the-host-application"></a>Ana Bilgisayar Uygulamasının Uygulanması  
 Ana bilgisayar tarafı bağdaştırıcısı ve ana bilgisayar görünümü oluşturulduğunda, ana bilgisayar uygulaması .NET Framework eklentisi modelini `IWPFAddInHostView.GetAddInUI` kullanarak ardışık alanı açabilir, eklentinin ana bilgisayar görünümünü alabilir ve yöntemi çağırabilir. Bu adımlar aşağıdaki kodda gösterilir.  
  
 [!code-csharp[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/CSharp/Host/MainWindow.xaml.cs#getuicode)]
 [!code-vb[SimpleAddInReturnsAUISample#GetUICode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInReturnsAUISample/VisualBasic/Host/MainWindow.xaml.vb#getuicode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
