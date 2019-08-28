---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 724a13504cea2672aef7ff155fbbff055aac34e6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044583"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="2ea73-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="2ea73-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="2ea73-103">Sınıfı <xref:System.UriTemplateTable> , bir <xref:System.UriTemplate> örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ea73-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="2ea73-104">Bu örnek, `UriTemplateTable` sınıfı için ortak bir kullanım senaryosu `UriTemplateTable`kullanılarak oluşturulan temel bir gönderme altyapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ea73-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="2ea73-105">Bu örnek, `UriTemplateTable` sınıfı için aşağıdaki temel kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="2ea73-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="2ea73-106">Temsilcileri bir `UriTemplates` `UriTemplateTable`ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="2ea73-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="2ea73-107">Belirli <xref:System.UriTemplateTable.MatchSingle%2A> bir URI için doğru işleyici temsilcisini almak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="2ea73-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="2ea73-108">İsteği işlemek için işleyici temsilcisi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="2ea73-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ea73-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2ea73-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2ea73-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2ea73-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2ea73-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2ea73-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2ea73-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ea73-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2ea73-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2ea73-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2ea73-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="2ea73-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ea73-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ea73-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="2ea73-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea73-116">See also</span></span>

- [<span data-ttu-id="2ea73-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="2ea73-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="2ea73-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2ea73-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
