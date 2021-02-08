---
description: 'Daha fazla bilgi edinin: UriTemplate Tablo dağıtıcısı örneği'
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 68cd7e87c9768995210f369e2d55a10ad048e338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798205"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="21963-103">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="21963-103">UriTemplate Table Dispatcher Sample</span></span>

<span data-ttu-id="21963-104"><xref:System.UriTemplateTable>Sınıfı, bir örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> .</span><span class="sxs-lookup"><span data-stu-id="21963-104">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="21963-105">Bu örnek `UriTemplateTable` , sınıfı için ortak bir kullanım senaryosu kullanılarak oluşturulan temel bir gönderme altyapısını gösterir `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="21963-105">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="21963-106">Bu örnek, sınıfı için aşağıdaki temel kavramları gösterir `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="21963-106">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="21963-107">Temsilcileri bir ile ilişkilendirme `UriTemplates` `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="21963-107">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="21963-108"><xref:System.UriTemplateTable.MatchSingle%2A>Belirli BIR URI için doğru işleyici temsilcisini almak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="21963-108">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="21963-109">İsteği işlemek için işleyici temsilcisi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="21963-109">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21963-110">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="21963-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="21963-111">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="21963-111">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="21963-112">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="21963-112">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="21963-113">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="21963-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="21963-114">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="21963-114">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="21963-115">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="21963-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21963-116">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="21963-116">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="21963-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21963-117">See also</span></span>

- [<span data-ttu-id="21963-118">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="21963-118">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="21963-119">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="21963-119">UriTemplate</span></span>](uritemplate-sample.md)
