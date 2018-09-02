---
title: Zaman Uyumsuz Bulma Örneği
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424397"
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="b473d-102">Zaman Uyumsuz Bulma Örneği</span><span class="sxs-lookup"><span data-stu-id="b473d-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="b473d-103">Bu örnek, bir istemci uygulamasında zaman uyumsuz bulma işlemi işlemi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b473d-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b473d-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b473d-104">Sample Details</span></span>  
 <span data-ttu-id="b473d-105">Bu tasarım deseni aşağıdaki istemci bulma isteği sonucunda bulunan uç noktaları zaman uyumsuz olarak bildirilir avantajdır.</span><span class="sxs-lookup"><span data-stu-id="b473d-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="b473d-106">Nasıl çalıştığını görmek için Client.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b473d-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="b473d-107">Not <xref:System.ServiceModel.Discovery.DiscoveryClient> nesnesi iki Temsilciler, olay işleyicilerinin sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b473d-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="b473d-108">Bir temsilci çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> olayı oluşturulur ve başka her zaman çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b473d-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="b473d-109">Örnek, uygulamanızda bu düzeni nasıl kullanabileceği gösterir.</span><span class="sxs-lookup"><span data-stu-id="b473d-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b473d-110">Bu örnek HTTP uç noktaları kullanır ve çalıştırmak için uygun URL'yi ACL'leri eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b473d-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> <span data-ttu-id="b473d-111">Daha fazla bilgi için [yapılandırma HTTP ve HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="b473d-111">For more information, see [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="b473d-112">Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b473d-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="b473d-113">Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler için kullanıcı adı ve etki alanı yerine isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b473d-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b473d-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b473d-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b473d-115">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AsyncFind.sln açın.</span><span class="sxs-lookup"><span data-stu-id="b473d-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="b473d-116">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b473d-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="b473d-117">Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug veya \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug dizine gidin ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b473d-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="b473d-118">Hizmet başlatıldıktan sonra \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug veya WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug dizine gidin ve Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b473d-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="b473d-119">İstemci bulun ve hizmet çağrısı gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="b473d-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b473d-120">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b473d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b473d-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b473d-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b473d-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b473d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b473d-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b473d-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="b473d-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b473d-124">See Also</span></span>
