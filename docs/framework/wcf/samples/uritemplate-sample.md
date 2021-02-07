---
description: 'Daha fazla bilgi edinin: UriTemplate örneği'
title: UriTemplate Örneği
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 80e932c06a6819ef7e1e289d9eacab6cd4e55f92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685445"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="7854d-103">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="7854d-103">UriTemplate Sample</span></span>

<span data-ttu-id="7854d-104"><xref:System.UriTemplate>Sınıfı, ortak bir yapıyı paylaşan URI kümeleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7854d-104">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="7854d-105">Bu örnek, ile ilgili aşağıdaki temel kavramları göstermektedir `UriTemplate` :</span><span class="sxs-lookup"><span data-stu-id="7854d-105">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="7854d-106">Şablon oluşturma sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="7854d-106">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="7854d-107">Bir `UriTemplate` using ve kullanarak URI 'leri örnekleme <xref:System.UriTemplate.BindByName%2A> <xref:System.UriTemplate.BindByPosition%2A> .</span><span class="sxs-lookup"><span data-stu-id="7854d-107">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="7854d-108"><xref:System.UriTemplateTable.Match%2A>, ve ' nin ters işlemidir `BindByName` `BindByPosition` .</span><span class="sxs-lookup"><span data-stu-id="7854d-108"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7854d-109">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7854d-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7854d-110">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7854d-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="7854d-111">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7854d-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7854d-112">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7854d-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7854d-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7854d-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7854d-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7854d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7854d-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7854d-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="7854d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7854d-116">See also</span></span>

- [<span data-ttu-id="7854d-117">UriTemplate Tablosu</span><span class="sxs-lookup"><span data-stu-id="7854d-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="7854d-118">UriTemplate Tablosu Dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="7854d-118">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
