---
title: "TransactedReceiveScope kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 23117014b688f0b440da3cec8620023eaf212f71
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="use-of-transactedreceivescope"></a><span data-ttu-id="cf656-102">TransactedReceiveScope kullanımı</span><span class="sxs-lookup"><span data-stu-id="cf656-102">Use of TransactedReceiveScope</span></span>
<span data-ttu-id="cf656-103">Bu örnek kullanarak bir sunucu için bir istemciden bir işlem akışı gösterilmektedir <xref:System.Activities.Statements.TransactionScope> istemci üzerinde yeni bir işlem oluşturmak için ve bir <xref:System.ServiceModel.Activities.TransactedReceiveScope> akışlı bir işlem içeren bir ileti almak ve sunucu üzerindeki işlem ömrü kapsam için.</span><span class="sxs-lookup"><span data-stu-id="cf656-103">This sample shows how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="cf656-104">Örnek, istemci ve sunucu rolleri dolduran iki projeden oluşan.</span><span class="sxs-lookup"><span data-stu-id="cf656-104">The sample consists of two projects that fill the roles of client and server.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="cf656-105">İstemci uygulaması</span><span class="sxs-lookup"><span data-stu-id="cf656-105">Client Application</span></span>  
 <span data-ttu-id="cf656-106">İstemci uygulaması dağıtılmış işlem kimliği yazdırır, sunucuya bir ileti gönderir, işlem akışlar, yanıtı alır, dağıtılmış işlem kimliği yeniden yazdırır ve tamamlandıktan bir iş akışı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cf656-106">The client application runs a workflow that prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="cf656-107">Dağıtılmış işlem kimliği başlangıçta baskı siparişi olduğunda, işlem hala yalnızca yerel olarak boş bir GUID olur.</span><span class="sxs-lookup"><span data-stu-id="cf656-107">When the distributed transaction ID is initially prints, it is an empty GUID as the transaction is still only local.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="cf656-108">Sunucu uygulaması</span><span class="sxs-lookup"><span data-stu-id="cf656-108">Server Application</span></span>  
 <span data-ttu-id="cf656-109">Sunucu projesi benzer, ancak, iş akışı içinde barındırılan <xref:System.ServiceModel.Activities.WorkflowServiceHost> istemciden gelen iletiyi için bunu bir uç noktası üzerinde dinleme gerekir çünkü.</span><span class="sxs-lookup"><span data-stu-id="cf656-109">The server project is similar, however, the workflow is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> because it must listen on an endpoint for the message from the client.</span></span> <span data-ttu-id="cf656-110">İş akışı üzerinde ortalanır <xref:System.ServiceModel.Activities.TransactedReceiveScope>, istemciden akışlı işlem aldığı gönderildi, dağıtılmış işlem kimliği yazdırır ve yanıt istemciye gönderir. ileti yazdırır.</span><span class="sxs-lookup"><span data-stu-id="cf656-110">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the message that was sent, prints the distributed transaction ID and sends the reply to the client.</span></span> <span data-ttu-id="cf656-111">Dağıtılmış işlem kimliği boş olmayan GUID ve işlem algılayan bir etkinlik gövdesi ile eklendiyse sunulmuştur <xref:System.ServiceModel.Activities.TransactedReceiveScope>, akan işlem altında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="cf656-111">The distributed transaction ID is now a non-empty GUID and if a transaction-aware activity was added to the body of the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, it would execute under the flowed transaction.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="cf656-112">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cf656-112">To run the sample</span></span>  
  
1.  <span data-ttu-id="cf656-113">TransactedReceiveScope.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf656-113">Open the TransactedReceiveScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf656-114">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cf656-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="cf656-115">Derleme başarılı olduktan sonra çözüme sağ tıklayın ve seçin **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="cf656-115">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="cf656-116">İletişim kutusundan seçin **birden fazla başlangıç projesi** ve her iki projeleri için eylem olun **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="cf656-116">From the dialog, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="cf656-117">F5 tuşuna basın veya seçin **hata ayıklamayı Başlat** gelen **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cf656-117">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="cf656-118">Alternatif olarak, CTRL + F5 tuşuna basın veya seçin **hata ayıklama olmadan Başlat** gelen **hata ayıklama** menü hata ayıklama olmadan çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="cf656-118">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cf656-119">Sunucu, istemci başlatmadan önce çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf656-119">The server must be running prior to starting the client.</span></span> <span data-ttu-id="cf656-120">Barındırma hizmeti konsol penceresinden çıktı ne zaman başlatıldığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf656-120">The output from the console window hosting the service indicates when it has started.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cf656-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf656-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cf656-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cf656-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cf656-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cf656-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cf656-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf656-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`