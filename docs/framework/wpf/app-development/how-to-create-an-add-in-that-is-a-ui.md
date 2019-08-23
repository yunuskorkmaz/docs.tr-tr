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
ms.openlocfilehash: fa30b7860bd8afdb68b0b54cd8d40f3e1ec86077
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949126"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Nasıl yapılır: UI Olan Eklenti Oluşturma
Bu örnek, WPF tek başına uygulaması tarafından barındırılan Windows Presentation Foundation (WPF) olan bir eklentinin nasıl oluşturulacağını gösterir.  
  
 Eklenti, WPF Kullanıcı denetimi olan bir kullanıcı arabirimi. Kullanıcı denetiminin içeriği, tıklandığında bir ileti kutusu görüntüleyen tek bir düğmedir. WPF tek başına uygulaması, ana uygulama penceresinin içeriği olarak eklenti Kullanıcı arabirimini barındırır.  
  
 **Önkoşullar**  
  
 Bu örnek, WPF uzantılarını bu senaryoyu etkinleştiren .NET Framework eklenti modeline vurgular ve şunları varsayar:  
  
- İşlem hattı, eklenti ve konak geliştirme dahil .NET Framework eklenti modeli hakkında bilgi. Bu kavramları tanımıyorsanız, bkz. eklentiler [ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Bir işlem hattının, eklentinin ve ana bilgisayar uygulamasının uygulanmasını gösteren bir öğretici için bkz [. İzlenecek yol: Genişletilebilir bir uygulama](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100))oluşturma.  
  
- .NET Framework eklentisi modeline WPF uzantıları hakkında bilgi. Bkz. [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 WPF Kullanıcı arabirimi olan bir eklenti oluşturmak için her bir işlem hattı segmenti, eklentisi ve konak uygulaması için belirli bir kod gerekir.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama

Bir eklenti bir kullanıcı arabirimi olduğunda, eklenti için Sözleşmenin uygulanması <xref:System.AddIn.Contract.INativeHandleContract>gerekir. Örnekte `IWPFAddInContract` , aşağıdaki kodda gösterildiği <xref:System.AddIn.Contract.INativeHandleContract>gibi öğesini uygular.  
  
[!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]
[!code-vb[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Contracts/IWPFAddInContract.vb#contractcode)]

<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü ardışık düzen segmentini uygulama

Eklenti <xref:System.Windows.FrameworkElement> türün bir alt sınıfı olarak uygulandığından, eklenti görünümü de alt sınıf <xref:System.Windows.FrameworkElement>olmalıdır. Aşağıdaki kod, `WPFAddInView` sınıf olarak uygulanan, sözleşmenin eklenti görünümünü gösterir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
[!code-vb[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInViews/WPFAddInView.vb#AddInViewCode)]  
  
Burada, eklenti görünümü öğesinden <xref:System.Windows.Controls.UserControl>türetilir. Sonuç olarak, eklenti Kullanıcı arabirimi ' den <xref:System.Windows.Controls.UserControl>da türetilmelidir.  
  
<a name="AddInSideAdapter"></a>
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Eklenti tarafı bağdaştırıcısı ardışık düzen segmentini uygulama

Sözleşme bir <xref:System.AddIn.Contract.INativeHandleContract>olduğunda, eklenti bir <xref:System.Windows.FrameworkElement> (eklenti görünümü ardışık düzen segmenti tarafından belirtildiği gibi) olur. Bu nedenle, <xref:System.Windows.FrameworkElement> yalıtım sınırını geçmeden <xref:System.AddIn.Contract.INativeHandleContract> önce, ' a dönüştürülmesi gerekir. Bu iş, aşağıdaki kodda gösterildiği gibi, çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>eklenti bağdaştırıcısı tarafından gerçekleştirilir.  
  
[!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
[!code-vb[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.vb#addinsideadaptercode)]

Eklentinin bir kullanıcı arabirimi döndürdüğü eklenti modelinde (bkz. [bir UI döndüren eklenti oluşturma](how-to-create-an-add-in-that-returns-a-ui.md)), eklenti bağdaştırıcısı öğesini çağırarak <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>öğesine <xref:System.AddIn.Contract.INativeHandleContract> dönüştürüyordu. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>Ayrıca bu modelde çağrılmalıdır, ancak bunu çağırmak için kodun yazılacağı bir yöntem uygulamanız gerekir. Bunu <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> , çağıran <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> kodun<xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> bir beklediğitakdirdeçağırankodugeçersizkılarak<xref:System.AddIn.Contract.INativeHandleContract>ve uygulayarak yapabilirsiniz. Bu durumda, çağıran, sonraki bir alt bölümde kapsanan konak tarafı bağdaştırıcısı olur.  
  
> [!NOTE]
> Konak uygulama kullanıcı arabirimi ve <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> eklenti Kullanıcı arabirimi arasında sekmeyi etkinleştirmek için de bu modelde geçersiz kılmanız gerekir. Daha fazla bilgi için [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)bölümünde "WPF eklentisi sınırlamaları" konusuna bakın.  
  
Eklenti tarafı bağdaştırıcısı öğesinden <xref:System.AddIn.Contract.INativeHandleContract>türetilen bir arabirim uyguladığından, geçersiz kılınırsa bu yok sayılacak <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> de uygulamanız <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>gerekir.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Konak görünümü ardışık düzen segmentini uygulama

Bu modelde, ana bilgisayar uygulaması genellikle konak görünümünün bir <xref:System.Windows.FrameworkElement> alt sınıf olmasını bekler. Konak tarafı bağdaştırıcısının, <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırını <xref:System.AddIn.Contract.INativeHandleContract> kesişdikten sonra ' <xref:System.Windows.FrameworkElement> a dönüştürmeniz gerekir. Bir yöntemi almak <xref:System.Windows.FrameworkElement>için ana bilgisayar uygulaması tarafından çağrılmadığı için, ana bilgisayar görünümü kendisini içeren "döndürmelidir <xref:System.Windows.FrameworkElement> ". Sonuç olarak <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.UserControl>, ana bilgisayar görünümü, gibi diğer usıs 'leri içerebilen öğesinin bir alt sınıfından türetilmelidir. Aşağıdaki kod, `WPFAddInHostView` sınıf olarak uygulanan sözleşmenin konak görünümünü gösterir.  

[!code-csharp[WPFAddInHostView class](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostViews/WPFAddInHostView.cs#HostViewCode)]
[!code-vb[WPFAddInHostView class](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostViews/WPFAddInHostView.vb#HostViewCode)]

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı ardışık düzen segmentini uygulama

Sözleşme bir <xref:System.AddIn.Contract.INativeHandleContract>olsa da, ana bilgisayar uygulaması bir (konak <xref:System.Windows.Controls.UserControl> görünümü tarafından belirtildiği gibi) bir bekler. Sonuç olarak, ana bilgisayar görünümünün (öğesinden <xref:System.Windows.FrameworkElement> <xref:System.Windows.Controls.UserControl>türetildiği) içerik olarak ayarlamadan önce, yalıtım sınırı geçtikten sonra bir öğesine dönüştürülmelidir. <xref:System.AddIn.Contract.INativeHandleContract>  
  
Bu çalışma, aşağıdaki kodda gösterildiği gibi konak tarafı bağdaştırıcısı tarafından gerçekleştirilir.  

[!code-csharp[Host-side adapter](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.cs#HostSideAdapterCode)]
[!code-vb[Host-side adapter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/HostSideAdapters/WPFAddIn_ContractToViewHostSideAdapter.vb#HostSideAdapterCode)]

Görebileceğiniz gibi, konak tarafı bağdaştırıcısı, <xref:System.AddIn.Contract.INativeHandleContract> eklenti tarafı <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> bağdaştırıcısının yöntemini çağırarak (Bu, yalıtım sınırını <xref:System.AddIn.Contract.INativeHandleContract> kesen bir noktasıdır) öğesini alır.  
  
Konak tarafı bağdaştırıcısı daha sonra öğesini çağırarak <xref:System.AddIn.Contract.INativeHandleContract> <xref:System.Windows.FrameworkElement> <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>öğesine dönüştürür. <xref:System.Windows.FrameworkElement> Son olarak, ana bilgisayar görünümünün içeriği olarak ayarlanır.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklentiyi uygulama

Eklenti tarafı bağdaştırıcısı ve eklenti görünümü yerinde, eklenti, aşağıdaki kodda gösterildiği gibi eklenti görünümünden türeterek uygulanabilir...  

[!code-csharp[Add-in implementation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/WPFAddIn1/AddInUI.xaml.cs#AddInCodeBehind)]
[!code-vb[Add-in implementation](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/WPFAddIn1/AddInUI.xaml.vb#AddInCodeBehind)]

Bu örnekte, bu modelin ilginç bir avantajına bakabilirsiniz: eklenti geliştiricileri, hem eklenti sınıfı hem de eklenti Kullanıcı arabirimi yerine, yalnızca eklentiyi (Kullanıcı arabirimi olduğundan) uygulamalıdır.  
  
<a name="HostApp"></a>
## <a name="implementing-the-host-application"></a>Konak uygulamasını uygulama

Konak tarafı bağdaştırıcısı ve konak görünümü oluşturulduğunda konak uygulama, .NET Framework eklenti modelini kullanarak işlem hattını açabilir ve eklentinin bir ana bilgisayar görünümünü alabilir. Bu adımlar aşağıdaki kodda gösterilmiştir.  

[!code-csharp[Acquiring a host view of the add-in](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Host/MainWindow.xaml.cs#GetUICode)]
[!code-vb[Acquiring a host view of the add-in](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleAddInIsAUISample/VisualBasic/Host/MainWindow.xaml.vb#GetUICode)]

Ana bilgisayar uygulaması, dolaylı olarak ana bilgisayar görünümünü konak uygulamasına döndüren eklentiyi etkinleştirmek için tipik .NET Framework eklenti modeli kodu kullanır. Ana bilgisayar uygulaması daha sonra bir <xref:System.Windows.Controls.UserControl> <xref:System.Windows.Controls.Grid>' den ana bilgisayar görünümünü (bir) görüntüler.  
  
 Eklenti kullanıcı arabirimi ile etkileşim işleme kodu, eklentinin uygulama etki alanında çalışır. Bu etkileşimler şunları içerir:  
  
- <xref:System.Windows.Controls.Button> Olayı işleme<xref:System.Windows.Controls.Primitives.ButtonBase.Click> .  
  
- <xref:System.Windows.MessageBox>Gösteriliyor.  
  
 Bu etkinlik, ana bilgisayar uygulamasından tamamen yalıtılmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
