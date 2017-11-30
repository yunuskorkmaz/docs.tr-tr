---
title: "Durum makinesi Akış Çizelgesi ve çekme birleşimini kullanarak senaryosu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a4ff644367f0bcd6562bd8931406a11f39d62df
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="0f8ca-102">Durum makinesi Akış Çizelgesi ve çekme birleşimini kullanarak senaryosu</span><span class="sxs-lookup"><span data-stu-id="0f8ca-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="0f8ca-103">Bu örnek, bir birleşimini kullanarak basit kronometre senaryoları uygulayacak gösterilmiştir <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="0f8ca-104">Alma ve gönderme içinde çekme etkinlik kronometre olaylarını dinleyecek şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f8ca-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f8ca-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f8ca-107">Bu dizin mevcut değilse (indirme) gidin tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f8ca-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="0f8ca-109">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0f8ca-109">Sample Details</span></span>  
 <span data-ttu-id="0f8ca-110">Aşağıdaki tabloda, bu örnek projelerinde listeler.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="0f8ca-111">Proje adı</span><span class="sxs-lookup"><span data-stu-id="0f8ca-111">Project Name</span></span>|<span data-ttu-id="0f8ca-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f8ca-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="0f8ca-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="0f8ca-113">StopWatchService</span></span>|<span data-ttu-id="0f8ca-114">Bu proje bir birleşimini kullanarak kronometre örneği için durum makinesinin uyarlamasını içeren <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="0f8ca-115"><xref:System.Activities.Statements.Pick> Etkinlik sahip 3 <xref:System.Activities.Statements.PickBranch> deyimleri içinde <xref:System.Activities.Statements.Pick.Branches%2A> dinlemek özelliği `GetStart`, `GetStop` ve `GetOff` olaylar.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="0f8ca-116">Dalları biri için Tetikleyiciler gelen olaya bağlı olarak, etkinleştirme ve karşılık gelen <xref:System.Activities.Statements.PickBranch.Action%2A> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="0f8ca-117">İçinde <xref:System.Activities.Statements.PickBranch.Action%2A> özelliği var. bir <xref:System.Activities.Statements.Switch%601> geçişi yasal geçiş olup olmadığını ve bu doğruysa değerlendirir deyimi `currentState` özelliği geçirme durumuna güncelleştirildi ve istemciye gönderilen.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="0f8ca-118"><xref:System.Activities.Statements.FlowDecision> Sonunda etkinlik <xref:System.Activities.Statements.Flowchart> değerlendirir `currentState` durumu terminal olup olmadığını belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="0f8ca-119">Bu durumda, iş akışı sona erer; Aksi takdirde, döngüler başlangıcını dön kontrol <xref:System.Activities.Statements.Pick> etkinliği iş akışı için daha fazla kronometre olayları burada bekler.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="0f8ca-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="0f8ca-120">StopWatchClient</span></span>|<span data-ttu-id="0f8ca-121">Bu basit çeşitli kronometre olaylarla etkinlik birleşimleri gönderip gönderen bir basit sıralı iş akışı konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0f8ca-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0f8ca-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="0f8ca-123">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], açık StateMachineWithPick.sln çözüm dosyası.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="0f8ca-124">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="0f8ca-125">Gelen StopWatchService.exe Başlat [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] .exe dosyasına sağ tıklatarak ve seçerek yönetici olarak **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="0f8ca-126">StateMachineWithPick\CS\StopWatchService\bin\Debug klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="0f8ca-127">StopWatchService.exe dosyasını sağ tıklatın ve seçin **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="0f8ca-128">StopWatchClient istemci uygulaması içinden Başlat [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0f8ca-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="0f8ca-129">İçinde **Çözüm Gezgini**seçin **StopWatchClient** sağ tıklayın ve proje **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="0f8ca-130">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="0f8ca-131">İçin durumu geçişleri görüntülemek StopWatchService.exe konsol penceresine dönün.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f8ca-132">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f8ca-133">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f8ca-134">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f8ca-135">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0f8ca-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`