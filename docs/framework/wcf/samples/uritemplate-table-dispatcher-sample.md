---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143687"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="4ca06-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="4ca06-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="4ca06-103">Sınıf, <xref:System.UriTemplateTable> bir dizi <xref:System.UriTemplate> örnekle çalışmak için sözlük benzeri ilişkilendirici tablo yapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ca06-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="4ca06-104">Bu örnek, `UriTemplateTable` `UriTemplateTable` sınıf için ortak bir kullanım senaryosu olan kullanılarak oluşturulmuş temel bir gönderme motoru gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ca06-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="4ca06-105">Bu `UriTemplateTable` örnek, sınıf için aşağıdaki anahtar kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="4ca06-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="4ca06-106">Bir `UriTemplates` `UriTemplateTable`içinde delegeler ilişkilendirme .</span><span class="sxs-lookup"><span data-stu-id="4ca06-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="4ca06-107">Belirli <xref:System.UriTemplateTable.MatchSingle%2A> bir URI için doğru işleyici temsilcisini elde etmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="4ca06-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="4ca06-108">İsteği işlemek için işleyici temsilciçağırmak.</span><span class="sxs-lookup"><span data-stu-id="4ca06-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ca06-109">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4ca06-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4ca06-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4ca06-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="4ca06-111">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4ca06-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4ca06-112">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ca06-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ca06-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4ca06-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4ca06-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="4ca06-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ca06-115">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ca06-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="4ca06-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ca06-116">See also</span></span>

- [<span data-ttu-id="4ca06-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="4ca06-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="4ca06-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4ca06-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
