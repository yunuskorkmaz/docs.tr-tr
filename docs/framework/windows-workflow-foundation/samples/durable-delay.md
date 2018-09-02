---
title: Dayanıklı gecikme
ms.date: 03/30/2017
ms.assetid: 220ec240-b958-430c-81ff-b734a6aa97ae
ms.openlocfilehash: 2a7692e28d60232913ae5d11a90025e59664c0e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406582"
---
# <a name="durable-delay"></a><span data-ttu-id="f1f8c-102">Dayanıklı gecikme</span><span class="sxs-lookup"><span data-stu-id="f1f8c-102">Durable Delay</span></span>
<span data-ttu-id="f1f8c-103">Bu örnek, iş akışı kalıcı bir cihaza gecikme sırasında devam eden bir gecikmenin bir dayanıklı gecikme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span> <span data-ttu-id="f1f8c-104">Örnek iş akışı tarafından bir gecikme ayrılmış iki ileti konsola içerir.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-104">The sample workflow contains two messages to the console that are separated by a delay.</span></span> <span data-ttu-id="f1f8c-105">Gecikme tetiklendiğinde, iş akışı kaldırıldı ve bellekte yeniden yükleniyor önce 5 saniye içinde iş akışı örnek deposu bekler.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-105">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
## <a name="workflow-details"></a><span data-ttu-id="f1f8c-106">İş akışı ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="f1f8c-106">Workflow Details</span></span>  
 <span data-ttu-id="f1f8c-107">İş akışı hizmeti konağı, iş akışını barındıran ve iş akışı örneği yükleme ve bunları kaldırma tarafından yönetir.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-107">The workflow service host hosts the workflow and manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="f1f8c-108">Örnek iş akışı tanımının örneği başlatmak için bir ileti gönderen bir proxy ayarlar <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-108">To start an instance of the workflow definition, the sample sets a proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="f1f8c-109"><xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> Özelliği `true`, bir ileti aldıktan sonra iş akışının yeni bir örneğini oluşturmak için etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-109">The <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property is set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="f1f8c-110">Aşağıdaki liste iş akışı hizmeti ana bilgisayarı tarafından Kurulum başlatma sırasında ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-110">The following list details the set-up by the workflow service host during initialization.</span></span>  
  
1.  <span data-ttu-id="f1f8c-111">Bir adresi bir hizmet konağı oluşturur (http://localhost:8080/Client).</span><span class="sxs-lookup"><span data-stu-id="f1f8c-111">Creates a service host with an address (http://localhost:8080/Client).</span></span>  
  
2.  <span data-ttu-id="f1f8c-112">Hizmet ana bilgisayarı ile iletişimi etkinleştirmek için bir uç nokta oluşturur <xref:System.ServiceModel.Activities.Receive> etkinliği iş akışı içinde.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-112">Creates an endpoint in the service host to enable communication with the <xref:System.ServiceModel.Activities.Receive> activity inside the workflow.</span></span>  
  
3.  <span data-ttu-id="f1f8c-113">Bir SQL örneği deposu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-113">Sets up a SQL instance store.</span></span>  
  
4.  <span data-ttu-id="f1f8c-114">SQL kalıcı depolama için bir iş akışı örneği iş akışı hizmeti konağı kaldırma koşulları belirten bir kaldırma örneği davranışı ekler.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-114">Adds an unload instance behavior that specifies the conditions under which the workflow service host should unload a workflow instance to the SQL persistence store.</span></span> <span data-ttu-id="f1f8c-115">Bu örnek için (gecikme tetiklendiğinde) iş akışı boş göründükten hemen sonra örneğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-115">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
5.  <span data-ttu-id="f1f8c-116">İleti gönderen bir proxy oluşturur <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-116">Creates the proxy that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f1f8c-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f1f8c-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="f1f8c-118">Kalıcılık veritabanı ayarlama.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-118">Set up the persistence database.</span></span>  
  
    1.  <span data-ttu-id="f1f8c-119">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="f1f8c-120">Gidin [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dizin (C:\Windows\Microsoft.NET\Framework\v4. X\\).</span><span class="sxs-lookup"><span data-stu-id="f1f8c-120">Navigate to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory (C:\Windows\Microsoft.NET\Framework\v4.X\\).</span></span>  
  
    3.  <span data-ttu-id="f1f8c-121">WorkflowManagementService.exe.config dosyasını düzenleyin ve içine aşağıdaki bağlantı dizesi Ekle <`database`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-121">Edit the WorkflowManagementService.exe.config file and add the following connection string inside the <`database`> element.</span></span>  
  
        ```xml  
        <database connectionString="Data Source=localhost\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True;Asynchronous Processing=True" />  
        ```  
  
    4.  <span data-ttu-id="f1f8c-122">DurableDelay\CS dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-122">Navigate to the DurableDelay\CS directory.</span></span>  
  
    5.  <span data-ttu-id="f1f8c-123">Setup.cmd'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-123">Run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="f1f8c-124">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] sağ tıklayarak yükseltilmiş izinler kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] simgesini seçip **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-124">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] using elevated permissions by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="f1f8c-125">Delay.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-125">Open the Delay.sln solution file.</span></span>  
  
4.  <span data-ttu-id="f1f8c-126">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="f1f8c-127">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-127">Press CTRL+F5 to run the solution.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="f1f8c-128">Bu örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="f1f8c-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="f1f8c-129">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="f1f8c-130">DurableDelay\CS dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-130">Navigate to the DurableDelay\CS directory.</span></span>  
  
3.  <span data-ttu-id="f1f8c-131">CleanUp.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1f8c-132">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1f8c-133">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1f8c-134">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1f8c-135">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f1f8c-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelay`