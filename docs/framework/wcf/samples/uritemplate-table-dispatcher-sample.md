---
title: "UriTemplate Tablosu Dağıtıcı Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3574183f0900c853bd3ff541aabc8fc6b7fcd157
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="ee47e-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="ee47e-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="ee47e-103"><xref:System.UriTemplateTable> Sınıfı, bir dizi birlikte çalışmaya yönelik bir sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ee47e-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="ee47e-104">Bu örnek kullanılarak oluşturulmuş bir temel dağıtırken altyapısı gösteren `UriTemplateTable`, genel bir kullanım senaryosu `UriTemplateTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ee47e-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="ee47e-105">Bu örnek için aşağıdaki anahtar kavramları göstermektedir `UriTemplateTable` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="ee47e-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="ee47e-106">Temsilcileri ile ilişkilendirme `UriTemplates` içinde bir `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="ee47e-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="ee47e-107">Kullanarak <xref:System.UriTemplateTable.MatchSingle%2A> belirli bir URI doğru işleyici temsilcisi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ee47e-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="ee47e-108">İsteği işlemek için işleyici temsilcisi çağırma.</span><span class="sxs-lookup"><span data-stu-id="ee47e-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee47e-109">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ee47e-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ee47e-110">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee47e-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="ee47e-111">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee47e-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee47e-112">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ee47e-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee47e-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ee47e-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee47e-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ee47e-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee47e-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ee47e-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="ee47e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee47e-116">See Also</span></span>  
 [<span data-ttu-id="ee47e-117">UriTemplate tablosu</span><span class="sxs-lookup"><span data-stu-id="ee47e-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="ee47e-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ee47e-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
