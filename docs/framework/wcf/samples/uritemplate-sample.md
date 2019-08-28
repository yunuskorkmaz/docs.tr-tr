---
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 15799c1aaf3ed7df5f7721368dea426665dcf335
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044593"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="366f2-102">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="366f2-102">UriTemplate Sample</span></span>
<span data-ttu-id="366f2-103">Sınıfı <xref:System.UriTemplate> , ortak bir yapıyı paylaşan URI kümeleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="366f2-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="366f2-104">Bu örnek, ile ilgili `UriTemplate`aşağıdaki temel kavramları göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="366f2-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="366f2-105">Şablon oluşturma sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="366f2-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="366f2-106">Bir `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> ve<xref:System.UriTemplate.BindByPosition%2A>kullanarak URI 'leri örnekleme.</span><span class="sxs-lookup"><span data-stu-id="366f2-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="366f2-107"><xref:System.UriTemplateTable.Match%2A>, ve `BindByName` `BindByPosition`' nin ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="366f2-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="366f2-108">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="366f2-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="366f2-109">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="366f2-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="366f2-110">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="366f2-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="366f2-111">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="366f2-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="366f2-112">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="366f2-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="366f2-113">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="366f2-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="366f2-114">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="366f2-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="366f2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="366f2-115">See also</span></span>

- [<span data-ttu-id="366f2-116">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="366f2-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="366f2-117">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="366f2-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
