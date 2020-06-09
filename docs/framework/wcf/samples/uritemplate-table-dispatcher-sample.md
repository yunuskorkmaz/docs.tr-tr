---
title: UriTemplate Tablosu Dağıtıcı Örneği
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591078"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="799fc-102">UriTemplate Tablosu Dağıtıcı Örneği</span><span class="sxs-lookup"><span data-stu-id="799fc-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="799fc-103"><xref:System.UriTemplateTable>Sınıfı, bir örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar <xref:System.UriTemplate> .</span><span class="sxs-lookup"><span data-stu-id="799fc-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="799fc-104">Bu örnek `UriTemplateTable` , sınıfı için ortak bir kullanım senaryosu kullanılarak oluşturulan temel bir gönderme altyapısını gösterir `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="799fc-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="799fc-105">Bu örnek, sınıfı için aşağıdaki temel kavramları gösterir `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="799fc-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="799fc-106">Temsilcileri bir ile ilişkilendirme `UriTemplates` `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="799fc-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="799fc-107"><xref:System.UriTemplateTable.MatchSingle%2A>Belirli BIR URI için doğru işleyici temsilcisini almak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="799fc-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="799fc-108">İsteği işlemek için işleyici temsilcisi çağrılıyor.</span><span class="sxs-lookup"><span data-stu-id="799fc-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="799fc-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="799fc-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="799fc-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="799fc-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="799fc-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="799fc-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="799fc-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="799fc-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="799fc-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="799fc-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="799fc-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="799fc-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="799fc-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="799fc-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="799fc-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="799fc-116">See also</span></span>

- [<span data-ttu-id="799fc-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="799fc-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="799fc-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="799fc-118">UriTemplate</span></span>](uritemplate-sample.md)
