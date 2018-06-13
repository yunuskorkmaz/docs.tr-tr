---
title: Zaman uyumsuz iletişim
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 9eafeab89aefb181ae016dc0219f9155d9bd2a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515166"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="3cb96-102">Zaman uyumsuz iletişim</span><span class="sxs-lookup"><span data-stu-id="3cb96-102">Asynchronous Communication</span></span>
<span data-ttu-id="3cb96-103">Bu örnekte, iki farklı Windows Workflow Foundation (WF) hizmeti arasındaki iletişimi varsayılan olarak zaman uyumsuz olarak nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3cb96-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3cb96-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3cb96-104">Demonstrates</span></span>  
 <span data-ttu-id="3cb96-105">Zaman uyumsuz iletişim arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="3cb96-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="3cb96-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="3cb96-106">Discussion</span></span>  
 <span data-ttu-id="3cb96-107">Bu örnek göstermektedir nasıl arasındaki iletişimi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamaları yapılır zaman uyumsuz olarak .NET Framework tarafından sağlanan Mesajlaşma etkinlikleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3cb96-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="3cb96-108">Bu örnek, aşağıdaki üç projeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="3cb96-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="3cb96-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="3cb96-109">CreditCheckService</span></span>  
 <span data-ttu-id="3cb96-110">Bu hizmet, belirli bir kişinin kredi puanı veya edinmek için öğenin değerini alır ve kredi kişiye verilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3cb96-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="3cb96-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="3cb96-111">RentalApprovalService</span></span>  
 <span data-ttu-id="3cb96-112">Bu hizmetin gerekli bazı alacak olan bir kişi bir uygulamayı alır.</span><span class="sxs-lookup"><span data-stu-id="3cb96-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="3cb96-113">Bu hizmet zaman uyumsuz olarak iletişim kurar `CreditCheckService` kredi uygulama geçerli olup olmadığına karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="3cb96-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="3cb96-114">İstemci</span><span class="sxs-lookup"><span data-stu-id="3cb96-114">Client</span></span>  
 <span data-ttu-id="3cb96-115">İstemci eş zamanlı olarak iletişim kurar `RentalApprovalService` kredi onaylanmış olup olmadığını bilmek.</span><span class="sxs-lookup"><span data-stu-id="3cb96-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3cb96-116">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3cb96-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3cb96-117">Sağ **AsynchronousCommunication** çözümü ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3cb96-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="3cb96-118">İçinde **ortak özellikleri**seçin **başlangıç projesi**seçip **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="3cb96-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="3cb96-119">Taşıma **RentalApprovalService** listedeki ilk konumuna arkasından **CreditCheckService**, ardından **istemci**.</span><span class="sxs-lookup"><span data-stu-id="3cb96-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="3cb96-120">Ayarlama **Başlat** üç projenin eylem.</span><span class="sxs-lookup"><span data-stu-id="3cb96-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="3cb96-121">Tıklatın **Tamam**, örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3cb96-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3cb96-122">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3cb96-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3cb96-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3cb96-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3cb96-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3cb96-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3cb96-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3cb96-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
