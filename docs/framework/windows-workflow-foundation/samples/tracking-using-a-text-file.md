---
title: Bir metin dosyası kullanarak izleme
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: 19b4d544bc1d1c5bc9ebfa51b4ba28eb82c525d0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674604"
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="699cf-102">Bir metin dosyası kullanarak izleme</span><span class="sxs-lookup"><span data-stu-id="699cf-102">Tracking Using a Text File</span></span>
<span data-ttu-id="699cf-103">Bu örnek bir özel izleme katılımcı oluşturarak izleme Windows Workflow Foundation (WF) gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="699cf-103">This sample demonstrates how to extend tracking in Windows Workflow Foundation (WF) by creating a custom tracking participant.</span></span> <span data-ttu-id="699cf-104">İzleme katılımcıları yayılan gibi çalışma zamanını şuradan izleme kayıtları bildiren .NET Framework sınıflardır.</span><span class="sxs-lookup"><span data-stu-id="699cf-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="699cf-105">Hangi hedef senaryonuz için gerekli izleme olayları taşımak için izleme katılımcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="699cf-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="699cf-106">Örneğin, (olay izleme için Windows) ETW İzleme katılımcı bir parçası olarak sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="699cf-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="699cf-107">Bu örnekte izleme katılımcı kayıtları XML biçiminde bir metin dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="699cf-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="699cf-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="699cf-108">Sample details</span></span>  
 <span data-ttu-id="699cf-109">İzleme katılımcı'ların sağlamlığını ve yararlılığını en iyi duruma getirmek için bazı ek adımlar izleme katılımcı çalışma zamanının düzgün kablo tamamlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="699cf-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="699cf-110">Bu örnekte, en iyi yöntemleriyle uyumlu bir izleme katılımcı oluşturmak için kullanılan sınıfları aşağıdaki tabloda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="699cf-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="699cf-111">örneği</span><span class="sxs-lookup"><span data-stu-id="699cf-111">Class</span></span>|<span data-ttu-id="699cf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="699cf-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="699cf-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> metin dosyası izleme katılımcı yapılandırmak için kullanılan yapılandırma bölümü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="699cf-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="699cf-114">Bu, kullanıcıların standart .NET Framework yapılandırma dosyalarını kullanarak günlük dosyasının hedef belirtmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="699cf-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="699cf-115">WCF davranışları, kullanıcıların çalışma zamanına uzantıları eklemesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="699cf-115">Behaviors in WCF allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="699cf-116">Hizmet başlatıldığında bu davranışı için hizmet izleme katılımcı ekler.</span><span class="sxs-lookup"><span data-stu-id="699cf-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="699cf-117">Çalışma zamanında izleme katılımcıları alır ve bunları bir günlük dosyasına XML olarak depolayan izleme katılımcı.</span><span class="sxs-lookup"><span data-stu-id="699cf-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="699cf-118">Davranış uzantı öğeleri yapılandırması</span><span class="sxs-lookup"><span data-stu-id="699cf-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="699cf-119">Bir adım daha hale getirmeniz için gereken .NET Framework yapılandırma dosyalarını kullanarak daha önce açıklanan davranışı uzantı öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="699cf-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="699cf-120">Aşağıdaki yapılandırmayı uzantısı kullanılacak olduğu yapılandırma dosyalarında yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="699cf-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="699cf-121">Tam örnek kullanımı davranışı uzantı öğeleri yapılandırması için örnek Web.config dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="699cf-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="699cf-122">Özel izleme kayıtları</span><span class="sxs-lookup"><span data-stu-id="699cf-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="699cf-123">GetStockPrices.cs dosyası içinden özel izleme kayıtları oluşturma işlemini gösterir bir <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="699cf-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="699cf-124">Bu kayıt için örnek çalıştırırken arayın.</span><span class="sxs-lookup"><span data-stu-id="699cf-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="699cf-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="699cf-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="699cf-126">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="699cf-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="699cf-127">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="699cf-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="699cf-128">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="699cf-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="699cf-129">Tarayıcı penceresi açılır ve dizin için uygulama listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="699cf-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="699cf-130">Tarayıcıda StockPriceService.xamlx tıklayın.</span><span class="sxs-lookup"><span data-stu-id="699cf-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="699cf-131">Tarayıcı görüntüler **StockPriceService** sayfası, yerel hizmet wsdl adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="699cf-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="699cf-132">Bu adresini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="699cf-132">Copy this address.</span></span>  
  
     <span data-ttu-id="699cf-133">Yerel Hizmet wsdl adresi örneğidir http://localhost:53797/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="699cf-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="699cf-134">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]gidin, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (varsayılan yükleme klasörünü %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) klasörü.</span><span class="sxs-lookup"><span data-stu-id="699cf-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="699cf-135">Ardından Common7\IDE\ alt klasörü bulun.</span><span class="sxs-lookup"><span data-stu-id="699cf-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="699cf-136">WCF Test İstemcisi'ni başlatmak için WcfTestClient.exe dosyasına çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="699cf-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="699cf-137">WCF Test İstemcisi'nde seçin **Hizmet Ekle...**</span><span class="sxs-lookup"><span data-stu-id="699cf-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="699cf-138">gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="699cf-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="699cf-139">Metin kutusuna kopyaladığınız URL'yi yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="699cf-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="699cf-140">Tıklayın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="699cf-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="699cf-141">WCF Test İstemcisi'ı kullanarak hizmeti test edin.</span><span class="sxs-lookup"><span data-stu-id="699cf-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="699cf-142">WCF Test İstemcisi'nde çift **GetStockPrice()** altında **IStockPriceService** düğümü.</span><span class="sxs-lookup"><span data-stu-id="699cf-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="699cf-143">**GetStockPrice()** sağ bölmede, bir parametre içeren yöntemi görünür.</span><span class="sxs-lookup"><span data-stu-id="699cf-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="699cf-144">Contoso ağında parametresinin değeri olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="699cf-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="699cf-145">Tıklayın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="699cf-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="699cf-146">İzlenen olayları % APPDATA%\trackingRecords.log uygulama veri dizininde bulunan günlük dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="699cf-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="699cf-147">% APPDATA % %SystemDrive%\Users için gideren bir ortam değişkenidir\\< kullanıcı adı\>içinde \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], veya Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="699cf-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="699cf-148">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="699cf-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="699cf-149">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="699cf-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="699cf-150">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="699cf-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="699cf-151">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="699cf-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="699cf-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="699cf-152">See Also</span></span>  
 [<span data-ttu-id="699cf-153">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="699cf-153">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
