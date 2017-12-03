---
title: "Zaman uyumsuz iletişim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea2d705a38ddae1689d212bbd50196920fe73fe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="asynchronous-communication"></a><span data-ttu-id="02844-102">Zaman uyumsuz iletişim</span><span class="sxs-lookup"><span data-stu-id="02844-102">Asynchronous Communication</span></span>
<span data-ttu-id="02844-103">Bu örnek gösterilmektedir nasıl iki farklı arasındaki iletişimi [!INCLUDE[wf](../../../../includes/wf-md.md)] Hizmetleri zaman uyumsuz olarak varsayılan olarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="02844-103">This sample demonstrates how the communication between two different [!INCLUDE[wf](../../../../includes/wf-md.md)] services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="02844-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="02844-104">Demonstrates</span></span>  
 <span data-ttu-id="02844-105">Zaman uyumsuz iletişim arasında [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="02844-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="02844-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="02844-106">Discussion</span></span>  
 <span data-ttu-id="02844-107">Bu örnek göstermektedir nasıl arasındaki iletişimi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamaları yapılır zaman uyumsuz olarak .NET Framework tarafından sağlanan Mesajlaşma etkinlikleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="02844-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="02844-108">Bu örnek, aşağıdaki üç projeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="02844-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="02844-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="02844-109">CreditCheckService</span></span>  
 <span data-ttu-id="02844-110">Bu hizmet, belirli bir kişinin kredi puanı veya edinmek için öğenin değerini alır ve kredi kişiye verilen olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="02844-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="02844-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="02844-111">RentalApprovalService</span></span>  
 <span data-ttu-id="02844-112">Bu hizmetin gerekli bazı alacak olan bir kişi bir uygulamayı alır.</span><span class="sxs-lookup"><span data-stu-id="02844-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="02844-113">Bu hizmet zaman uyumsuz olarak iletişim kurar `CreditCheckService` kredi uygulama geçerli olup olmadığına karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="02844-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="02844-114">İstemci</span><span class="sxs-lookup"><span data-stu-id="02844-114">Client</span></span>  
 <span data-ttu-id="02844-115">İstemci eş zamanlı olarak iletişim kurar `RentalApprovalService` kredi onaylanmış olup olmadığını bilmek.</span><span class="sxs-lookup"><span data-stu-id="02844-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02844-116">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="02844-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="02844-117">Sağ **AsynchronousCommunication** çözümü ve select **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="02844-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="02844-118">İçinde **ortak özellikleri**seçin **başlangıç projesi**seçip **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="02844-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="02844-119">Taşıma **RentalApprovalService** listedeki ilk konumuna arkasından **CreditCheckService**, ardından **istemci**.</span><span class="sxs-lookup"><span data-stu-id="02844-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="02844-120">Ayarlama **Başlat** üç projenin eylem.</span><span class="sxs-lookup"><span data-stu-id="02844-120">Set the **Start** action on all three projects.</span></span>  
  
4.  <span data-ttu-id="02844-121">Tıklatın **Tamam**, örneği çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="02844-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="02844-122">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="02844-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="02844-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="02844-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="02844-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="02844-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02844-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="02844-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
