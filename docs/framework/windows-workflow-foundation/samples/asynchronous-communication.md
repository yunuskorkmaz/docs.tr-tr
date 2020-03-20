---
title: Zaman Uyumsuz İletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142882"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="565d6-102">Zaman Uyumsuz İletişim</span><span class="sxs-lookup"><span data-stu-id="565d6-102">Asynchronous Communication</span></span>
<span data-ttu-id="565d6-103">Bu örnek, iki farklı Windows İş Akışı Temeli (WF) hizmeti arasındaki iletişimin varsayılan olarak nasıl eşzamanlı olarak yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="565d6-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="565d6-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="565d6-104">Demonstrates</span></span>  
 <span data-ttu-id="565d6-105">Hizmetler arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] eşzamanlı iletişim.</span><span class="sxs-lookup"><span data-stu-id="565d6-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="565d6-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="565d6-106">Discussion</span></span>  
 <span data-ttu-id="565d6-107">Bu örnek, .NET [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Framework tarafından sağlanan ileti etkinlikleri kullanılarak uygulamalar arasındaki iletişimin nasıl eş senkronize bir şekilde yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="565d6-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="565d6-108">Bu örnek aşağıdaki üç projeden oluşmaktadır.</span><span class="sxs-lookup"><span data-stu-id="565d6-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="565d6-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="565d6-109">CreditCheckService</span></span>  
 <span data-ttu-id="565d6-110">Bu hizmet, belirli bir kişinin kredi puanını veya elde edilen maddenin değerini alır ve sonra kredinin kişiye verilip verilmeyeceğine karar verir.</span><span class="sxs-lookup"><span data-stu-id="565d6-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="565d6-111">Kiralama Onay Hizmeti</span><span class="sxs-lookup"><span data-stu-id="565d6-111">RentalApprovalService</span></span>  
 <span data-ttu-id="565d6-112">Bu hizmet, krediye ihtiyacı olan bir kişiden bir uygulama alır.</span><span class="sxs-lookup"><span data-stu-id="565d6-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="565d6-113">Bu hizmet, kredi başvurusunun `CreditCheckService` geçerli olup olmadığına karar vermek için eş senkronize olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="565d6-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="565d6-114">İstemci</span><span class="sxs-lookup"><span data-stu-id="565d6-114">Client</span></span>  
 <span data-ttu-id="565d6-115">İstemci, kredinin onaylanıp onaylanmadığını öğrenmek `RentalApprovalService` için senkronize olarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="565d6-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="565d6-116">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="565d6-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="565d6-117">**AsynchronousCommunication** çözümünü sağ tıklatın ve **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="565d6-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="565d6-118">**Ortak**Özellikler'de, **Başlangıç Projesi'ni**seçin ve **Birden Çok Başlangıç Projesi'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="565d6-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="565d6-119">**RentalApprovalService** listede ilk pozisyona taşıyın, **CreditCheckService**takip , **Müşteri**izledi .</span><span class="sxs-lookup"><span data-stu-id="565d6-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="565d6-120">Üç projede de **Başlat** eylemini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="565d6-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="565d6-121">**Tamam'ı**tıklatın ve örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="565d6-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="565d6-122">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="565d6-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="565d6-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="565d6-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="565d6-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="565d6-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="565d6-125">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="565d6-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
