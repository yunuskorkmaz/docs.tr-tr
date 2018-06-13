---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807325"
---
# <a name="using-performance-counters"></a><span data-ttu-id="55bd7-102">Performans Sayaçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="55bd7-102">Using Performance Counters</span></span>
<span data-ttu-id="55bd7-103">Bu örnek, Windows Communication Foundation (WCF) performans sayaçları erişmek nasıl ve kullanıcı tanımlı performans sayaçları oluşturma gösterilir.</span><span class="sxs-lookup"><span data-stu-id="55bd7-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="55bd7-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="55bd7-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55bd7-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="55bd7-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="55bd7-106">Bu örnekte, istemci dört yöntemlerini çağıran `ICalculator` hizmet.</span><span class="sxs-lookup"><span data-stu-id="55bd7-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="55bd7-107">İstemci kullanıcı tarafından kesilene kadar bunun devam eder.</span><span class="sxs-lookup"><span data-stu-id="55bd7-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="55bd7-108">Hizmet değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="55bd7-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="55bd7-109">Performans sayaçları hizmet için Web.config dosyasının tanılama bölümünde şu örnek yapılandırmada gösterildiği gibi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55bd7-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="55bd7-110">Bu görev ayrıca yapılabilir kullanarak [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="55bd7-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="55bd7-111">Performans sayaçları etkin olduğunda, tüm paketi WCF performans sayaçları için hizmet etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="55bd7-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="55bd7-112">.NET Framework, üç düzeyde performans verilerini otomatik olarak bulundurur: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="55bd7-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="55bd7-113">Bu düzeylerin her birinde, performans sayaçları "Çağrıları", "Çağrıları saniyede" ve "Güvenlik çağrıları yetkilendirilmedi" gibi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="55bd7-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55bd7-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="55bd7-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="55bd7-115">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55bd7-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="55bd7-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55bd7-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="55bd7-117">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="55bd7-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="55bd7-118">Performans verilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="55bd7-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="55bd7-119">Performans İzleyicisi aracıyla tıklayarak Başlat **Başlat**, **Çalıştır...** , girin `perfmon` tıklatıp **Tamam** veya Denetim Masası'ndan seçin **Yönetimsel Araçlar** çift tıklayın ve **performans**.</span><span class="sxs-lookup"><span data-stu-id="55bd7-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55bd7-120">Örnek kod çalışıncaya kadar sayaçları ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="55bd7-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="55bd7-121">Bunları seçerek ve Delete tuşuna basarak listelenen performans sayaçlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="55bd7-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="55bd7-122">WCF sayaçları Grafik bölmesi sağ tıklayıp seçerek eklemek **Sayaç Ekle**.</span><span class="sxs-lookup"><span data-stu-id="55bd7-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="55bd7-123">İçinde **Sayaç Ekle** iletişim kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0** performans nesnesi açılır liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="55bd7-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="55bd7-124">Listeden görüntülemek istediğiniz sayaçları seçin.</span><span class="sxs-lookup"><span data-stu-id="55bd7-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="55bd7-125">Bilgisayarda çalışan hiçbir WCF hizmetleri varsa bir hizmet için hiçbir WCF performans sayaçları vardır.</span><span class="sxs-lookup"><span data-stu-id="55bd7-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="55bd7-126">Sayaçları etkinleştirmek için yapılandırma Düzenleyicisi'ni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="55bd7-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="55bd7-127">SvcConfigEditor.exe örneği açın.</span><span class="sxs-lookup"><span data-stu-id="55bd7-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="55bd7-128">Dosya menüsünde **açık** ve ardından **yapılandırma dosyası...** .</span><span class="sxs-lookup"><span data-stu-id="55bd7-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="55bd7-129">Örnek uygulama hizmeti klasörüne gidin ve Web.config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="55bd7-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="55bd7-130">Tıklatın **tanılama** yapılandırma ağaç.</span><span class="sxs-lookup"><span data-stu-id="55bd7-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="55bd7-131">İki durumlu **performans sayacı** içinde **tanılama** 'All' göstermek için penceresi.</span><span class="sxs-lookup"><span data-stu-id="55bd7-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="55bd7-132">Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.</span><span class="sxs-lookup"><span data-stu-id="55bd7-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55bd7-133">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="55bd7-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="55bd7-134">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="55bd7-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55bd7-135">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="55bd7-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55bd7-136">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="55bd7-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="55bd7-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55bd7-137">See Also</span></span>  
 [<span data-ttu-id="55bd7-138">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="55bd7-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
