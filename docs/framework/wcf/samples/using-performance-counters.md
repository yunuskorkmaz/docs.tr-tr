---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 787a3d08b463980721fb207d029057e14618db5e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131891"
---
# <a name="using-performance-counters"></a><span data-ttu-id="de161-102">Performans Sayaçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="de161-102">Using Performance Counters</span></span>
<span data-ttu-id="de161-103">Bu örnek, kullanıcı tanımlı performans Sayaçlarınızı oluşturma işlemleri ve Windows Communication Foundation (WCF) performans sayaçlarını nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="de161-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="de161-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="de161-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de161-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="de161-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="de161-106">Bu örnekte, dört yöntemlerinin istemci çağrıları `ICalculator` hizmeti.</span><span class="sxs-lookup"><span data-stu-id="de161-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="de161-107">İstemci, kullanıcı tarafından kesintiye kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="de161-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="de161-108">Hizmet değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="de161-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="de161-109">Performans sayaçları hizmeti için Web.config dosyasının tanılama bölümünde şu örnek yapılandırmada gösterildiği etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de161-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="de161-110">Bu görevi de yapılabilir kullanarak [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="de161-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="de161-111">Performans sayaçlarını etkin olduğunda, tüm WCF performans sayaçları dizisi için hizmet etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="de161-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="de161-112">.NET Framework, üç düzeyde performans verilerini otomatik olarak bulundurur: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="de161-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="de161-113">Bu düzeylerinin her biri "Çağrıları", "Çağrıları saniye başına" ve "Güvenlik çağrıları yetkilendirilmedi" gibi performans sayaçları sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de161-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="de161-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="de161-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="de161-115">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de161-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="de161-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de161-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="de161-117">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="de161-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="de161-118">Performans verilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="de161-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="de161-119">Tıklayarak Performans İzleyicisi Aracı'nı başlatın **Başlat**, **Çalıştır...** , girin `perfmon` tıklatıp **Tamam** veya Denetim Masası'ndan seçin **Yönetimsel Araçlar** ve çift **performans**.</span><span class="sxs-lookup"><span data-stu-id="de161-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de161-120">Örnek kodunu çalıştıran dek sayaçları ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="de161-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="de161-121">Bunları seçerek ve Delete tuşuna basarak listelenen performans sayaçlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="de161-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="de161-122">Grafik bölmesi sağ tıklatıp seçerek WCF sayaçları ekleyin **Sayaç Ekle**.</span><span class="sxs-lookup"><span data-stu-id="de161-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="de161-123">İçinde **Sayaç Ekle** iletişim kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0** performans nesnesinde açılan liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="de161-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="de161-124">Listeden görüntülemek istediğiniz sayaçları seçin.</span><span class="sxs-lookup"><span data-stu-id="de161-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de161-125">Bilgisayarda çalışan bir WCF Hizmeti yok ise hiçbir WCF performans sayaçları için bir hizmet vardır.</span><span class="sxs-lookup"><span data-stu-id="de161-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="de161-126">Sayaçları etkinleştirmek için yapılandırma Düzenleyicisi'ni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="de161-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="de161-127">SvcConfigEditor.exe örneği açın.</span><span class="sxs-lookup"><span data-stu-id="de161-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="de161-128">Dosya menüsünde **açık** ve ardından **yapılandırma dosyası...** .</span><span class="sxs-lookup"><span data-stu-id="de161-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="de161-129">Örnek uygulama hizmeti klasörüne gidin ve Web.config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="de161-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="de161-130">Tıklayın **tanılama** yapılandırma ağaç.</span><span class="sxs-lookup"><span data-stu-id="de161-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="de161-131">İki durumlu **performans sayacı** içinde **tanılama** 'All' gösterilecek penceresi.</span><span class="sxs-lookup"><span data-stu-id="de161-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="de161-132">Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.</span><span class="sxs-lookup"><span data-stu-id="de161-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="de161-133">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="de161-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="de161-134">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="de161-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de161-135">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="de161-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de161-136">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="de161-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="de161-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de161-137">See Also</span></span>  
 [<span data-ttu-id="de161-138">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="de161-138">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
