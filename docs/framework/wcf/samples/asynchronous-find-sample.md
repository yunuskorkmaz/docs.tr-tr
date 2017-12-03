---
title: "Zaman Uyumsuz Bulma Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 229e2ff6e630527e3735e3c48f698f582b0b60f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-find-sample"></a><span data-ttu-id="9cc49-102">Zaman Uyumsuz Bulma Örneği</span><span class="sxs-lookup"><span data-stu-id="9cc49-102">Asynchronous Find Sample</span></span>
<span data-ttu-id="9cc49-103">Bu örnek, bir istemci uygulaması zaman uyumsuz bulma işlemi kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-103">This sample shows how to use the asynchronous find operation from a client application.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9cc49-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9cc49-104">Sample Details</span></span>  
 <span data-ttu-id="9cc49-105">Bu tasarım deseni aşağıdaki avantajı, istemci bulma isteği sonucunda bulunan uç noktaları zaman uyumsuz olarak bildirilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-105">The benefit of following this design pattern is that the client is notified asynchronously of the endpoints located as a result of the find request.</span></span> <span data-ttu-id="9cc49-106">Bunun nasıl çalıştığını görmek için Client.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9cc49-106">To see how this works, open the Client.cs file.</span></span> <span data-ttu-id="9cc49-107">Not <xref:System.ServiceModel.Discovery.DiscoveryClient> nesnesi iki temsilciler olayı olarak işleyicilerinin sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-107">Note the <xref:System.ServiceModel.Discovery.DiscoveryClient> object has two delegates attached to its event handlers.</span></span> <span data-ttu-id="9cc49-108">Bir temsilci çağrılır bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> olayı oluşturulur ve her zaman başka adlı bir <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> olayı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9cc49-108">One delegate is called when a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> event is raised and another is called each time a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> event is raised.</span></span> <span data-ttu-id="9cc49-109">Örnek nasıl uygulamanızda bu deseni kullanabilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-109">The sample shows how you can utilize this pattern in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc49-110">Bu örnek HTTP uç noktaları kullanır ve çalıştırmak için doğru URL ACL eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-110">This sample uses HTTP endpoints and to run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="9cc49-111">[HTTP ve HTTPS yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="9cc49-111"> [Configuring HTTP and HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="9cc49-112">Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-112">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="9cc49-113">Komut olduğu gibi çalışmazsa şu bağımsız değişkenleri için kullanıcı adı ve etki alanı yerine isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cc49-113">You may want to substitute your domain and username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9cc49-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9cc49-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9cc49-115">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], AsyncFind.sln açın.</span><span class="sxs-lookup"><span data-stu-id="9cc49-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the AsyncFind.sln.</span></span>  
  
2.  <span data-ttu-id="9cc49-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9cc49-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="9cc49-117">Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi ve \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug veya \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug dizinine gidin ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9cc49-117">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug or \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug directory and run Service.exe.</span></span>  
  
4.  <span data-ttu-id="9cc49-118">Hizmeti başlatıldıktan sonra \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug ya da WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug dizine gidin ve Client.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9cc49-118">After the service has started, navigate to the \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug or WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug directory and run Client.exe.</span></span>  
  
5.  <span data-ttu-id="9cc49-119">İstemci bulun ve hizmeti çağırmak mümkün gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="9cc49-119">Observe the client is able to locate and call the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9cc49-120">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cc49-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9cc49-121">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9cc49-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9cc49-122">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9cc49-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9cc49-123">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9cc49-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a><span data-ttu-id="9cc49-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9cc49-124">See Also</span></span>
