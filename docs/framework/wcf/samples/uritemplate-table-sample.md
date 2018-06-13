---
title: UriTemplate Tablo Örneği
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: ef445e30257e9bf99e111c1a1f569e42c2017b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504204"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="7c43c-102">UriTemplate Tablo Örneği</span><span class="sxs-lookup"><span data-stu-id="7c43c-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="7c43c-103"><xref:System.UriTemplateTable> Sınıfı, bir dizi birlikte çalışmaya yönelik bir sözlük benzeri ilişkilendirilebilir tablo yapısı sağlar `UriTemplate` örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c43c-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="7c43c-104">Belirli Tekdüzen Kaynak Tanımlayıcıları (URI'ler) verimli bir şekilde tablosundaki tüm şablonları karşı eşleştirilir ve eşleşen şablonuyla ilişkili veriler alınabilir.</span><span class="sxs-lookup"><span data-stu-id="7c43c-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="7c43c-105">Bu örnek ile ilgili aşağıdaki temel kavramları göstermektedir `UriTemplateTable` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="7c43c-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="7c43c-106">Örnek oluşturma söz dizimi bir `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="7c43c-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="7c43c-107">Doldurma bir `UriTemplateTable` bir anahtar/değer çifti kümesi ile.</span><span class="sxs-lookup"><span data-stu-id="7c43c-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="7c43c-108">Tabloyu kullanarak karşı bir aday URI eşleşen <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c43c-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c43c-109">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7c43c-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7c43c-110">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7c43c-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="7c43c-111">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7c43c-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c43c-112">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="7c43c-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7c43c-113">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c43c-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c43c-114">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c43c-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c43c-115">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7c43c-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="7c43c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c43c-116">See Also</span></span>  
 [<span data-ttu-id="7c43c-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="7c43c-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="7c43c-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="7c43c-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
