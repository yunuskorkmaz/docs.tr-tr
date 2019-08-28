---
title: Performans Sayaçlarını Kullanma
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 724580c1725cf6513e1d85f03b0abfdefb4d040a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044539"
---
# <a name="using-performance-counters"></a><span data-ttu-id="8a953-102">Performans Sayaçlarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="8a953-102">Using Performance Counters</span></span>
<span data-ttu-id="8a953-103">Bu örnek, Windows Communication Foundation (WCF) performans sayaçlarına nasıl erişileceğini ve Kullanıcı tanımlı performans sayaçlarının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a953-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="8a953-104">Bu örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="8a953-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a953-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a953-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8a953-106">Bu örnekte istemci, `ICalculator` hizmetin dört yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8a953-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="8a953-107">İstemci, Kullanıcı tarafından kesintiye gelinceye kadar bunu yapmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="8a953-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="8a953-108">Hizmet değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="8a953-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="8a953-109">Aşağıdaki örnek yapılandırmada gösterildiği gibi, hizmetinin Web. config dosyasının Tanılama bölümünde performans sayaçları etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a953-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="8a953-110">Bu görev, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak da yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a953-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="8a953-111">Performans sayaçları etkinleştirildiğinde, hizmet için tüm WCF performans sayacı paketi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8a953-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="8a953-112">.NET Framework, performans verilerini otomatik olarak üç düzeyde tutar: `ServiceModelService`, `ServiceModelEndpoint` ve `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="8a953-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="8a953-113">Bu düzeylerin her biri, "çağrı", "saniyedeki çağrı" ve "güvenlik çağrıları yetkilendirilmemiş" gibi performans sayaçlarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8a953-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a953-114">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8a953-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8a953-115">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a953-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8a953-116">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a953-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8a953-117">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a953-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="8a953-118">Performans verilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="8a953-118">To view performance data</span></span>  
  
1. <span data-ttu-id="8a953-119">Sırasıyla **Başlat**, **Çalıştır..** `perfmon` . ' a tıklayarak Performans İzleyicisi aracını başlatın, Tamam ' a tıklayın, **Tamam** ' a tıklayın veya denetim masasından, **Yönetim Araçları** ' nı seçin ve **performans**' ı çift</span><span class="sxs-lookup"><span data-stu-id="8a953-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8a953-120">Örnek kod çalışmadığı sürece sayaç ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a953-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="8a953-121">Seçerek listelenen performans sayaçlarını kaldırın ve Sil tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8a953-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="8a953-122">Grafik bölmesine sağ tıklayıp **Sayaç Ekle**' yı seçerek WCF sayaçlarını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8a953-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="8a953-123">**Sayaç Ekle** iletişim kutusunda, performans nesnesi açılan listesi kutusunda **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 veya ServiceModelService 3.0.0.0 öğesini** seçin.</span><span class="sxs-lookup"><span data-stu-id="8a953-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="8a953-124">Listeden görüntülemek istediğiniz sayaçları seçin.</span><span class="sxs-lookup"><span data-stu-id="8a953-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8a953-125">Bilgisayarda çalışan bir WCF hizmeti yoksa, bir hizmet için WCF performans sayacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="8a953-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="8a953-126">Sayaçları etkinleştirmek üzere yapılandırma düzenleyicisini kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8a953-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="8a953-127">SvcConfigEditor. exe ' nin bir örneğini açın.</span><span class="sxs-lookup"><span data-stu-id="8a953-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="8a953-128">Dosya menüsünde **Aç** ' a ve ardından **yapılandırma dosyası...** öğesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8a953-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="8a953-129">Örnek uygulamanın hizmet klasörüne gidin ve Web. config dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="8a953-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="8a953-130">Yapılandırma ağacında **Tanılamalar** ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8a953-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="8a953-131">**Tanılama** penceresindeki **performans sayacını** ' tümünü ' gösterecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8a953-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="8a953-132">Yapılandırma dosyasını kaydedin ve düzenleyiciden çıkın.</span><span class="sxs-lookup"><span data-stu-id="8a953-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a953-133">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a953-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a953-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a953-134">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8a953-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="8a953-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a953-136">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8a953-136">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="8a953-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a953-137">See also</span></span>

- [<span data-ttu-id="8a953-138">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="8a953-138">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
