---
title: Gönderme ve hata işleme
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 6796b4daccd88adc3bd006f454ce96ca155fbcb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516132"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="46a9b-102">Gönderme ve hata işleme</span><span class="sxs-lookup"><span data-stu-id="46a9b-102">Sending and Handling Faults</span></span>
<span data-ttu-id="46a9b-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> Mesajlaşma etkinlikleri beklenen ve beklenmeyen hataları alıp göndermek için.</span><span class="sxs-lookup"><span data-stu-id="46a9b-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="46a9b-104">Bu senaryoda, ilk istemci isteği içinde bulunan bir beklenen hatasına sonuçlarında kendi <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="46a9b-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="46a9b-105">Son istekten başarılı olmadan önce beklenmeyen hataları alma sonraki birkaç istemci istekleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="46a9b-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="46a9b-106">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="46a9b-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="46a9b-107">Açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="46a9b-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="46a9b-108">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="46a9b-109">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="46a9b-110">Hizmet projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="46a9b-111">İçinde **Çözüm Gezgini**, sağ `FaultService` proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="46a9b-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="46a9b-112">CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="46a9b-113">Başka bir kopyasını açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklanarak yükseltilmiş izinleri olan [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini ve seçerek **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="46a9b-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="46a9b-114">Faults.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="46a9b-115">İstemci projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="46a9b-116">İçinde **Çözüm Gezgini**, sağ `FaultClient` proje ve seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="46a9b-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="46a9b-117">CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="46a9b-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46a9b-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="46a9b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46a9b-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46a9b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46a9b-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="46a9b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46a9b-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="46a9b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`