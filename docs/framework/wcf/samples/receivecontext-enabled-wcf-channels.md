---
title: ReceiveContext etkinleştirilmiş WCF kanalları
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442752"
---
# <a name="receivecontext-enabled-wcf-channels"></a><span data-ttu-id="96356-102">ReceiveContext etkinleştirilmiş WCF kanalları</span><span class="sxs-lookup"><span data-stu-id="96356-102">ReceiveContext-Enabled WCF Channels</span></span>
<span data-ttu-id="96356-103">Bu örnek kullanışlılığını gösterir <xref:System.ServiceModel.Channels.ReceiveContext>-etkinleştirilmiş WCF kanalları.</span><span class="sxs-lookup"><span data-stu-id="96356-103">This sample demonstrates the usefulness of <xref:System.ServiceModel.Channels.ReceiveContext>-enabled WCF channels.</span></span> <span data-ttu-id="96356-104">Örnek Ürün NetMSMQ kanalı kullanılarak iki sayının bulmak için bir hizmet uygular.</span><span class="sxs-lookup"><span data-stu-id="96356-104">The sample implements a service to find the product of two numbers using a NetMSMQ channel.</span></span>  
  
 <span data-ttu-id="96356-105"><xref:System.ServiceModel.Channels.ReceiveContext> Sınıfı, iletinin erişmek veya iletinin içeriğini bile inceledikten sonra daha fazla işleme için sıradaki bırakın karar vermek bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="96356-105">The <xref:System.ServiceModel.Channels.ReceiveContext> class enables an application to decide whether to access the message or leave it in the queue for further processing, even after the contents of the message have been inspected.</span></span> <span data-ttu-id="96356-106">Bu örnekte, bir istemci rastgele tamsayı işlem bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="96356-106">In this sample, a client sends random integers to a transactional queue.</span></span> <span data-ttu-id="96356-107">`ProductCalculator` Hizmet iletileri alır ve ürün hesaplanan olup olmadığını belirlemek için tamsayılardır iletisi içeriği olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="96356-107">The `ProductCalculator` service receives the messages and inspects the message contents, which are integers, to determine whether the product can be computed.</span></span> <span data-ttu-id="96356-108">Hizmet işlemi ürün işlem değil, ileti yeniden kuyruğa alınan ve kuyrukta dinleme hizmeti tarafından tekrar alınabilir.</span><span class="sxs-lookup"><span data-stu-id="96356-108">If the service operation does not compute the product, the message is put back into the queue and can be received again by the service listening on the queue.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96356-109">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="96356-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="96356-110">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="96356-110">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96356-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="96356-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96356-112">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="96356-112">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="96356-113">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="96356-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="96356-114">Microsoft Message Queuing (MSMQ) yüklendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="96356-114">Ensure that Microsoft Message Queuing (MSMQ) is installed.</span></span>  
  
    1.  <span data-ttu-id="96356-115">MSMQ yüklemek için [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="96356-115">To install MSMQ on [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="96356-116">İçinde **Sunucu Yöneticisi'ni**, tıklayın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="96356-116">In **Server Manager**, click **Features**.</span></span>  
  
        2.  <span data-ttu-id="96356-117">Sağ bölmede **özellikler özeti**, tıklayın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="96356-117">In the right pane under **Features Summary**, click **Add Features**.</span></span>  
  
        3.  <span data-ttu-id="96356-118">Sonuçta elde edilen penceresinde **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="96356-118">In the resulting window, expand **Message Queuing**.</span></span>  
  
        4.  <span data-ttu-id="96356-119">Genişletin **Message Queuing Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="96356-119">Expand **Message Queuing Services**.</span></span>  
  
        5.  <span data-ttu-id="96356-120">Tıklayın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) ve ardından **HTTP desteği**.</span><span class="sxs-lookup"><span data-stu-id="96356-120">Click **Directory Services Integration** (for computers joined to a domain), and then click **HTTP Support**.</span></span>  
  
        6.  <span data-ttu-id="96356-121">Tıklayın **sonraki**ve ardından **yükleme**.</span><span class="sxs-lookup"><span data-stu-id="96356-121">Click **Next**, and then click **Install**.</span></span>  
  
    2.  <span data-ttu-id="96356-122">MSMQ yüklemek için [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="96356-122">To install MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)]:</span></span>  
  
        1.  <span data-ttu-id="96356-123">Açık **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="96356-123">Open **Control Panel**.</span></span>  
  
        2.  <span data-ttu-id="96356-124">Tıklayın **programlar** ve sonra **programlar ve Özellikler**, tıklayın **Windows özelliklerini açma ve kapatma**.</span><span class="sxs-lookup"><span data-stu-id="96356-124">Click **Programs** and then, under **Programs and Features**, click **Turn Windows Features on and off**.</span></span>  
  
        3.  <span data-ttu-id="96356-125">Genişletin **Microsoft Message Queue (MSMQ) sunucusu**, genişletme **Microsoft Message Queue (MSMQ) Server Core**ve sonra yüklemek aşağıdaki olan Message Queuing özellikler için onay kutularını seçin:</span><span class="sxs-lookup"><span data-stu-id="96356-125">Expand **Microsoft Message Queue (MSMQ) Server**, expand **Microsoft Message Queue (MSMQ) Server Core**, and then select the check boxes for the following Message Queuing features to install:</span></span>  
  
            -   <span data-ttu-id="96356-126">Message Queuing sunucusu</span><span class="sxs-lookup"><span data-stu-id="96356-126">Message Queuing Server</span></span>  
  
            -   <span data-ttu-id="96356-127">MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için)</span><span class="sxs-lookup"><span data-stu-id="96356-127">MSMQ Active Directory Domain Services Integration (for computers joined to a domain)</span></span>  
  
            -   <span data-ttu-id="96356-128">MSMQ HTTP desteği</span><span class="sxs-lookup"><span data-stu-id="96356-128">MSMQ HTTP Support</span></span>  
  
        4.  <span data-ttu-id="96356-129">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="96356-129">Click **OK**.</span></span>  
  
        5.  <span data-ttu-id="96356-130">Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.</span><span class="sxs-lookup"><span data-stu-id="96356-130">If you are prompted to restart the computer, click **OK** to complete the installation.</span></span>  
  
2.  <span data-ttu-id="96356-131">Emin [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bilgisayara yüklendi.</span><span class="sxs-lookup"><span data-stu-id="96356-131">Ensure that [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is installed on the computer.</span></span>  
  
3.  <span data-ttu-id="96356-132">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ReceiveContextProductGenerator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="96356-132">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ReceiveContextProductGenerator.sln solution file.</span></span>  
  
4.  <span data-ttu-id="96356-133">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="96356-133">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="96356-134">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="96356-134">To run the solution, press CTRL+F5.</span></span>
