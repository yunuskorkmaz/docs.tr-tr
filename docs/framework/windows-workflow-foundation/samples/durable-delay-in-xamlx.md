---
title: Xamlx'de dayanıklı gecikme
ms.date: 03/30/2017
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
ms.openlocfilehash: 1eef9211c67d190ecb5f329c481fa2e3d1763353
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521459"
---
# <a name="durable-delay-in-xamlx"></a><span data-ttu-id="06387-102">Xamlx'de dayanıklı gecikme</span><span class="sxs-lookup"><span data-stu-id="06387-102">Durable Delay in XAMLX</span></span>
<span data-ttu-id="06387-103">Bu örnek, iş akışı kalıcı bir cihaza gecikme sırasında devam eden bir gecikmenin bir dayanıklı gecikme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="06387-103">This sample demonstrates how to use a durable delay, which is a delay that persists the workflow to a durable device during the delay.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06387-104">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="06387-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06387-105">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="06387-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06387-106">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="06387-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06387-107">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="06387-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a><span data-ttu-id="06387-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="06387-108">Discussion</span></span>  
 <span data-ttu-id="06387-109">Örnek iş akışı tarafından bir gecikme ayrılmış iki ileti yerel bir dosyaya içerir.</span><span class="sxs-lookup"><span data-stu-id="06387-109">The sample workflow contains two messages to a local file that are separated by a delay.</span></span> <span data-ttu-id="06387-110">Gecikme tetiklendiğinde, iş akışı kaldırıldı ve bellekte yeniden yükleniyor önce 5 saniye içinde iş akışı örnek deposu bekler.</span><span class="sxs-lookup"><span data-stu-id="06387-110">When the delay is triggered, the workflow is unloaded and waits 5 seconds in the workflow instance store before being reloaded in memory.</span></span>  
  
 <span data-ttu-id="06387-111">Visual Studio'da barındırılan bir iş akışı hizmeti .xamlx dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="06387-111">The .xamlx file is a workflow service that is hosted in Visual Studio.</span></span> <span data-ttu-id="06387-112">Visual Studio iş akışı iş akışı hizmeti konağı için konak kullanan Cassini'ye kullanır.</span><span class="sxs-lookup"><span data-stu-id="06387-112">Visual Studio uses Cassini that uses a workflow service host to host the workflow.</span></span>  
  
 <span data-ttu-id="06387-113">İş akışı barındırma yanı sıra, iş akışı hizmeti konağı iş akışı örneği yükleniyor ve bunları kaldırma yönetir.</span><span class="sxs-lookup"><span data-stu-id="06387-113">In addition to hosting the workflow, the workflow service host manages the workflow instances by loading and unloading them.</span></span> <span data-ttu-id="06387-114">Windows Workflow Foundation (WF) tanımını (iş akışı hizmeti konağı) örneği başlatmak için bir ileti gönderen bir istemci ayarlama <xref:System.ServiceModel.Activities.Receive> iş akışı etkinlik.</span><span class="sxs-lookup"><span data-stu-id="06387-114">To start an instance of the Windows Workflow Foundation (WF) definition (on the workflow service host), set a client that sends a message to the <xref:System.ServiceModel.Activities.Receive> activity in the workflow.</span></span> <span data-ttu-id="06387-115">Bu <xref:System.ServiceModel.Activities.Receive> sahip kendi <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> özelliğini `true`, bir ileti aldıktan sonra iş akışının yeni bir örneğini oluşturmak için etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="06387-115">This <xref:System.ServiceModel.Activities.Receive> has its <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> property set to `true`, enabling it to create a new instance of the workflow once it receives a message.</span></span>  
  
 <span data-ttu-id="06387-116">Başlatma sırasında bir kaldırma örneği davranışı altında Kalıcılık mağazayı (veritabanı) örneğine kaldırın iş akışı hizmeti konağı için belirten yapılandırma dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="06387-116">During initialization, an unload instance behavior is added to the configuration file that specifies to the workflow service host under which it should unload an instance to the persistence store (database).</span></span> <span data-ttu-id="06387-117">Bu örnek için (gecikme tetiklendiğinde) iş akışı boş göründükten hemen sonra örneğini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="06387-117">For this sample, it unloads the instance immediately after the workflow goes idle (when the delay is triggered).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="06387-118">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="06387-118">To use this sample</span></span>  
  
1.  <span data-ttu-id="06387-119">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="06387-119">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="06387-120">DurableDelayXamlx\CS klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="06387-120">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="06387-121">Setup.cmd'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06387-121">Run Setup.cmd.</span></span>  
  
4.  <span data-ttu-id="06387-122">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici olarak.</span><span class="sxs-lookup"><span data-stu-id="06387-122">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an administrator.</span></span>  
  
5.  <span data-ttu-id="06387-123">DurableDelayXamlx.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="06387-123">Open the DurableDelayXamlx.sln solution file.</span></span>  
  
6.  <span data-ttu-id="06387-124">İçinde **Çözüm Gezgini**, çözümü sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="06387-124">In **Solution Explorer**, right-click the solution and select **Properties**.</span></span>  
  
7.  <span data-ttu-id="06387-125">Seçin **birden fazla başlangıç projesi** ve her iki proje kümesine **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="06387-125">Select **Multiple startup projects** and set both projects to **Start**.</span></span>  
  
8.  <span data-ttu-id="06387-126">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="06387-126">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
9. <span data-ttu-id="06387-127">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="06387-127">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-uninstall-this-sample"></a><span data-ttu-id="06387-128">Bu örnek kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="06387-128">To uninstall this sample</span></span>  
  
1.  <span data-ttu-id="06387-129">Açık bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="06387-129">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
2.  <span data-ttu-id="06387-130">DurableDelayXamlx\CS klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="06387-130">Navigate to the DurableDelayXamlx\CS folder.</span></span>  
  
3.  <span data-ttu-id="06387-131">CleanUp.cmd çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06387-131">Run Cleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06387-132">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="06387-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06387-133">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="06387-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06387-134">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="06387-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06387-135">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="06387-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
