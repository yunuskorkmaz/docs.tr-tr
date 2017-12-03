---
title: "Bir metin dosyası kullanarak izleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abb29dc584bbede14adcb396df8cd37a894b6f2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tracking-using-a-text-file"></a><span data-ttu-id="57549-102">Bir metin dosyası kullanarak izleme</span><span class="sxs-lookup"><span data-stu-id="57549-102">Tracking Using a Text File</span></span>
<span data-ttu-id="57549-103">Bu örnek izlemede genişletmek gösterilmiştir [!INCLUDE[wf](../../../../includes/wf-md.md)] özel izleme katılımcı oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="57549-103">This sample demonstrates how to extend tracking in [!INCLUDE[wf](../../../../includes/wf-md.md)] by creating a custom tracking participant.</span></span> <span data-ttu-id="57549-104">İzleme katılımcıları yayılan gibi çalışma zamanını şuradan izleme kayıtları aldığınız .NET Framework sınıflarıdır.</span><span class="sxs-lookup"><span data-stu-id="57549-104">Tracking participants are .NET Framework classes that receive tracking records from the runtime as they are emitted.</span></span> <span data-ttu-id="57549-105">Hangi hedef senaryonuz için gerekli izleme olayları taşıma için bir izleme katılımcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57549-105">You can create a tracking participant to transport the tracking events to whichever destination is required for your scenario.</span></span> <span data-ttu-id="57549-106">Örneğin, (Windows için olay izleme) ETW İzleme katılımcı parçası olarak sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="57549-106">For example, ETW (Event Tracing for Windows) Tracking Participant is provided as part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="57549-107">Bu örnekte izleme katılımcı kayıtları XML biçiminde bir metin dosyasına yazar.</span><span class="sxs-lookup"><span data-stu-id="57549-107">The tracking participant in this sample writes the records in XML format to a text file.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="57549-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="57549-108">Sample details</span></span>  
 <span data-ttu-id="57549-109">İzleme katılımcının sağlamlık ve yararlılığını iyileştirmek için bazı ek adımlar düzgün çalışma zamanına izleme katılımcı kablo tamamlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="57549-109">To optimize the usefulness and robustness of your tracking participant, some additional steps must be completed to properly wire the tracking participant to the runtime.</span></span> <span data-ttu-id="57549-110">Aşağıdaki tabloda, en iyi yöntemlerle uyumlu bir izleme katılımcı oluşturmak için bu örnekte kullanılan sınıflar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57549-110">The following table describes the classes used in this sample to create a tracking participant that complies with best practices.</span></span>  
  
|<span data-ttu-id="57549-111">örneği</span><span class="sxs-lookup"><span data-stu-id="57549-111">Class</span></span>|<span data-ttu-id="57549-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57549-112">Description</span></span>|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<span data-ttu-id="57549-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> metin dosyası izleme katılımcı yapılandırmak için kullanılan yapılandırma bölümü tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57549-113">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> is used to define the configuration section used to configure the text file tracking participant.</span></span> <span data-ttu-id="57549-114">Bu, kullanıcıların standart .NET Framework yapılandırma dosyalarını kullanarak günlük dosyası hedef belirtmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="57549-114">This allows users to specify the destination of the log file using standard .NET Framework configuration files.</span></span>|  
|`TextFileTrackingBehavior`|<span data-ttu-id="57549-115">Davranışlarının [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanıcıların çalışma zamanına uzantıları eklemesine izin verin.</span><span class="sxs-lookup"><span data-stu-id="57549-115">Behaviors in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allow users to inject extensions into the runtime.</span></span> <span data-ttu-id="57549-116">Hizmet başlatıldığında bu davranış izleme katılımcı hizmete ekler.</span><span class="sxs-lookup"><span data-stu-id="57549-116">This behavior adds the tracking participant to the service when the service starts.</span></span>|  
|`TextFileTrackingParticipant`|<span data-ttu-id="57549-117">Çalışma zamanında izleme katılımcıları alır ve bunları bir günlük dosyasına XML olarak depolayan izleme katılımcı.</span><span class="sxs-lookup"><span data-stu-id="57549-117">The tracking participant that receives tracking participants at runtime and stores them to a log file as XML.</span></span>|  
  
## <a name="behavior-extension-elements-configuration"></a><span data-ttu-id="57549-118">Davranış uzantı öğeleri yapılandırması</span><span class="sxs-lookup"><span data-stu-id="57549-118">Behavior Extension Elements Configuration</span></span>  
 <span data-ttu-id="57549-119">Bir adım daha yapmak için gerekli .NET Framework yapılandırma dosyalarını kullanarak daha önce açıklanan davranış uzantı öğesinin kullanın.</span><span class="sxs-lookup"><span data-stu-id="57549-119">One more step is required to make use of the behavior extension element previously described using .NET Framework configuration files.</span></span> <span data-ttu-id="57549-120">Aşağıdaki yapılandırma uzantısı kullanılacak olduğu yapılandırma dosyalarında yerleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="57549-120">The following configuration must be placed in configuration files where the extension is to be used.</span></span>  
  
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
>  <span data-ttu-id="57549-121">Tam örnek kullanımı davranışı uzantı öğeleri yapılandırması için örnek Web.config dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="57549-121">See the Web.config file in the sample for a complete example usage of behavior extension elements configuration.</span></span>  
  
## <a name="custom-tracking-records"></a><span data-ttu-id="57549-122">Özel izleme kayıtları</span><span class="sxs-lookup"><span data-stu-id="57549-122">Custom Tracking Records</span></span>  
 <span data-ttu-id="57549-123">GetStockPrices.cs dosya nasıl özel izleme kayıtları içinden oluşturulduğunu gösteren bir <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="57549-123">The GetStockPrices.cs file demonstrates how to create custom tracking records from within a <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="57549-124">Bu kayıt için örnek çalıştırırken arayın.</span><span class="sxs-lookup"><span data-stu-id="57549-124">Look for this record when running the sample.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="57549-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="57549-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="57549-126">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WFStockPriceApplication.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="57549-126">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WFStockPriceApplication.sln solution file.</span></span>  
  
2.  <span data-ttu-id="57549-127">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="57549-127">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="57549-128">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="57549-128">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="57549-129">Bir tarayıcı penceresi açar ve dizin için uygulama listesi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="57549-129">The browser window opens and shows the directory listing for the application.</span></span>  
  
4.  <span data-ttu-id="57549-130">Tarayıcıda StockPriceService.xamlx'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="57549-130">In the browser, click StockPriceService.xamlx.</span></span>  
  
5.  <span data-ttu-id="57549-131">Tarayıcı görüntüler **StockPriceService** sayfası, yerel hizmet wsdl adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="57549-131">The browser displays the **StockPriceService** page, which contains the local service wsdl address.</span></span> <span data-ttu-id="57549-132">Bu adresini kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="57549-132">Copy this address.</span></span>  
  
     <span data-ttu-id="57549-133">Yerel Hizmet wsdl adresi http://localhost:53797/StockPriceService.xamlx?wsdl örnektir.</span><span class="sxs-lookup"><span data-stu-id="57549-133">An example of the local service wsdl address is http://localhost:53797/StockPriceService.xamlx?wsdl.</span></span>  
  
6.  <span data-ttu-id="57549-134">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]gidin, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] (varsayılan yükleme klasörüdür %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) klasör.</span><span class="sxs-lookup"><span data-stu-id="57549-134">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], go to your [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] folder (the default installation folder is %SystemDrive%\Program Files\Microsoft Visual Studio 10.0).</span></span> <span data-ttu-id="57549-135">Ardından Common7\IDE\ alt klasörü bulun.</span><span class="sxs-lookup"><span data-stu-id="57549-135">Then locate the Common7\IDE\ subfolder.</span></span>  
  
7.  <span data-ttu-id="57549-136">WCF Test İstemcisi başlatmak için WcfTestClient.exe dosyasını çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="57549-136">Double-click the WcfTestClient.exe file to launch the WCF Test Client.</span></span>  
  
8.  <span data-ttu-id="57549-137">WCF Test İstemcisi seçin **Hizmet Ekle...**</span><span class="sxs-lookup"><span data-stu-id="57549-137">In the WCF Test Client, select **Add Service…**</span></span> <span data-ttu-id="57549-138">gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="57549-138">from the **File** menu.</span></span>  
  
9. <span data-ttu-id="57549-139">Metin kutusuna kopyaladığınız URL'sini yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="57549-139">Paste the URL you just copied into the text box.</span></span>  
  
10. <span data-ttu-id="57549-140">Tıklatın **Tamam** iletişim kutusunu kapatmak için.</span><span class="sxs-lookup"><span data-stu-id="57549-140">Click **OK** to close the dialog.</span></span>  
  
11. <span data-ttu-id="57549-141">WCF Test İstemcisi'ni kullanarak hizmetini sınayın.</span><span class="sxs-lookup"><span data-stu-id="57549-141">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="57549-142">WCF Test istemcisi **GetStockPrice()** altında **IStockPriceService** düğümü.</span><span class="sxs-lookup"><span data-stu-id="57549-142">In the WCF Test Client, double-click **GetStockPrice()** under the **IStockPriceService** node.</span></span>  
  
         <span data-ttu-id="57549-143">**GetStockPrice()** yöntemi sağ bölmede, bir parametre ile görünür.</span><span class="sxs-lookup"><span data-stu-id="57549-143">The **GetStockPrice()** method appears in the right pane, with one parameter.</span></span>  
  
    2.  <span data-ttu-id="57549-144">Contoso'da parametresinin değeri olarak yazın.</span><span class="sxs-lookup"><span data-stu-id="57549-144">Type in Contoso as the value for the parameter.</span></span>  
  
    3.  <span data-ttu-id="57549-145">Tıklatın **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="57549-145">Click **Invoke**.</span></span>  
  
12. <span data-ttu-id="57549-146">İzlenen olayları, uygulama veri dizininde % APPDATA%\trackingRecords.log bulunan günlük dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="57549-146">See the tracked events in the log file located in your application data directory at %APPDATA%\trackingRecords.log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="57549-147">% APPDATA % %SystemDrive%\Users için çözümleyen bir ortam değişkenidir\\< kullanıcı adı\>içinde \AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], veya Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="57549-147">The %APPDATA% is an environment variable that resolves to %SystemDrive%\Users\\<username\>\AppData\Roaming in [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], or Windows Server 2008.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57549-148">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="57549-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="57549-149">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="57549-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="57549-150">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="57549-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57549-151">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="57549-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a><span data-ttu-id="57549-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57549-152">See Also</span></span>  
 [<span data-ttu-id="57549-153">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="57549-153">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
