---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 28b325a6bd870282577a2989b616628d52262deb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711855"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="88d33-102">Zaman Uyumsuz İletişim</span><span class="sxs-lookup"><span data-stu-id="88d33-102">Asynchronous Communication</span></span>
<span data-ttu-id="88d33-103">Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimin zaman uyumsuz olarak varsayılan olarak nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88d33-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="88d33-104">Gösterir</span><span class="sxs-lookup"><span data-stu-id="88d33-104">Demonstrates</span></span>  
 <span data-ttu-id="88d33-105">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] hizmetleri arasında zaman uyumsuz iletişim.</span><span class="sxs-lookup"><span data-stu-id="88d33-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="88d33-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="88d33-106">Discussion</span></span>  
 <span data-ttu-id="88d33-107">Bu örnek, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamalar arasındaki iletişimin, .NET Framework tarafından sunulan mesajlaşma etkinliklerini kullanarak zaman uyumsuz olarak nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88d33-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="88d33-108">Bu örnek, aşağıdaki üç projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="88d33-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="88d33-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="88d33-109">CreditCheckService</span></span>  
 <span data-ttu-id="88d33-110">Bu hizmet belirli bir kişinin kredi Puanını veya alınacak öğenin değerini alır ve ardından kredinin kişiye verilip verilmeyeceğine karar verir.</span><span class="sxs-lookup"><span data-stu-id="88d33-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="88d33-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="88d33-111">RentalApprovalService</span></span>  
 <span data-ttu-id="88d33-112">Bu hizmet, bazı kredilerin olması gereken bir kişiden uygulama alır.</span><span class="sxs-lookup"><span data-stu-id="88d33-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="88d33-113">Bu hizmet, kredi uygulamasının geçerli olup olmadığına karar vermek için `CreditCheckService` ile zaman uyumsuz olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="88d33-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="88d33-114">İstemci</span><span class="sxs-lookup"><span data-stu-id="88d33-114">Client</span></span>  
 <span data-ttu-id="88d33-115">İstemci, kredinin onaylanıp onaylanmadığını bildirmek için `RentalApprovalService` ile eşzamanlı olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="88d33-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88d33-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="88d33-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="88d33-117">**AsynchronousCommunication** çözümüne sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="88d33-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="88d33-118">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve **birden çok başlangıç**projesi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="88d33-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="88d33-119">**RentalApprovalService** ' i listedeki ilk konuma, ardından **CreditCheckService**ve ardından **Client**' a taşıyın.</span><span class="sxs-lookup"><span data-stu-id="88d33-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="88d33-120">Her üç projede de **Başlangıç** eylemini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="88d33-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="88d33-121">**Tamam**' a tıklayın ve örneği çalıştırmak için F5 ' e basın.</span><span class="sxs-lookup"><span data-stu-id="88d33-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="88d33-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="88d33-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88d33-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="88d33-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="88d33-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="88d33-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88d33-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="88d33-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
