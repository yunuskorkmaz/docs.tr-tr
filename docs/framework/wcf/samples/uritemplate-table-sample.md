---
title: UriTemplate Tablo Örneği
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: ff88bdfe0c8c32da6f07f2b22de54af437376c51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596441"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="539f9-102">UriTemplate Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="539f9-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="539f9-103"><xref:System.UriTemplateTable>Sınıfı, bir örnek kümesiyle çalışmak için sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar `UriTemplate` .</span><span class="sxs-lookup"><span data-stu-id="539f9-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="539f9-104">Belirli bir Tekdüzen Kaynak tanımlayıcısı (URI), tablodaki tüm şablonlara göre etkili bir şekilde eşleştirilebilir ve eşleşen şablonla ilişkili veriler alınabilir.</span><span class="sxs-lookup"><span data-stu-id="539f9-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="539f9-105">Bu örnek, sınıfıyla ilgili aşağıdaki temel kavramları gösterir `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="539f9-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="539f9-106">Örneğini oluşturma için sözdizimi `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="539f9-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="539f9-107">Bir `UriTemplateTable` anahtar/değer çiftleri kümesiyle bir doldurma.</span><span class="sxs-lookup"><span data-stu-id="539f9-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="539f9-108">Kullanarak bir aday URI ile tabloyla eşleşen <xref:System.UriTemplateTable.MatchSingle%2A> .</span><span class="sxs-lookup"><span data-stu-id="539f9-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="539f9-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="539f9-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="539f9-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="539f9-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="539f9-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="539f9-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="539f9-112">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="539f9-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="539f9-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="539f9-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="539f9-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="539f9-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="539f9-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="539f9-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="539f9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="539f9-116">See also</span></span>

- [<span data-ttu-id="539f9-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="539f9-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="539f9-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="539f9-118">UriTemplate</span></span>](uritemplate-sample.md)
