---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: e2ec85027274f302c59673a3d937be8f03d0b43b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715360"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="e92a8-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="e92a8-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="e92a8-103"><xref:System.UriTemplateTable> sınıfı, bir <xref:System.UriTemplate> örnekleri kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e92a8-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="e92a8-104">Bu örnek, `UriTemplateTable` sınıfı için ortak bir kullanım senaryosu olan `UriTemplateTable`kullanılarak oluşturulan temel bir gönderme altyapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e92a8-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="e92a8-105">Bu örnek `UriTemplateTable` sınıfı için aşağıdaki temel kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="e92a8-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="e92a8-106">Temsilcileri bir `UriTemplateTable``UriTemplates` ile ilişkilendirme.</span><span class="sxs-lookup"><span data-stu-id="e92a8-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="e92a8-107">Belirli bir URI için doğru işleyici temsilcisini almak üzere <xref:System.UriTemplateTable.MatchSingle%2A> kullanma.</span><span class="sxs-lookup"><span data-stu-id="e92a8-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="e92a8-108">İsteği işlemek için işleyici temsilcisi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="e92a8-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e92a8-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e92a8-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e92a8-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e92a8-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e92a8-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="e92a8-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e92a8-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e92a8-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e92a8-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e92a8-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e92a8-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e92a8-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e92a8-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e92a8-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="e92a8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e92a8-116">See also</span></span>

- [<span data-ttu-id="e92a8-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="e92a8-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="e92a8-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e92a8-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
