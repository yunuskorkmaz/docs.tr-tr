---
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 5f8a969a9ddea633d12ebe2d922c152dbb0d7241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322621"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="c09b3-102">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="c09b3-102">UriTemplate Sample</span></span>
<span data-ttu-id="c09b3-103"><xref:System.UriTemplate> Sınıfı, ortak bir yapıya sahiptir URI'ler kümesi ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c09b3-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="c09b3-104">Bu örnek, ilgili aşağıdaki temel kavramları gösterir `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="c09b3-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="c09b3-105">Şablonları oluşturmaya yönelik söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="c09b3-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="c09b3-106">Gelen bir URI'leri örnekleme bir `UriTemplate` kullanarak <xref:System.UriTemplate.BindByName%2A> ve <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="c09b3-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="c09b3-107"><xref:System.UriTemplateTable.Match%2A>, ters işlemi olduğu `BindByName` ve `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="c09b3-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c09b3-108">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c09b3-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c09b3-109">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c09b3-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="c09b3-110">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c09b3-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c09b3-111">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="c09b3-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c09b3-112">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c09b3-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c09b3-113">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c09b3-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c09b3-114">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c09b3-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="c09b3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c09b3-115">See also</span></span>

- [<span data-ttu-id="c09b3-116">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="c09b3-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="c09b3-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="c09b3-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
