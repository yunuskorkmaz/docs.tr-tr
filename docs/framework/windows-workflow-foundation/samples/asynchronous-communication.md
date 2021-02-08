---
description: 'Daha fazla bilgi edinin: zaman uyumsuz Iletişim'
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 3e824c03a07682faaf60d8434f6af1a26742ead7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792602"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="0fbfa-103">Zaman Uyumsuz İletişim</span><span class="sxs-lookup"><span data-stu-id="0fbfa-103">Asynchronous Communication</span></span>

<span data-ttu-id="0fbfa-104">Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimin zaman uyumsuz olarak varsayılan olarak nasıl yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-104">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0fbfa-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0fbfa-105">Demonstrates</span></span>  

 <span data-ttu-id="0fbfa-106">Hizmetler arasında zaman uyumsuz iletişim [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0fbfa-106">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0fbfa-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="0fbfa-107">Discussion</span></span>  

 <span data-ttu-id="0fbfa-108">Bu örnek, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .NET Framework tarafından sunulan mesajlaşma etkinliklerini kullanarak uygulamalar arasındaki iletişimin zaman uyumsuz olarak nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-108">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="0fbfa-109">Bu örnek, aşağıdaki üç projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-109">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="0fbfa-110">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="0fbfa-110">CreditCheckService</span></span>  
 <span data-ttu-id="0fbfa-111">Bu hizmet belirli bir kişinin kredi Puanını veya alınacak öğenin değerini alır ve ardından kredinin kişiye verilip verilmeyeceğine karar verir.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-111">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="0fbfa-112">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="0fbfa-112">RentalApprovalService</span></span>  
 <span data-ttu-id="0fbfa-113">Bu hizmet, bazı kredilerin olması gereken bir kişiden uygulama alır.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-113">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="0fbfa-114">Bu hizmet, `CreditCheckService` kredi uygulamasının geçerli olup olmadığına karar vermek için ile zaman uyumsuz olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-114">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="0fbfa-115">İstemci</span><span class="sxs-lookup"><span data-stu-id="0fbfa-115">Client</span></span>  
 <span data-ttu-id="0fbfa-116">İstemci, `RentalApprovalService` kredinin onaylanıp onaylanmadığını bildirmek için ile eşzamanlı olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-116">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0fbfa-117">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0fbfa-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0fbfa-118">**AsynchronousCommunication** çözümüne sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-118">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="0fbfa-119">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve **birden çok başlangıç** projesi ' ni seçin.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-119">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="0fbfa-120">**RentalApprovalService** ' i listedeki ilk konuma, ardından **CreditCheckService** ve ardından **Client**' a taşıyın.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-120">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="0fbfa-121">Her üç projede de **Başlangıç** eylemini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-121">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="0fbfa-122">**Tamam**' a tıklayın ve örneği çalıştırmak için F5 ' e basın.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-122">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0fbfa-123">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0fbfa-124">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0fbfa-125">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0fbfa-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0fbfa-126">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0fbfa-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
