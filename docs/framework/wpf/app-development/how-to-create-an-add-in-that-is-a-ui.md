---
title: 'Nasıl yapılır: UI Olan Eklenti Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- creating an add-in that is a UI [WPF]
- add-ins [WPF], UI
- creating UI add-ins [WPF]
- UI add-ins [WPF], creating
- implementing UI add-ins [WPF]
- pipeline segments [WPF], creating add-ins
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
ms.openlocfilehash: 9b7fa33d9af8d364491d1c72813cb62f34378557
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947894"
---
# <a name="how-to-create-an-add-in-that-is-a-ui"></a>Nasıl yapılır: UI Olan Eklenti Oluşturma
Bu örnek, bir Windows Presentation Foundation (WPF tek başına uygulama tarafından barındırılan WPF) olan bir eklenti oluşturma işlemi gösterilmektedir.  
  
 Eklentinin bir WPF kullanıcı denetimi bir UI'dir. Tek bir düğme, tıklandığında, kullanıcı denetiminin içeriği olan bir ileti kutusu görüntüler. WPF tek başına uygulama eklenti kullanıcı Arabirimi ana uygulama penceresini içeriğini barındırır.  
  
 **Önkoşullar**  
  
 Bu örnekte, bu senaryoyu WPF uzantıları için .NET Framework eklenti modeli vurgular ve aşağıdaki varsayar:  
  
- Bilgi işlem hattı, eklenti ve konak geliştirme gibi .NET Framework eklenti modeli, sahibi. Bu kavramları alışkın değilseniz bkz [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)). Bir işlem hattı, bir eklenti ve ana bilgisayar uygulamasına uygulanışı gösteren bir öğretici için bkz [izlenecek yol: Genişletilebilir uygulama oluşturma](/previous-versions/dotnet/netframework-4.0/bb788290(v%3dvs.100)).  
  
- .NET Framework eklenti modeli WPF uzantılarını bilgi. Bkz: [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md).  
  
## <a name="example"></a>Örnek  
 Bir WPF UI olan eklenti oluşturmak için her işlem hattı segment, eklenti ve ana bilgisayar uygulaması için özel kod gerektirir.  

<a name="Contract"></a>   
## <a name="implementing-the-contract-pipeline-segment"></a>Sözleşme ardışık düzen segmentini uygulama  
 Sözleşme eklenti için bir eklentiyi bir UI olduğunda uygulamalıdır <xref:System.AddIn.Contract.INativeHandleContract>. Örnekte, `IWPFAddInContract` uygulayan <xref:System.AddIn.Contract.INativeHandleContract>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInIsAUISample#ContractCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/Contracts/IWPFAddInContract.cs#contractcode)]  
  
<a name="AddInViewPipeline"></a>   
## <a name="implementing-the-add-in-view-pipeline-segment"></a>Eklenti görünümü işlem hattı segmentini uygulama  
 Eklenti öğesinin uygulandığından <xref:System.Windows.FrameworkElement> türü, eklenti görünümü gerekir ayrıca alt <xref:System.Windows.FrameworkElement>. Aşağıdaki kod olarak uygulanan sözleşme, eklenti görünümü gösterir `WPFAddInView` sınıfı.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInViewCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInViews/WPFAddInView.cs#addinviewcode)]  
  
 Eklenti görünümü burada türetilir <xref:System.Windows.Controls.UserControl>. Sonuç olarak, eklentinin kullanıcı Arabirimi de türetilmesi <xref:System.Windows.Controls.UserControl>.  
  
<a name="AddInSideAdapter"></a>   
## <a name="implementing-the-add-in-side-adapter-pipeline-segment"></a>Ekleme tarafı bağdaştırıcısı işlem hattı segmentini uygulama  
 Sözleşme olsa da bir <xref:System.AddIn.Contract.INativeHandleContract>, eklentinin bir <xref:System.Windows.FrameworkElement> (eklenti görünümü işlem hattı segment tarafından belirtildiği gibi). Bu nedenle, <xref:System.Windows.FrameworkElement> dönüştürülmelidir bir <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı geçmeden önce. Bu iş tarafından Ekle tarafı bağdaştırıcısı çağrılarak gerçekleştirilir <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>aşağıdaki kodda gösterildiği gibi.  
  
 [!code-csharp[SimpleAddInIsAUISample#AddInSideAdapterCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleAddInIsAUISample/CSharp/AddInSideAdapters/WPFAddIn_ViewToContractAddInSideAdapter.cs#addinsideadaptercode)]  
  
 İçinde bir eklenti döndüğü UI olan eklenti modeli (bkz [bir eklenti döndürür bir kullanıcı Arabirimi oluşturma](how-to-create-an-add-in-that-returns-a-ui.md)), eklenti bağdaştırıcısı dönüştürülen <xref:System.Windows.FrameworkElement> için bir <xref:System.AddIn.Contract.INativeHandleContract> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A>. <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> Ayrıca bir yöntemi çağırmak için kod yazmak için uygulamanız gereken ancak bu modelde, çağrılmalıdır. Geçersiz kılarak bunu <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> ve çağıran kodu uygulama <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter%2A> , çağıran kod <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> bekliyor bir <xref:System.AddIn.Contract.INativeHandleContract>. Bu durumda arayan bir sonraki alt bölümünde ele alınmıştır konak tarafı bağdaştırıcı olacaktır.  
  
> [!NOTE]
>  Geçersiz kılmanız gerekir <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> konak uygulama kullanıcı Arabirimi arasında sekmeyle gitmeyi etkinleştirme ve kullanıcı Arabirimi eklentisi için bu modeli. Daha fazla bilgi için "WPF eklentisi sınırlamaları" konusuna bakın. [WPF eklentileri genel bakış](wpf-add-ins-overview.md).  
  
 Türetilen bir arabirim Ekle tarafı bağdaştırıcısı uyguladığından <xref:System.AddIn.Contract.INativeHandleContract>, uygulamanız gereken <xref:System.AddIn.Contract.INativeHandleContract.GetHandle%2A>, ancak bu yoksayılır olduğunda <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> geçersiz kılındı.  
  
<a name="HostViewPipeline"></a>   
## <a name="implementing-the-host-view-pipeline-segment"></a>Ana görünüm ardışık düzen segmentini uygulama  
 Bu modelde, ana bilgisayar uygulaması genellikle ana görünümünde olmasını bekliyor. bir <xref:System.Windows.FrameworkElement> öğesinin alt sınıfı. Konak tarafı bağdaştırıcısı dönüştürmelisiniz <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> sonra <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı aştığında. Bir yöntem almak için konak uygulama tarafından çağrılmadığından <xref:System.Windows.FrameworkElement>, "ana görünümünde döndürmelidir" <xref:System.Windows.FrameworkElement> içererek. Sonuç olarak, ana görünümünde öğesinin türetilmelidir <xref:System.Windows.FrameworkElement> , diğer içerebilir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], gibi <xref:System.Windows.Controls.UserControl>. Aşağıdaki kod olarak uygulanan sözleşme ana görünümünde gösterir `WPFAddInHostView` sınıfı.  

<a name="HostSideAdapter"></a>   
## <a name="implementing-the-host-side-adapter-pipeline-segment"></a>Konak tarafı bağdaştırıcısı işlem hattı segmentini uygulama  
 Sözleşme olsa da bir <xref:System.AddIn.Contract.INativeHandleContract>, ana bilgisayar uygulaması bekliyor bir <xref:System.Windows.Controls.UserControl> (ana görünümünde tarafından belirtildiği gibi). Sonuç olarak, <xref:System.AddIn.Contract.INativeHandleContract> dönüştürülmelidir bir <xref:System.Windows.FrameworkElement> ana görünümünde içeriği olarak ayarlamadan önce yalıtım sınırı geçmesinden sonra (öğesinden türetildiğini <xref:System.Windows.Controls.UserControl>).  
  
 Bu iş, aşağıdaki kodda gösterildiği gibi konak tarafı bağdaştırıcı tarafından gerçekleştirilir.  

 Gördüğünüz gibi konak tarafı bağdaştırıcısını alır <xref:System.AddIn.Contract.INativeHandleContract> Ekle tarafı bağdaştırıcının çağırarak <xref:System.AddIn.Pipeline.ContractBase.QueryContract%2A> yöntemi (Bu noktadır burada <xref:System.AddIn.Contract.INativeHandleContract> yalıtım sınırı aştığında).  
  
 Ardından konak tarafı bağdaştırıcısı dönüştürür <xref:System.AddIn.Contract.INativeHandleContract> için bir <xref:System.Windows.FrameworkElement> çağırarak <xref:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter%2A>. Son olarak, <xref:System.Windows.FrameworkElement> ana görünümünde içeriği olarak ayarlanır.  
  
<a name="AddIn"></a>   
## <a name="implementing-the-add-in"></a>Eklenti uygulama  
 Ekle tarafı bağdaştırıcısı ve eklenti görünümü yerinde eklenti eklenti görünümünden türetilerek aşağıdaki kodda gösterildiği gibi uygulanabilir.  

 Bu örnekte, bir ilgi çekici Bu modelin avantajı görebileceğiniz: eklenti, geliştiricilerin yalnızca gerekir (kullanıcı Arabirimi de olduğundan) eklentisi, yerine hem bir eklenti sınıfı ve eklentinin kullanıcı Arabirimi uygulamak.  
  
<a name="HostApp"></a>   
## <a name="implementing-the-host-application"></a>Konak uygulamanın uygulama  
 Konak tarafı bağdaştırıcısı ile oluşturulan ana görünümünde, ana bilgisayar uygulaması kullanabileceğiniz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işlem hattı açıp eklentiyi bir ana bilgisayar görünümü elde eklenti modeli. Aşağıdaki kodda adımları gösterilmektedir.  

 Konak uygulamanın tipik .NET Framework eklenti modeli kodu örtük olarak ana bilgisayar uygulamasına ana görünümünde döndüren, eklentiyi etkinleştirmek için kullanır. Konak uygulama sonradan ana görünümünde görüntüler (olduğu bir <xref:System.Windows.Controls.UserControl>) gelen bir <xref:System.Windows.Controls.Grid>.  
  
 Eklentinin kullanıcı Arabirimi ile etkileşim işlemek için kod eklentinin uygulama etki alanında çalışır. Bu etkileşimlerin şunları içerir:  
  
- İşleme <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay.  
  
- Gösteren <xref:System.Windows.MessageBox>.  
  
 Bu etkinlik ana bilgisayar uygulamasını tamamen yalıtılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eklentiler ve Genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))
- [WPF Eklentilerine Genel Bakış](wpf-add-ins-overview.md)
