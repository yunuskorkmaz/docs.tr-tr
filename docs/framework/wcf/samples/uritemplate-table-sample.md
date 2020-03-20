---
title: UriTemplate Tablo Örneği
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183261"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="34632-102">UriTemplate Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="34632-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="34632-103">Sınıf, <xref:System.UriTemplateTable> bir dizi `UriTemplate` örnekle çalışmak için sözlük benzeri ilişkilendirici tablo yapısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="34632-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="34632-104">Belirli Tekdüzen Kaynak Tanımlayıcıları (URI'ler) tablodaki tüm şablonlarla verimli bir şekilde eşlenebilir ve eşleşen şablonla ilişkili veriler alınabilir.</span><span class="sxs-lookup"><span data-stu-id="34632-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="34632-105">Bu örnek, `UriTemplateTable` sınıfla ilgili aşağıdaki anahtar kavramları gösterir:</span><span class="sxs-lookup"><span data-stu-id="34632-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="34632-106">Bir `UriTemplateTable`' yi anlık olarak sindizim</span><span class="sxs-lookup"><span data-stu-id="34632-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="34632-107">A'yı `UriTemplateTable` anahtar/değer çiftleri kümesiyle doldurma.</span><span class="sxs-lookup"><span data-stu-id="34632-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="34632-108">Bir aday URI'yi <xref:System.UriTemplateTable.MatchSingle%2A>kullanarak tabloyla eşleştirme</span><span class="sxs-lookup"><span data-stu-id="34632-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="34632-109">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="34632-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="34632-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="34632-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="34632-111">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="34632-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34632-112">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="34632-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="34632-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="34632-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="34632-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="34632-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34632-115">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="34632-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="34632-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34632-116">See also</span></span>

- [<span data-ttu-id="34632-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="34632-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="34632-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="34632-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
