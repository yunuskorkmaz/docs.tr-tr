---
title: "İşlem Convoy kapsamı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b5fc8834fb72163a615633d81232e25768683278
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-convoy-scope"></a><span data-ttu-id="7b80e-102">İşlem Convoy kapsamı</span><span class="sxs-lookup"><span data-stu-id="7b80e-102">Transaction Convoy Scope</span></span>
<span data-ttu-id="7b80e-103">Bu örnek nasıl paralel etkinlik düzeni ile birlikte Mesajlaşma Convoy oluşturulduğunu gösteren bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> burada birkaç işlem oluşabilir tüm aynı işlem altında herhangi bir sırada bir protokol modellemek için.</span><span class="sxs-lookup"><span data-stu-id="7b80e-103">This sample demonstrates how to create a Parallel Convoy messaging activity pattern in conjunction with a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to model a protocol where a number of operations can happen in any order all under the same transaction.</span></span> <span data-ttu-id="7b80e-104">Bu örnek ayrıca gösterir nasıl bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> istemci kullanmayan şekilde bir sunucuya akıtılan değil, yeni bir işlem otomatik olarak oluşturur işlemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-104">This sample also demonstrates how a <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatically creates a new transaction when one is not flowed to the server, so the client does not make use of any transactions.</span></span>  
  
 <span data-ttu-id="7b80e-105">Örnek istemci ve sunucu temsil eden iki iş akışı projeleri oluşur.</span><span class="sxs-lookup"><span data-stu-id="7b80e-105">The sample consists of two workflow projects that represent the client and server.</span></span> <span data-ttu-id="7b80e-106">İstemci projesi bir bağıntı başlatır ve mesajlaşma etkinlikleri geri kalanı için bir işlem kapsamı başlatır sunucu iş akışı bootstrap isteyen bir ileti göndererek başlayan bir iş akışı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="7b80e-106">The client project runs a workflow that begins by sending a message to bootstrap the server workflow, which initializes a correlation and starts a transactional scope for the remainder of the messaging activities.</span></span> <span data-ttu-id="7b80e-107">İstemci <xref:System.Activities.Statements.Sequence> etkinlik içeren bir ilk <xref:System.ServiceModel.Activities.Send> ve <xref:System.ServiceModel.Activities.ReceiveReply> çifti ve ardından bir <xref:System.Activities.Statements.Parallel> üç dalları etkinlikle.</span><span class="sxs-lookup"><span data-stu-id="7b80e-107">The client <xref:System.Activities.Statements.Sequence> activity contains an initial <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> pair and then a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="7b80e-108">Her dal sunucuya tek yönlü bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="7b80e-108">Each branch sends a one-way message to the server.</span></span> <span data-ttu-id="7b80e-109"><xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Özelliği <xref:System.Activities.Statements.Parallel> etkinlik ayarlanmış `false` böylece tüm üç dalları tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-109">The <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> property of the <xref:System.Activities.Statements.Parallel> activity is set to `false` so that all three branches complete.</span></span>  
  
 <span data-ttu-id="7b80e-110">Sunucu iş akışı Mesajlaşma etkinlikleri iletişimi sunucu tarafı doğru yerleştirilir ve içinde yer alan dışındaki istemci iş akışına benzer bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> etkinlik tüm Bitti'yi çalışmak üzere aynı işlemde yürütür.</span><span class="sxs-lookup"><span data-stu-id="7b80e-110">The server workflow is similar to the client workflow except the messaging activities are oriented towards the server side of the communication and they are contained within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity so that all work done executes under the same transaction.</span></span> <span data-ttu-id="7b80e-111">Sunucuda ilk ileti alındığında, bir işlem oluşturulur ve kapsamını ortam yapılan <xref:System.ServiceModel.Activities.TransactedReceiveScope> bu kapsam içinde herhangi bir etkinlik işlem erişebilmesi için gövde.</span><span class="sxs-lookup"><span data-stu-id="7b80e-111">When the first message is received on the server, a transaction is created and is made ambient for the scope of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body so that any activity within this scope can access the transaction.</span></span> <span data-ttu-id="7b80e-112">Bundan sonra tüm alan paralel olarak yürütün.</span><span class="sxs-lookup"><span data-stu-id="7b80e-112">After this, all receives execute in parallel.</span></span> <span data-ttu-id="7b80e-113">Tüm alır gereken tam olarak bir kez üzerinde paralel etkinlik tamamlanma koşul tarafından açıklandığı gibi yürütün.</span><span class="sxs-lookup"><span data-stu-id="7b80e-113">All receives must execute exactly once as described by the completion condition on the parallel activity.</span></span> <span data-ttu-id="7b80e-114">Sonunda örtük Kalıcılık noktanız var <xref:System.ServiceModel.Activities.TransactedReceiveScope> gövde ve sürdürme işlemi aynı işlemde yürütülen de.</span><span class="sxs-lookup"><span data-stu-id="7b80e-114">An implicit persistence point exists at the end of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body and the persistence operation is also executed under the same transaction.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7b80e-115">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7b80e-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="7b80e-116">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ParallelConvoySample.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-116">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ParallelConvoySample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7b80e-117">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-117">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7b80e-118">Her iki proje başlatmak için ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b80e-118">Ensure both projects are set to start.</span></span>  
  
    1.  <span data-ttu-id="7b80e-119">İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="7b80e-119">In **Solution Explorer**, right-click the solution and select **Set Startup Projects**.</span></span>  
  
    2.  <span data-ttu-id="7b80e-120">Seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem ayarlandığından emin olun **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="7b80e-120">Select **Multiple Startup Projects** and ensure the action for both projects is set to **Start**.</span></span>  
  
4.  <span data-ttu-id="7b80e-121">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-121">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="7b80e-122">Sunucu baskı siparişi `Server is running`, sunucunun belirten hazırdır.</span><span class="sxs-lookup"><span data-stu-id="7b80e-122">The server prints `Server is running`, which indicates the server is ready.</span></span>  
  
     <span data-ttu-id="7b80e-123">Örnek başlatmak için istemci konsol penceresinde herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="7b80e-123">Press any key in the client console window to start the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b80e-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b80e-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b80e-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b80e-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b80e-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7b80e-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b80e-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b80e-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`  
  
## <a name="see-also"></a><span data-ttu-id="7b80e-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b80e-128">See Also</span></span>
