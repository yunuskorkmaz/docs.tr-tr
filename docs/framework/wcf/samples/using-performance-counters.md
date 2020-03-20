---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143583"
---
# <a name="using-performance-counters"></a><span data-ttu-id="9be85-102">Performans Sayaçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="9be85-102">Using Performance Counters</span></span>
<span data-ttu-id="9be85-103">Bu örnek, Windows Communication Foundation (WCF) performans sayaçlarına nasıl erişilmeyi ve kullanıcı tanımlı performans sayaçlarının nasıl oluşturulacaklarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9be85-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="9be85-104">Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9be85-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9be85-105">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="9be85-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9be85-106">Bu örnekte, istemci hizmetin dört `ICalculator` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="9be85-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="9be85-107">İstemci, kullanıcı tarafından kesintiye uğrayana kadar bunu yapmaya devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="9be85-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="9be85-108">Hizmet değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="9be85-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="9be85-109">Performans sayaçları, aşağıdaki örnek yapılandırmada gösterildiği gibi, hizmet için Web.config dosyasının tanılama bölümünde etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9be85-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9be85-110">Bu görev configuration editor [aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9be85-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="9be85-111">Performans sayaçları etkinleştirildiğinde, hizmet için WCF performans sayaçlarının tamamı etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9be85-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="9be85-112">.NET Framework, performans verilerini otomatik olarak `ServiceModelService`üç `ServiceModelEndpoint` `ServiceModelOperation`düzeyde tutar: ve .</span><span class="sxs-lookup"><span data-stu-id="9be85-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="9be85-113">Bu düzeylerin her birinde "Aramalar", "Saniyebaşına Aramalar" ve "Yetkili Olmayan Güvenlik Çağrıları" gibi performans sayaçları bulunur.</span><span class="sxs-lookup"><span data-stu-id="9be85-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9be85-114">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9be85-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9be85-115">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="9be85-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9be85-116">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9be85-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9be85-117">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9be85-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="9be85-118">Performans verilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="9be85-118">To view performance data</span></span>  
  
1. <span data-ttu-id="9be85-119">Performans İzleme Aracını **Başlat,** **Çalıştır...** seçeneğini `perfmon` tıklatarak başlatın, **Tamam'a** girin ve tıklayın veya Denetim Masası'ndan **Yönetim Araçları'nı** seçin ve **Performans'ı**çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9be85-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9be85-120">Örnek kod çalışmayana kadar sayaç ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9be85-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="9be85-121">Bunları seçerek ve Sil tuşuna basarak listelenen performans sayaçlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="9be85-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="9be85-122">Grafik bölmesine sağ tıklayarak ve Sayaç Ekle'yi seçerek WCF **sayaçları**ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9be85-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="9be85-123">Sayaç **Ekle** iletişim kutusunda, **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0.0'ı** Seç nesnesi açılan liste kutusunda seçin.</span><span class="sxs-lookup"><span data-stu-id="9be85-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="9be85-124">Listeden görüntülemek istediğiniz sayaçları seçin.</span><span class="sxs-lookup"><span data-stu-id="9be85-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9be85-125">Bilgisayarda çalışan WCF hizmetleri yoksa, bir hizmet için WCF performans sayacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="9be85-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="9be85-126">Sayaçları etkinleştirmek için Configuration Editor'u kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9be85-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="9be85-127">SvcConfigEditor.exe bir örnek açın.</span><span class="sxs-lookup"><span data-stu-id="9be85-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="9be85-128">Dosya menüsünde **Aç'ı** tıklatın ve **ardından Config dosyasını tıklatın...**.</span><span class="sxs-lookup"><span data-stu-id="9be85-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="9be85-129">Örnek uygulamanın hizmet klasörüne gidin ve Web.config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9be85-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="9be85-130">Yapılandırma ağacında **Tanılama'yı** tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9be85-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="9be85-131">'Tümü'nu göstermek için **Tanılama** penceresinde **Performans Sayacını** titretin.</span><span class="sxs-lookup"><span data-stu-id="9be85-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="9be85-132">Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.</span><span class="sxs-lookup"><span data-stu-id="9be85-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9be85-133">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="9be85-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9be85-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9be85-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9be85-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="9be85-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9be85-136">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="9be85-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="9be85-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9be85-137">See also</span></span>

- <span data-ttu-id="9be85-138">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9be85-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
