---
title: "HTTP Doğrulama Kanalı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9081b47284b63315d950ef791389312df32815f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="http-acknowledgement-channel"></a><span data-ttu-id="757cf-102">HTTP Doğrulama Kanalı</span><span class="sxs-lookup"><span data-stu-id="757cf-102">HTTP Acknowledgement Channel</span></span>
<span data-ttu-id="757cf-103">HTTP doğrulama kanalı tek yönlü Mesajlaşma düzeni, onaylayabilir veya gelen iletileri reddetmek bir hizmet veren otomatik olarak bir bildirim alındığında göndermek yerine değişiklikleri katmanlı bir kanal örneğidir.</span><span class="sxs-lookup"><span data-stu-id="757cf-103">The HTTP Acknowledgement Channel is an example of a layered channel that changes the one-way messaging pattern, allowing a service to acknowledge or refuse incoming messages rather than automatically sending an acknowledgement on receipt.</span></span> <span data-ttu-id="757cf-104">İleti işleme, iş düzeyi garantisi yapabilirsiniz kadar HTTP doğrulama kanalı gecikme bildirim hizmete de sağlar.</span><span class="sxs-lookup"><span data-stu-id="757cf-104">The HTTP Acknowledgement Channel also allows the service to delay acknowledgement until it can make a business-level guarantee that the message will be processed.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="757cf-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="757cf-105">Demonstrates</span></span>  
 <span data-ttu-id="757cf-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Katmanlı kanal örnek (HTTP doğrulama kanalı).</span><span class="sxs-lookup"><span data-stu-id="757cf-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Layered channel example (HTTP Acknowledgement channel).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="757cf-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="757cf-107">Discussion</span></span>  
 <span data-ttu-id="757cf-108">HTTP doğrulama kanalı uygulayan <xref:System.ServiceModel.Channels.ReceiveContext> Gecikmeli bildirim ile tek yönlü bir desenle HTTP istek-yanıt Mesajlaşma düzeni yeniden şekillendirmek için.</span><span class="sxs-lookup"><span data-stu-id="757cf-108">The HTTP Acknowledgement Channel implements <xref:System.ServiceModel.Channels.ReceiveContext> to reshape the HTTP request-reply messaging pattern to a one-way pattern with delayed acknowledgement.</span></span> <span data-ttu-id="757cf-109">Bu yeni desenini kullanarak, bir hizmet ileti işleme ileti işleme tamamlanana veya bir hata iletisi biçiminde bir HTTP istemci gönderebilirsiniz kadar istemci engellenmeden bir HTTP Tamam durum kodu 200 biçiminde bir bildirim göndererek emin olabilirsiniz İç sunucu hatası durum kodu 500.</span><span class="sxs-lookup"><span data-stu-id="757cf-109">Using this new pattern, a service can ensure message processing by sending an acknowledgement in the form of an HTTP OK status code of 200 without blocking the client until message processing completes or can send a failure message to the client in the form of an HTTP Internal Server error status code of 500.</span></span> <span data-ttu-id="757cf-110">Örneğin, bir hizmet bir sıraya bir ileti yazdıktan sonra bir bildirim göndermek ve iletisini zaman uyumsuz olarak işleme devam.</span><span class="sxs-lookup"><span data-stu-id="757cf-110">For example, a service could send an acknowledgement after writing a message to a queue, and then continue processing the message asynchronously.</span></span> <span data-ttu-id="757cf-111">Bir bildirim hizmetinden alınan kadar her ileti yeniden göndermeden, bu senaryoda, bir istemci kendi iletileri en az bir kez hizmeti tarafından işlenen gösterilmeyeceği.</span><span class="sxs-lookup"><span data-stu-id="757cf-111">In this scenario, a client could be assured its messages were processed at least once by the service, if it re-sent each message until it received an acknowledgement from the service.</span></span> <span data-ttu-id="757cf-112">Bir hizmeti hızlı zaman uyumsuz ileti işleme garantileri, herhangi bir iletisi HTTP üzerinden işleme gerektiriyorsa, Not sonra <xref:System.ServiceModel.Channels.OneWayBindingElement> daha uygun bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="757cf-112">Note that, if a service requires fast asynchronous message processing over HTTP without any message processing guarantees, then the <xref:System.ServiceModel.Channels.OneWayBindingElement> is a more appropriate choice.</span></span>  
  
 <span data-ttu-id="757cf-113"><xref:System.ServiceModel.Channels.ReceiveContext>iletinin ileti hizmeti işleme alınacak belirlenir yerinde tutarken için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="757cf-113"><xref:System.ServiceModel.Channels.ReceiveContext> is used to hold the message in place while it is determined whether the message can be processed at the service.</span></span> <span data-ttu-id="757cf-114">Bir hizmeti başarıyla ileti işleme yeteneği üzerinde tam çağrılarak gösterilen <xref:System.ServiceModel.Channels.ReceiveContext> gönderdiği Tamam HTTP durum kodu ve hizmet iletisi olup olmadığını işleyebilir nesne çağırarak belirtilir <xref:System.ServiceModel.Channels.ReceiveContext>'s `Abandon` yöntemini <xref:System.ServiceModel.Channels.ReceiveContext> bir HTTP iç sunucu hatası durum kodu gönderir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="757cf-114">The ability of a service to successfully process the message is indicated by calling Complete on the <xref:System.ServiceModel.Channels.ReceiveContext> object that sends an HTTP OK status code and whether the service can process the message is indicated by calling <xref:System.ServiceModel.Channels.ReceiveContext>’s `Abandon` method on the <xref:System.ServiceModel.Channels.ReceiveContext> object, which sends an HTTP Internal Server error status code.</span></span>  
  
 <span data-ttu-id="757cf-115">Bu örnekte, bir çalışan kimliği göndererek işleme bilgileri istemci istekleri</span><span class="sxs-lookup"><span data-stu-id="757cf-115">In this example, the client requests processing information by sending an employee ID.</span></span> <span data-ttu-id="757cf-116">Hizmet uç alınan çalışan kimliği 50'den büyükse hizmeti bir HTTP durum kodu 500 (Dahili Sunucu hatası) istemciye geri gönderir, aksi takdirde bu işlem başarıyla yapılabilir ve bir HTTP durum kodu 200 (gönderir varsayılır Başarılı) istemciye.</span><span class="sxs-lookup"><span data-stu-id="757cf-116">On the service end, if the employee ID received is greater than 50, the service sends an HTTP Status code of 500 (Internal Server Error) back to the client, otherwise it is assumed that the processing can be successfully done and sends an HTTP Status code of 200 (Successful) to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="757cf-117">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="757cf-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="757cf-118">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="757cf-118">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with Administrator privileges.</span></span>  
  
2.  <span data-ttu-id="757cf-119">Açık **HttpAckChannel** çözümü.</span><span class="sxs-lookup"><span data-stu-id="757cf-119">Open the **HttpAckChannel** solution.</span></span>  
  
3.  <span data-ttu-id="757cf-120">Yeni bir örneğini Başlat **hizmet** sağ tıklayarak projede Proje **Çözüm Gezgini**, seçerek **hata ayıklama**, **başlangıç yeni örnek** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="757cf-120">Start a new instance of the **Service** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, **Start new instance** from the context menu.</span></span>  
  
4.  <span data-ttu-id="757cf-121">Yeni bir örneğini Başlat **istemci** sağ tıklayarak projede Proje **Çözüm Gezgini**, seçerek **hata ayıklama**, ve **başlangıç yeni örnek** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="757cf-121">Start a new instance of the **Client** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, and **Start new instance** from the context menu.</span></span>  
  
5.  <span data-ttu-id="757cf-122">Hizmet başladıktan sonra hizmete bir ileti göndermek istemci izin vermek için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="757cf-122">Once the service has started, press ENTER in the client window to let the client send a message to the service.</span></span>  
  
6.  <span data-ttu-id="757cf-123">İlk iletinin hizmette işlenir ve bir HTTP Tamam durum kodu istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="757cf-123">The first message is processed on the service, and it sends an HTTP OK status code back to the client.</span></span>  
  
7.  <span data-ttu-id="757cf-124">İkinci bir ileti başarısız olur ve bir HTTP iç sunucu hatası durum kodu oluşturan istemciye, gönderen bir <xref:System.ServiceModel.CommunicationException> istemci üzerinde.</span><span class="sxs-lookup"><span data-stu-id="757cf-124">The second message is unsuccessful, and it sends an HTTP Internal Server error status code back to the client, which raises a <xref:System.ServiceModel.CommunicationException> on the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="757cf-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="757cf-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="757cf-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="757cf-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="757cf-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="757cf-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="757cf-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="757cf-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
