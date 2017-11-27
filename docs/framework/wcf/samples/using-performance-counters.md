---
title: "Performans Sayaçlarını Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84cbbf83c240ae11099e2c9646150c810a437e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-performance-counters"></a><span data-ttu-id="0c1a5-102">Performans Sayaçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="0c1a5-102">Using Performance Counters</span></span>
<span data-ttu-id="0c1a5-103">Bu örnek nasıl erişileceği gösterilmektedir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performans sayaçları ve kullanıcı tanımlı performans sayaçları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-103">This sample demonstrates how to access [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="0c1a5-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0c1a5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c1a5-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0c1a5-106">Bu örnekte, istemci dört yöntemlerini çağıran `ICalculator` hizmet.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="0c1a5-107">İstemci kullanıcı tarafından kesilene kadar bunun devam eder.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="0c1a5-108">Hizmet değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="0c1a5-109">Performans sayaçları hizmet için Web.config dosyasının tanılama bölümünde şu örnek yapılandırmada gösterildiği gibi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0c1a5-110">Bu görev ayrıca yapılabilir kullanarak [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0c1a5-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="0c1a5-111">Performans sayaçları etkin olduğunda, tüm paketi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performans sayaçları, hizmet için etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-111">When performance counters are enabled, the entire suite of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters is enabled for the service.</span></span> <span data-ttu-id="0c1a5-112">.NET Framework, üç düzeyde performans verilerini otomatik olarak bulundurur: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="0c1a5-113">Bu düzeylerin her birinde, performans sayaçları "Çağrıları", "Çağrıları saniyede" ve "Güvenlik çağrıları yetkilendirilmedi" gibi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0c1a5-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="0c1a5-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0c1a5-115">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1a5-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0c1a5-116">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1a5-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0c1a5-117">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0c1a5-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="0c1a5-118">Performans verilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="0c1a5-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="0c1a5-119">Performans İzleyicisi aracıyla tıklayarak Başlat **Başlat**, **Çalıştır...** , girin `perfmon` tıklatıp **Tamam** veya Denetim Masası'ndan seçin **Yönetimsel Araçlar** çift tıklayın ve **performans**.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c1a5-120">Örnek kod çalışıncaya kadar sayaçları ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="0c1a5-121">Bunları seçerek ve Delete tuşuna basarak listelenen performans sayaçlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="0c1a5-122">Ekle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Grafik bölmesi sağ tıklatıp seçerek sayaçları **Sayaç Ekle**.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-122">Add [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="0c1a5-123">İçinde **Sayaç Ekle** iletişim kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0** performans nesnesi açılır liste kutusu.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="0c1a5-124">Listeden görüntülemek istediğiniz sayaçları seçin.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c1a5-125">Vardır hiçbir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsa bir hizmet için performans sayaçları yok [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bilgisayarda çalışan hizmetler.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-125">There are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters for a service if there are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="0c1a5-126">Sayaçları etkinleştirmek için yapılandırma Düzenleyicisi'ni kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0c1a5-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="0c1a5-127">SvcConfigEditor.exe örneği açın.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="0c1a5-128">Dosya menüsünde **açık** ve ardından **yapılandırma dosyası...** .</span><span class="sxs-lookup"><span data-stu-id="0c1a5-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="0c1a5-129">Örnek uygulama hizmeti klasörüne gidin ve Web.config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="0c1a5-130">Tıklatın **tanılama** yapılandırma ağaç.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="0c1a5-131">İki durumlu **performans sayacı** içinde **tanılama** 'All' göstermek için penceresi.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="0c1a5-132">Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0c1a5-133">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0c1a5-134">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0c1a5-135">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c1a5-136">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="0c1a5-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0c1a5-137">See Also</span></span>  
 [<span data-ttu-id="0c1a5-138">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="0c1a5-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
