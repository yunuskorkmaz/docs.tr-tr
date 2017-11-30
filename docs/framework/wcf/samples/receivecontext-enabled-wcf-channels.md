---
title: "ReceiveContext etkinleştirilmiş WCF kanalları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec3b161ec9dedc2cbf389d8ec5ac4629cf54e007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="81455-102">ReceiveContext etkinleştirilmiş WCF kanalları</span><span class="sxs-lookup"><span data-stu-id="81455-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="81455-103">Bu örnek yararlılığı gösteren <xref:System.ServiceModel.Channels.ReceiveContext>-WCF kanalları etkin.</span><span class="sxs-lookup"><span data-stu-id="81455-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="81455-104">Örnek NetMSMQ kanalı kullanılarak iki sayının çarpımını bulmak için bir hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="81455-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="81455-105"><xref:System.ServiceModel.Channels.ReceiveContext> Sınıfı erişim iletisi veya iletinin içeriğini bile inceledikten sonra daha fazla işleme için sıraya bırakın karar vermek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="81455-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="81455-106">Bu örnekte, bir istemci için bir işlem sırası rastgele tamsayılar gönderir.</span><span class="sxs-lookup"><span data-stu-id="81455-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="81455-107">`ProductCalculator` Hizmeti iletileri alır ve ürünün hesaplanan olup olmadığını belirlemek için tamsayı olduğunu iletisi içeriği olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="81455-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="81455-108">Hizmet işlemini ürün işlem değil, ileti geri sıraya konur ve sıra üzerinde dinleme hizmeti tarafından tekrar alınabilir.</span><span class="sxs-lookup"><span data-stu-id="81455-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="81455-109">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="81455-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="81455-110">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="81455-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="81455-111">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="81455-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="81455-112">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="81455-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="81455-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="81455-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="81455-114">Microsoft Message Queuing (MSMQ) yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="81455-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="81455-115">MSMQ yüklemek için [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="81455-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="81455-116">İçinde **Sunucu Yöneticisi'ni**, tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="81455-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="81455-117">Sağ bölmede altında **Özellik Özeti**, tıklatın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="81455-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="81455-118">Sonuçta elde edilen penceresinde **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="81455-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="81455-119">Genişletme **Message Queuing Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="81455-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="81455-120">Tıklatın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) ve ardından **HTTP desteği**.</span><span class="sxs-lookup"><span data-stu-id="81455-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="81455-121">Tıklatın **sonraki**ve ardından **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="81455-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="81455-122">MSMQ yüklemek için [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="81455-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="81455-123">Açık **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="81455-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="81455-124">Tıklatın **programları** ve ardından, **programlar ve Özellikler**, tıklatın **Windows özelliklerini açma ve kapatma**.</span><span class="sxs-lookup"><span data-stu-id="81455-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="81455-125">Genişletme **Microsoft Message Queue (MSMQ) sunucusu**, genişletin **Microsoft Message Queue (MSMQ) Sunucu Çekirdeği**ve ardından yüklemek aşağıdaki olan Message Queuing özelliklerin onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="81455-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="81455-126">Message Queuing sunucusu</span><span class="sxs-lookup"><span data-stu-id="81455-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="81455-127">MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için)</span><span class="sxs-lookup"><span data-stu-id="81455-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="81455-128">MSMQ HTTP desteği</span><span class="sxs-lookup"><span data-stu-id="81455-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="81455-129">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="81455-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="81455-130">Bilgisayarı yeniden başlatmanız istenirse, tıklatın **Tamam** yüklemeyi tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="81455-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="81455-131">Emin [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bilgisayara yüklendi.</span><span class="sxs-lookup"><span data-stu-id="81455-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="81455-132">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ReceiveContextProductGenerator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="81455-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="81455-133">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="81455-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="81455-134">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="81455-134">To run the solution, press CTRL+F5.</span></span>
