---
title: Flowchart ve Pick birleşimini kullanarak senaryosu
ms.date: 03/30/2017
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
ms.openlocfilehash: b0f8e884a8a6c62c4e7edaf5cc9727bf7bfe8603
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195692"
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="114de-102">Flowchart ve Pick birleşimini kullanarak senaryosu</span><span class="sxs-lookup"><span data-stu-id="114de-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="114de-103">Bu örnek bir birleşimini kullanarak bir kronometre basit senaryonun nasıl uygulanacağını gösterir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="114de-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="114de-104">Alma ve gönderme Pick etkinliği içinde kronometre olaylarını dinleyecek şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="114de-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="114de-105">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="114de-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="114de-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="114de-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="114de-107">Bu dizin mevcut değilse (indirme sayfası) Git tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="114de-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="114de-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="114de-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="114de-109">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="114de-109">Sample Details</span></span>  
 <span data-ttu-id="114de-110">Aşağıdaki tabloda, bu örnekte projeleri listeler.</span><span class="sxs-lookup"><span data-stu-id="114de-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="114de-111">Proje adı</span><span class="sxs-lookup"><span data-stu-id="114de-111">Project Name</span></span>|<span data-ttu-id="114de-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="114de-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="114de-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="114de-113">StopWatchService</span></span>|<span data-ttu-id="114de-114">Bu proje bir durum makinesindeki bir birleşimi kullanılarak kronometre örnek uygulamasını içerir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="114de-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="114de-115"><xref:System.Activities.Statements.Pick> Etkinliğinde 3 <xref:System.Activities.Statements.PickBranch> deyimleri içinde <xref:System.Activities.Statements.Pick.Branches%2A> dinler özelliği `GetStart`, `GetStop` ve `GetOff` olayları.</span><span class="sxs-lookup"><span data-stu-id="114de-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="114de-116">Gelen olay tabanlı, dalları biri için Tetikleyiciler etkinleştirmek ve karşılık gelen <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="114de-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="114de-117">İçinde <xref:System.Activities.Statements.PickBranch.Action%2A> özelliği var. bir <xref:System.Activities.Statements.Switch%601> geçiş yasal geçiş olup olmadığını ve eğer ise, değerlendirilen ifade `currentState` özelliği için geçiş durumu güncelleştirildi ve istemciye gönderilen.</span><span class="sxs-lookup"><span data-stu-id="114de-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="114de-118"><xref:System.Activities.Statements.FlowDecision> Etkinlik sonunda <xref:System.Activities.Statements.Flowchart> değerlendirir `currentState` durumu terminal olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="114de-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="114de-119">İse, iş akışı sona erer; Aksi takdirde, döngüler tekrar başlangıcını denetim <xref:System.Activities.Statements.Pick> burada iş akışını bekler daha fazla kronometre etkinlik için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="114de-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="114de-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="114de-120">StopWatchClient</span></span>|<span data-ttu-id="114de-121">Bu basit çeşitli kronometre olaylarla etkinlik birleşimleri gönderip gönderen bir basit sıralı iş akışı konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="114de-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="114de-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="114de-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="114de-123">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]açın StateMachineWithPick.sln çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="114de-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="114de-124">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="114de-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="114de-125">Gelen StopWatchService.exe Başlat [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] .exe dosyasına sağ tıklayarak ve seçerek bir yönetici olarak **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="114de-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="114de-126">StateMachineWithPick\CS\StopWatchService\bin\Debug klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="114de-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="114de-127">StopWatchService.exe dosyaya sağ tıklayıp **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="114de-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="114de-128">StopWatchClient istemci uygulamasının içinden başlatın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="114de-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="114de-129">İçinde **Çözüm Gezgini**seçin **StopWatchClient** sağ tıklayın ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="114de-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="114de-130">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="114de-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="114de-131">Durumu geçişleri görüntülemek StopWatchService.exe için konsol penceresine dönün.</span><span class="sxs-lookup"><span data-stu-id="114de-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="114de-132">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="114de-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="114de-133">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="114de-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="114de-134">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="114de-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="114de-135">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="114de-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`