---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 800765c6b01e49b730414132ac64ab8eed3e9e5f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330837"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="ca778-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="ca778-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="ca778-103"><xref:System.UriTemplateTable> Sınıfı bir dizi birlikte çalışmak için bir sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ca778-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="ca778-104">Bu örnek, bir temel dispatching altyapısı kullanılarak oluşturulan gösterir `UriTemplateTable`, genel bir kullanım senaryosu `UriTemplateTable` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ca778-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="ca778-105">Bu örnek aşağıdaki kavramlar gösterir `UriTemplateTable` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="ca778-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="ca778-106">Temsilcileri ile ilişkilendirme `UriTemplates` içinde bir `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="ca778-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="ca778-107">Kullanarak <xref:System.UriTemplateTable.MatchSingle%2A> belirli bir URI için doğru işleyici temsilcisini almak için.</span><span class="sxs-lookup"><span data-stu-id="ca778-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="ca778-108">İsteği işlemek için işleyici temsilcisini çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="ca778-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca778-109">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ca778-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ca778-110">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca778-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="ca778-111">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ca778-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca778-112">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ca778-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca778-113">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ca778-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ca778-114">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ca778-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca778-115">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ca778-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="ca778-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca778-116">See also</span></span>

- [<span data-ttu-id="ca778-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="ca778-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="ca778-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ca778-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
