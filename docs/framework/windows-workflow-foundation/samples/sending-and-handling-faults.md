---
title: Hata gönderme ve işleme
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406664"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="7c66b-102">Hata gönderme ve işleme</span><span class="sxs-lookup"><span data-stu-id="7c66b-102">Sending and Handling Faults</span></span>
<span data-ttu-id="7c66b-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> beklenen ve beklenmedik hataları gönderip etkinlikler ileti.</span><span class="sxs-lookup"><span data-stu-id="7c66b-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="7c66b-104">Bu senaryoda, ilk istemci isteği içinde bulunan bir beklenen hata sonuçlarında kendi <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7c66b-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="7c66b-105">Sonraki birkaç istemci istekleri son istek başarılı olmadan önce beklenmeyen hataları alma neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c66b-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="7c66b-106">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="7c66b-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="7c66b-107">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinlerle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="7c66b-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="7c66b-108">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="7c66b-109">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="7c66b-110">Hizmet projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="7c66b-111">İçinde **Çözüm Gezgini**, sağ `FaultService` seçin ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="7c66b-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="7c66b-112">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="7c66b-113">Başka bir kopyasını açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinlerle [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="7c66b-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="7c66b-114">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="7c66b-115">İstemci projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="7c66b-116">İçinde **Çözüm Gezgini**, sağ `FaultClient` seçin ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="7c66b-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="7c66b-117">CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="7c66b-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c66b-118">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7c66b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c66b-119">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c66b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c66b-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c66b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c66b-121">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7c66b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`