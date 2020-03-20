---
title: 'Nasıl yapılır: UI Olan Eklenti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 339231031b9e57b9f00a2aeb6fbbde8ad66c1ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141035"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Nasıl yapılır: UI Olan Eklenti Oluşturma
Bu örnek, WPF bağımsız bir uygulama tarafından barındırılan bir Windows Sunu Temeli (WPF) olan bir eklentinin nasıl oluşturulacağınÝ gösterir.  
  
 Eklenti, WPF kullanıcı denetimi olan bir kullanıcı aracıdır. Kullanıcı denetiminin içeriği, tıklatıldığında bir ileti kutusu görüntüleyen tek bir düğmedir. WPF bağımsız uygulaması, eklenti Kullanıcı UI'sini ana uygulama penceresinin içeriği olarak barındırar.  
  
 **Önkoşullar**  
  
 Bu örnek, bu senaryoyu etkinleştiren .NET Framework eklentisi modelindeki WPF uzantılarını vurgular ve aşağıdakileri varsayar:  
  
- Boru hattı, eklenti ve ana bilgisayar geliştirme dahil olmak üzere .NET Framework eklentisi modeli hakkında bilgi. Bu kavramlara aşina değilseniz, [Eklentiler ve Genişletilebilirlik'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))bakın. Bir ardışık hatlar, eklenti ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))  
  
- .NET Framework eklentisi modelindeki WPF uzantıları hakkında bilgi. [Bkz. WPF Eklentileri Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 WPF Kullanıcı Arabirimi olan bir eklenti oluşturmak için her bir dizini, eklenti ve ana bilgisayar uygulaması için özel kod gerektirir.  

<a name="Contract"></a>
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme Boru Hattı Segmentinin Uygulanması

Bir eklenti bir UI olduğunda, eklenti için sözleşme uygulaması <xref:System.AddIn.Contract.INativeHandleContract>gerekir. Örnekte, `IWPFAddInContract` aşağıdaki <xref:System.AddIn.Contract.INativeHandleContract>kodda gösterildiği gibi uygular.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti Görünüm Ardışık Bölüm'e Uygulama

Eklenti <xref:System.Windows.FrameworkElement> türünün bir alt sınıfı olarak uygulandığından, eklenti görünümünün de alt <xref:System.Windows.FrameworkElement>sınıf olması gerekir. Aşağıdaki kod, `WPFAddInView` sınıf olarak uygulanan sözleşmenin eklenti görünümünü gösterir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Burada, eklenti <xref:System.Windows.Controls.UserControl>görünümü. Sonuç olarak, eklenti UI da <xref:System.Windows.Controls.UserControl>türetilmelidir.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Eklenti Bağdaştırıcı Boru Hattı Segmentinin Uygulanması

Sözleşme bir <xref:System.AddIn.Contract.INativeHandleContract>iken, eklenti bir <xref:System.Windows.FrameworkElement> (eklenti görünüm ardışık segmenttarafından belirtildiği gibi). Bu nedenle, yalıtım sınırını <xref:System.AddIn.Contract.INativeHandleContract> geçmeden önce bir <xref:System.Windows.FrameworkElement> dönüştürülmelidir. Bu çalışma, aşağıdaki kodda gösterildiği gibi, <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>yan add-in-side bağdaştırıcı tarafından çağrılar tarafından gerçekleştirilir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

Eklentinin bir UI döndürdüğü eklenti modelinde (bkz. bir [UI döndüren eklenti oluştur),](how-to-create-an-add-in-that-returns-a-ui.md)eklenti <xref:System.Windows.FrameworkElement> bağdaştırıcısı arayarak bir <xref:System.AddIn.Contract.INativeHandleContract> eklentiye <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>dönüştürülür. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>kod çağırmak için yazmak için bir yöntem uygulamak gerekir rağmen, bu modelde de çağrılması gerekir. <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> Bunu, çağıran <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> kod bir <xref:System.AddIn.Contract.INativeHandleContract>. Bu durumda, arayan sonraki alt bölümde kapsanan ana bilgisayar tarafı bağdaştırıcısı olacaktır.  
  
> [!NOTE]
> Ayrıca, ana bilgisayar <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> uygulaması Kullanıcı Arabirimi ve eklenti kullanıcı arabirimi arasında sekme etkinleştirmek için bu modelde geçersiz kılmanız gerekir. Daha fazla bilgi için [WPF Eklentilerine Genel Bakış'ta](wpf-add-ins-overview.md)"WPF Eklenti Sınırlamaları" başlıklı bakın.  
  
Eklenti-in-side bağdaştırıcı, aynı zamanda uygulamak <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>gerekir, bu geçersiz kılındığında <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> göz ardı edilir, türetilmiştir bir arabirim uygular çünkü.  
  
<a name="HostViewPipeline"></a>
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana Bilgisayar Görünümü Ardışık Bölüm'e Uygulama

Bu modelde, ana bilgisayar uygulaması genellikle ana <xref:System.Windows.FrameworkElement> bilgisayar görünümünün bir alt sınıf olmasını bekler. Ana bilgisayar tarafı bağdaştırıcısı <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırını geçtikten sonra <xref:System.AddIn.Contract.INativeHandleContract> a'ya <xref:System.Windows.FrameworkElement> dönüştürmelidir. Bir yöntem ana bilgisayar uygulaması tarafından çağrıldığı <xref:System.Windows.FrameworkElement>için, ana bilgisayar görünümünü <xref:System.Windows.FrameworkElement> içeren "döndürme" gerekir. Sonuç olarak, ana bilgisayar görünümü, diğer <xref:System.Windows.FrameworkElement> UI'leri içerebilen <xref:System.Windows.Controls.UserControl>bir alt sınıftan türemelidir. Aşağıdaki kod, `WPFAddInHostView` sınıf olarak uygulanan sözleşmenin ana bilgisayar görünümünü gösterir.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Ana Bilgisayar-Yan Bağdaştırıcı Boru Hattı Segmentinin Uygulanması

Sözleşme bir <xref:System.AddIn.Contract.INativeHandleContract>iken, ana bilgisayar <xref:System.Windows.Controls.UserControl> uygulaması (ana bilgisayar görünümünde belirtildiği gibi) bir bekliyor. Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> ev sahibi görünümün içeriği olarak ayarlanmadan önce (bu da türetilmiş) yalıtım sınırını geçtikten sonra bir'e <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.UserControl>dönüştürülmelidir.  
  
Bu çalışma, aşağıdaki kodda gösterildiği gibi, ana bilgisayar tarafı bağdaştırıcısı tarafından gerçekleştirilir.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Gördüğünüz gibi, ana bilgisayar tarafı bağdaştırıcısı eklenti-in-side bağdaştırıcıyöntemini <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> çağırarak <xref:System.AddIn.Contract.INativeHandleContract> edinir (bu, yalıtım sınırını aştığı noktadır).  
  
Ana bilgisayar tarafı bağdaştırıcısı <xref:System.Windows.FrameworkElement> daha <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>sonra <xref:System.AddIn.Contract.INativeHandleContract> a'ya çevirerek. Son olarak, ana <xref:System.Windows.FrameworkElement> bilgisayar görünümü içeriği olarak ayarlanır.  
  
<a name="AddIn"></a>
## <a name="implementing-the-add-in"></a>Eklentinin Uygulanması

Eklenti yan bağdaştırıcıve eklenti görünümü yerinde olduğu için, eklenti aşağıdaki kodda gösterildiği gibi eklenti görünümünden elde edilerek uygulanabilir.  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Bu örnekten, bu modelin ilginç bir yararı nı görebilirsiniz: eklenti geliştiricilerin eklentiyi (ui de olduğu için) hem eklenti sınıfı hem de eklenti ui yerine yalnızca uygulaması gerekir.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Ana Bilgisayar Uygulamasının Uygulanması

Ana bilgisayar tarafı bağdaştırıcısı ve ana bilgisayar görünümü oluşturulduğunda, ana bilgisayar uygulaması .NET Framework eklentisi modelini kullanarak ardışık alanı açabilir ve eklentinin ana bilgisayar görünümünü elde edebilir. Bu adımlar aşağıdaki kodda gösterilir.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Ana bilgisayar uygulaması, ana bilgisayar görünümünü dolaylı olarak ana bilgisayar uygulamasına döndüren eklentiyi etkinleştirmek için tipik .NET Framework eklentisi model kodunu kullanır. Ana bilgisayar uygulaması daha sonra ana bilgisayar <xref:System.Windows.Controls.UserControl>görünümünü <xref:System.Windows.Controls.Grid>(bir ) bir .  
  
 Eklenti Kullanıcı Arabirimi ile etkileşimleri işleme kodu eklentinin uygulama etki alanında çalışır. Bu etkileşimler şunlardır:  
  
- Olayı <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ele alma.  
  
- Gösterilen <xref:System.Windows.MessageBox>.  
  
 Bu etkinlik ana bilgisayar uygulamasından tamamen yalıtılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
