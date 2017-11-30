---
title: "İçeriğe dayalı bağıntı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 03c37fd66b8e03661d793b22a98c1816bf5042c9
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="content-based-correlation"></a><span data-ttu-id="011cc-102">İçeriğe dayalı bağıntı</span><span class="sxs-lookup"><span data-stu-id="011cc-102">Content-Based Correlation</span></span>
<span data-ttu-id="011cc-103">Bu örnek gösterilmektedir nasıl Mesajlaşma etkinlikleri (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>) içerik tabanlı birden çok içerik tabanlı correlations.and bağıntı ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="011cc-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="011cc-104">Bu senaryoda, satın alma siparişi kimliği temel alarak bir bağıntı önce başlatılır ve başka bir bağıntı daha sonra müşteri kimliği temel alınarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="011cc-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="011cc-105">Bu durum gösterilir ve nasıl bir <xref:System.ServiceModel.Activities.Receive> etkinlik hem mevcut bir bağıntı izleyin ve aynı gelen iletisini temel alarak yeni bir bağıntı başlatma.</span><span class="sxs-lookup"><span data-stu-id="011cc-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="011cc-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="011cc-106">Demonstrates</span></span>  
 <span data-ttu-id="011cc-107">Mesajlaşma etkinlikleri ve içerik tabanlı bağıntı</span><span class="sxs-lookup"><span data-stu-id="011cc-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="011cc-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="011cc-108">Discussion</span></span>  
 <span data-ttu-id="011cc-109">Bu örnek, birden çok içerik tabanlı bağıntıları kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="011cc-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="011cc-110">Bu senaryoda, satın alma siparişi kimliği temel alarak bir bağıntı önce başlatılır ve başka bir bağıntı daha sonra müşteri kimliği temel alınarak oluşturulur</span><span class="sxs-lookup"><span data-stu-id="011cc-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="011cc-111">Kullanarak bağıntıları basamaklı bir <xref:System.ServiceModel.Activities.Receive> var olan bir bağıntı (PurchaseOrderID) izleyen hem de yeni bir bağıntı (CustomerID) başlatır etkinlik tabanlı aynı gelen ileti üzerinde.</span><span class="sxs-lookup"><span data-stu-id="011cc-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="011cc-112">Bunu başarmak için <xref:System.ServiceModel.Activities.Receive> aktivitesi kullanır <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> ve <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="011cc-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="011cc-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="011cc-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="011cc-114">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="011cc-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="011cc-115">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CascadingCorrelation.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="011cc-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="011cc-116">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="011cc-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="011cc-117">Sunucu çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="011cc-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="011cc-118">Hizmet, Çözüm Gezgini'nde, iletileri için hazır ve dinleme sonra istemci projesine sağ tıklayın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="011cc-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="011cc-119">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="011cc-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="011cc-120">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="011cc-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="011cc-121">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="011cc-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="011cc-122">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="011cc-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`