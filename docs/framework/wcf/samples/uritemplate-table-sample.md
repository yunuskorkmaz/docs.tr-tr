---
title: UriTemplate Tablo Örneği
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 174c0035adb0b38ddb18f79f9cc4d76d3db46b74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962910"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="019d7-102">UriTemplate Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="019d7-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="019d7-103">Sınıfı <xref:System.UriTemplateTable> , bir `UriTemplate` örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="019d7-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="019d7-104">Belirli bir Tekdüzen Kaynak tanımlayıcısı (URI), tablodaki tüm şablonlara göre etkili bir şekilde eşleştirilebilir ve eşleşen şablonla ilişkili veriler alınabilir.</span><span class="sxs-lookup"><span data-stu-id="019d7-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="019d7-105">Bu örnek, `UriTemplateTable` sınıfıyla ilgili aşağıdaki temel kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="019d7-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="019d7-106">Örneğini oluşturma `UriTemplateTable`için sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="019d7-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="019d7-107">Bir anahtar `UriTemplateTable` /değer çiftleri kümesiyle bir doldurma.</span><span class="sxs-lookup"><span data-stu-id="019d7-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="019d7-108">Kullanarak bir aday URI ile <xref:System.UriTemplateTable.MatchSingle%2A>tabloyla eşleşen.</span><span class="sxs-lookup"><span data-stu-id="019d7-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="019d7-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="019d7-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="019d7-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="019d7-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="019d7-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="019d7-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="019d7-112">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="019d7-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="019d7-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="019d7-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="019d7-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="019d7-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="019d7-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="019d7-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="019d7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="019d7-116">See also</span></span>

- [<span data-ttu-id="019d7-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="019d7-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="019d7-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="019d7-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
