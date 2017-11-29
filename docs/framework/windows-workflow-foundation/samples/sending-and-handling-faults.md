---
title: "Gönderme ve hata işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57d522918d280c9a8a68fcd420b7216cc48216d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="9820d-102">Gönderme ve hata işleme</span><span class="sxs-lookup"><span data-stu-id="9820d-102">Sending and Handling Faults</span></span>
<span data-ttu-id="9820d-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> Mesajlaşma etkinlikleri beklenen ve beklenmeyen hataları alıp göndermek için.</span><span class="sxs-lookup"><span data-stu-id="9820d-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="9820d-104">Bu senaryoda, ilk istemci isteği içinde bulunan bir beklenen hatasına sonuçlarında kendi <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9820d-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="9820d-105">Son istekten başarılı olmadan önce beklenmeyen hataları alma sonraki birkaç istemci istekleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="9820d-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="9820d-106">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="9820d-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="9820d-107">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="9820d-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="9820d-108">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9820d-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="9820d-109">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9820d-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="9820d-110">Hizmet projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9820d-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="9820d-111">İçinde **Çözüm Gezgini**, sağ `FaultService` proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="9820d-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="9820d-112">CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9820d-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="9820d-113">Başka bir kopyasını açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="9820d-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="9820d-114">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="9820d-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="9820d-115">İstemci projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9820d-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="9820d-116">İçinde **Çözüm Gezgini**, sağ `FaultClient` proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="9820d-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="9820d-117">CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9820d-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9820d-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9820d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9820d-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9820d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9820d-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9820d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9820d-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9820d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="9820d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9820d-122">See Also</span></span>
