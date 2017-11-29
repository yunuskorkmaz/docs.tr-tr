---
title: "UriTemplate Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 729a48fe0ea34bf1630824d941341fff82ade1ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-sample"></a><span data-ttu-id="9268b-102">UriTemplate Örneği</span><span class="sxs-lookup"><span data-stu-id="9268b-102">UriTemplate Sample</span></span>
<span data-ttu-id="9268b-103"><xref:System.UriTemplate> Sınıfı ortak bir yapıya sahiptir URI'ler kümesi ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9268b-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="9268b-104">Bu örnek ile ilgili aşağıdaki temel kavramları göstermektedir `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="9268b-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="9268b-105">Şablonları oluşturmak için söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="9268b-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="9268b-106">Gelen URI başlatmasını bir `UriTemplate` kullanarak <xref:System.UriTemplate.BindByName%2A> ve <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="9268b-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="9268b-107"><xref:System.UriTemplateTable.Match%2A>, ters işlemi olduğu `BindByName` ve `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="9268b-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9268b-108">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9268b-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9268b-109">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9268b-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="9268b-110">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9268b-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9268b-111">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="9268b-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9268b-112">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9268b-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9268b-113">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9268b-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9268b-114">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9268b-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="9268b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9268b-115">See Also</span></span>  
 [<span data-ttu-id="9268b-116">UriTemplate tablosu</span><span class="sxs-lookup"><span data-stu-id="9268b-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="9268b-117">UriTemplate tablosu dağıtıcısı</span><span class="sxs-lookup"><span data-stu-id="9268b-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
