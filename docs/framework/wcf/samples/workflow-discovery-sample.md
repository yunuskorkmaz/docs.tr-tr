---
title: "İş Akışı Keşif Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cf150562beaacb56596b90e1680adca97dd24a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="219d5-102">İş Akışı Keşif Örneği</span><span class="sxs-lookup"><span data-stu-id="219d5-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="219d5-103">Bu örnek bir iş akışı hizmeti bulunabilirlik yapma ve belirli bir hizmet için arar özel kod etkinlik yazmak nasıl gösterilir.</span><span class="sxs-lookup"><span data-stu-id="219d5-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="219d5-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="219d5-104">Demonstrates</span></span>  
 <span data-ttu-id="219d5-105">Bulma Bul etkinliği ve iş akışı kullanımı</span><span class="sxs-lookup"><span data-stu-id="219d5-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="219d5-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="219d5-106">Discussion</span></span>  
 <span data-ttu-id="219d5-107">Örnek ilk bölümünde, bir iş akışı hizmeti bulunabilirlik yapılan Yapılandırması'nı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="219d5-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="219d5-108">Yapılandırma, özel meta verileri (örneğin, kapsam) hizmetiyle uygun şekilde uygulamak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="219d5-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="219d5-109">İstemci üzerinde örnek bulma aramak için belirli bir sözleşme eşleşen bir hizmetini kullanan bir özel kod aktivitesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="219d5-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="219d5-110">Daha sonra Gönder etkinliği tarafından kullanılan bir URI kodunu aktivite çıkarır.</span><span class="sxs-lookup"><span data-stu-id="219d5-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="219d5-111">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="219d5-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="219d5-112">Bu örneği çalıştırmak için doğru URL ACL olmalıdır HTTP uç noktaları kullanır (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için).</span><span class="sxs-lookup"><span data-stu-id="219d5-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="219d5-113">Yükseltilmiş bir komut isteminde aşağıdaki komutu yürütülürken uygun ACL'ler eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="219d5-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="219d5-114">Kabuğunuzu değişken biçimi anlamıyorsa etki alanı ve kullanıcı adı şu bağımsız değişkenleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="219d5-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="219d5-115">**Netsh http add urlacl url = http: / / +: 8000 / kullanıcı etki alanı % =\\% UserName %**</span><span class="sxs-lookup"><span data-stu-id="219d5-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="219d5-116">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="219d5-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="219d5-117">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="219d5-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="219d5-118">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="219d5-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="219d5-119">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="219d5-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
