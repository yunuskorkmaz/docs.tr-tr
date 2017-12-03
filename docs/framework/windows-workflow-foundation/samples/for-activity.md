---
title: "Etkinlik için"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3b97e4bcd8dd60aa2768a8346d120bdebdb55ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="for-activity"></a><span data-ttu-id="c3dfd-102">Etkinlik için</span><span class="sxs-lookup"><span data-stu-id="c3dfd-102">For Activity</span></span>
<span data-ttu-id="c3dfd-103">İçin örnek devralan bir özel etkinlik oluşturmak nasıl gösterir <xref:System.Activities.NativeActivity>ve gerçek dünya örneği yürütmek için bir iş akışında kullanın.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="c3dfd-104">C# gibi bu örnek işlevleri dahil özel etkinlik `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="c3dfd-105">T</span><span class="sxs-lookup"><span data-stu-id="c3dfd-105">T</span></span>  
  
 <span data-ttu-id="c3dfd-106">`For` Özel etkinlik adında özelliklere sahip `InitAction`, `IterationAction`, `Condition`, ve `Body` başlatma deyimi, yinelemeli deyimi, devamlılık koşul karşılık gelir ve deyimi sırasıyla gövde Standart C# içinde bulunan `For` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="c3dfd-107">Aşağıdaki tabloda örnek anahtar dosyaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="c3dfd-108">Dosya</span><span class="sxs-lookup"><span data-stu-id="c3dfd-108">File</span></span>|<span data-ttu-id="c3dfd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3dfd-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c3dfd-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="c3dfd-110">For.cs</span></span>|<span data-ttu-id="c3dfd-111">Sınıf tanımı `For` genişletir özel etkinlik <xref:System.Activities.NativeActivity> C# işlevselliğini sağlamak için sınıf `For` deyimi.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="c3dfd-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="c3dfd-112">Program.cs</span></span>|<span data-ttu-id="c3dfd-113">Özel kullanarak bir koleksiyon temel yinelemeli çalışmayı gerçekleştiren bir istemci uygulaması `For` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c3dfd-114">Kullanırken `For` özel etkinlik emin `Condition` özelliği ayarlanmış; Aksi takdirde sonsuz bir döngüde oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c3dfd-115">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="c3dfd-115">Demonstrates</span></span>  
 <span data-ttu-id="c3dfd-116">Devralan bir özel etkinlik oluşturmak <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c3dfd-117">Tartışma</span><span class="sxs-lookup"><span data-stu-id="c3dfd-117">Discussion</span></span>  
 <span data-ttu-id="c3dfd-118">Aşağıdaki tabloda bu örnekte dahil etkinlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="c3dfd-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="c3dfd-119">InitAction</span></span>  
 <span data-ttu-id="c3dfd-120">Başlatma deyimi</span><span class="sxs-lookup"><span data-stu-id="c3dfd-120">Initialization statement</span></span>  
  
 <span data-ttu-id="c3dfd-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="c3dfd-121">IterationAction</span></span>  
 <span data-ttu-id="c3dfd-122">Yinelemeli deyimi</span><span class="sxs-lookup"><span data-stu-id="c3dfd-122">Iterative statement</span></span>  
  
 <span data-ttu-id="c3dfd-123">Koşul</span><span class="sxs-lookup"><span data-stu-id="c3dfd-123">Condition</span></span>  
 <span data-ttu-id="c3dfd-124">Devamlılık deyimi</span><span class="sxs-lookup"><span data-stu-id="c3dfd-124">Continuation statement</span></span>  
  
 <span data-ttu-id="c3dfd-125">Gövde</span><span class="sxs-lookup"><span data-stu-id="c3dfd-125">Body</span></span>  
 <span data-ttu-id="c3dfd-126">Gövde deyimi</span><span class="sxs-lookup"><span data-stu-id="c3dfd-126">Body statement</span></span>  
  
 <span data-ttu-id="c3dfd-127">Etkinlik devraldığı <xref:System.Activities.NativeActivity> çalıştırmak için ek etkinlikler zamanlama gibi çalışma zamanı özellikleri birini kullanarak erişmek için `ScheduleActivity` yöntemlerini <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c3dfd-128">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="c3dfd-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="c3dfd-129">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], For.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="c3dfd-130">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="c3dfd-131">F5 tuşuna basarak çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3dfd-132">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3dfd-133">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3dfd-134">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3dfd-135">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c3dfd-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`