---
title: İş akışı hizmetlerinde iletileri biçimlendirme
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eb9a6b3a83a28154dc968bd4c1c41d34028bdd41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389143"
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="35871-102">İş akışı hizmetlerinde iletileri biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="35871-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="35871-103">Bu örnek nasıl farklı kullanıcı türleri kullanılabilir Mesajlaşma etkinlikleri (WF Hizmetleri) gösterir.</span><span class="sxs-lookup"><span data-stu-id="35871-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="35871-104">Örnek hizmet basit gider onay hizmetidir ve üç işlemini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="35871-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="35871-105">`ApproveExpense` bir veri anlaşması türü alır ve bilinen türleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="35871-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="35871-106">İşlem döndürür `true` veya `false` gider tutarını temel.</span><span class="sxs-lookup"><span data-stu-id="35871-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="35871-107">`ApprovePO` XmlSerializer türü alır ve döndürür `true` veya `false` gider tutarını temel.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="35871-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="35871-108">bir ileti anlaşması türü alır ve döndürür `true` veya `false` satıcı onaylanan satıcıları listesinde değilse veya istek (Finans departmanı, herhangi bir satıcı kullanabilirsiniz) Finans departmanında geldiyse.</span><span class="sxs-lookup"><span data-stu-id="35871-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="35871-109">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="35871-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="35871-110">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="35871-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="35871-111">İlk [çözüm temel dizini] \FormatterService\bin\debug\ içinde oluşturulan bir hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="35871-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="35871-112">İkinci olarak, [çözüm temel dizini] \FormatterClient\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="35871-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="35871-113">İstemci, üç hizmet işlemleri çağırır ve sonuçları yazdırır.</span><span class="sxs-lookup"><span data-stu-id="35871-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="35871-114">Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="35871-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="35871-115">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="35871-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="35871-116">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="35871-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="35871-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="35871-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35871-118">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="35871-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`