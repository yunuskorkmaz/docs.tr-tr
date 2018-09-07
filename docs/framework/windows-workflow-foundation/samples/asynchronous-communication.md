---
title: Zaman uyumsuz iletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e85f7efb0de1326ceb5091c305b20f34809eab57
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047093"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="1e452-102">Zaman uyumsuz iletişim</span><span class="sxs-lookup"><span data-stu-id="1e452-102">Asynchronous Communication</span></span>
<span data-ttu-id="1e452-103">Bu örnek, iki farklı Windows Workflow Foundation (WF) hizmetler arasındaki iletişimi varsayılan olarak zaman uyumsuz olarak nasıl yapılacağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e452-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1e452-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="1e452-104">Demonstrates</span></span>  
 <span data-ttu-id="1e452-105">Zaman uyumsuz iletişim arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="1e452-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1e452-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="1e452-106">Discussion</span></span>  
 <span data-ttu-id="1e452-107">Bu örnek, gösterir nasıl arasındaki iletişimi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamaları yapılır zaman uyumsuz olarak .NET Framework tarafından sağlanan ileti etkinlikleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1e452-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="1e452-108">Bu örnek, aşağıdaki üç projeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="1e452-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="1e452-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="1e452-109">CreditCheckService</span></span>  
 <span data-ttu-id="1e452-110">Bu hizmet, belirli bir kişinin kredi puan veya edinmek için öğenin değerini alır ve ardından kredi kişiye verilir karar verir.</span><span class="sxs-lookup"><span data-stu-id="1e452-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="1e452-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="1e452-111">RentalApprovalService</span></span>  
 <span data-ttu-id="1e452-112">Bu hizmet, bir uygulama geçirilmesi gereken bazı alacak olan bir kişiden alır.</span><span class="sxs-lookup"><span data-stu-id="1e452-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="1e452-113">Bu hizmet zaman uyumsuz olarak iletişim kurar `CreditCheckService` kredi başvurusunun geçerli olup olmadığına karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="1e452-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="1e452-114">İstemci</span><span class="sxs-lookup"><span data-stu-id="1e452-114">Client</span></span>  
 <span data-ttu-id="1e452-115">İstemci eş zamanlı olarak iletişim kurar `RentalApprovalService` kredi onaylanmış olup olmadığını bilmek.</span><span class="sxs-lookup"><span data-stu-id="1e452-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1e452-116">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1e452-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1e452-117">Sağ **AsynchronousCommunication** çözüm ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1e452-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="1e452-118">İçinde **ortak özellikler**seçin **başlangıç projesi**seçip **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="1e452-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="1e452-119">Taşıma **RentalApprovalService** ve ardından listedeki ilk konuma **CreditCheckService**çizgidir **istemci**.</span><span class="sxs-lookup"><span data-stu-id="1e452-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="1e452-120">Ayarlama **Başlat** üç projenin tamamına eylem.</span><span class="sxs-lookup"><span data-stu-id="1e452-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="1e452-121">Tıklayın **Tamam**, örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e452-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e452-122">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="1e452-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1e452-123">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1e452-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e452-124">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1e452-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e452-125">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e452-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
