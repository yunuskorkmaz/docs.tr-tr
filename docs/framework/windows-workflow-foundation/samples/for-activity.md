---
title: Etkinlik için
ms.date: 03/30/2017
ms.assetid: 2ea751b4-36f0-48aa-a115-70a2ab89f6d8
ms.openlocfilehash: 7a7023abb9057ab4b25552fbf9a81cd2ae2b4e88
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881530"
---
# <a name="for-activity"></a><span data-ttu-id="e30bf-102">Etkinlik için</span><span class="sxs-lookup"><span data-stu-id="e30bf-102">For Activity</span></span>
<span data-ttu-id="e30bf-103">Devralınan özel etkinlik oluşturma için örnek gösterir <xref:System.Activities.NativeActivity>ve bir iş akışında bir gerçek dünya örneği çalıştırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e30bf-103">The For sample demonstrates how to build a custom activity that inherits from <xref:System.Activities.NativeActivity>, and use it in a workflow to execute a real world example.</span></span> <span data-ttu-id="e30bf-104">Bu örnek işlevleri gibi C# içindeki özel etkinlik `for` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e30bf-104">The custom activity included in this sample functions like the C# `for` statement.</span></span> <span data-ttu-id="e30bf-105">T</span><span class="sxs-lookup"><span data-stu-id="e30bf-105">T</span></span>  
  
 <span data-ttu-id="e30bf-106">`For` Özel etkinlik adında özelliklere sahip `InitAction`, `IterationAction`, `Condition`, ve `Body` başlatma ifadesi, yinelemeli deyimi, devamlılık koşul karşılık gelir ve sırasıyla deyimi gövdesi Standart C# içinde bulunan `For` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e30bf-106">The `For` custom activity has properties named `InitAction`, `IterationAction`, `Condition`, and `Body` that correspond to the initialization statement, iterative statement, continuation condition, and body statement respectively found in the standard C# `For` statement.</span></span>  
  
 <span data-ttu-id="e30bf-107">Aşağıdaki tabloda, örnekteki anahtar dosyalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e30bf-107">The following table describes the key files in the sample.</span></span>  
  
|<span data-ttu-id="e30bf-108">Dosya</span><span class="sxs-lookup"><span data-stu-id="e30bf-108">File</span></span>|<span data-ttu-id="e30bf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30bf-109">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="e30bf-110">For.cs</span><span class="sxs-lookup"><span data-stu-id="e30bf-110">For.cs</span></span>|<span data-ttu-id="e30bf-111">Sınıf tanımı `For` genişletir özel etkinlik <xref:System.Activities.NativeActivity> C# işlevlerini sağlar sınıfını `For` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e30bf-111">Class definition for the `For` custom activity, which extends the <xref:System.Activities.NativeActivity> class to provide the functionality of the C# `For` statement.</span></span>|  
|<span data-ttu-id="e30bf-112">Program.cs</span><span class="sxs-lookup"><span data-stu-id="e30bf-112">Program.cs</span></span>|<span data-ttu-id="e30bf-113">Özel kullanarak bir koleksiyon üzerinde temel yineleme işini gerçekleştiren bir istemci uygulaması `For` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e30bf-113">A client application that performs basic iterative work on a collection using the custom `For` activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e30bf-114">Kullanırken `For` özel etkinlik emin `Condition` özelliği; Aksi takdirde sonsuz bir döngüye oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="e30bf-114">When using the `For` custom activity, ensure that the `Condition` property is set; otherwise an infinite loop could occur.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e30bf-115">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e30bf-115">Demonstrates</span></span>  
 <span data-ttu-id="e30bf-116">Devralınan özel etkinlik oluşturma <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="e30bf-116">Create a custom activity that inherits from <xref:System.Activities.NativeActivity>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e30bf-117">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e30bf-117">Discussion</span></span>  
 <span data-ttu-id="e30bf-118">Aşağıdaki tabloda, bu örnekte bulunan etkinlik özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e30bf-118">The following table describes the properties of the activity included in this sample.</span></span>  
  
 <span data-ttu-id="e30bf-119">InitAction</span><span class="sxs-lookup"><span data-stu-id="e30bf-119">InitAction</span></span>  
 <span data-ttu-id="e30bf-120">Başlatma ifadesi</span><span class="sxs-lookup"><span data-stu-id="e30bf-120">Initialization statement</span></span>  
  
 <span data-ttu-id="e30bf-121">IterationAction</span><span class="sxs-lookup"><span data-stu-id="e30bf-121">IterationAction</span></span>  
 <span data-ttu-id="e30bf-122">Yinelemeli deyimi</span><span class="sxs-lookup"><span data-stu-id="e30bf-122">Iterative statement</span></span>  
  
 <span data-ttu-id="e30bf-123">Koşul</span><span class="sxs-lookup"><span data-stu-id="e30bf-123">Condition</span></span>  
 <span data-ttu-id="e30bf-124">Devamlılık deyimi</span><span class="sxs-lookup"><span data-stu-id="e30bf-124">Continuation statement</span></span>  
  
 <span data-ttu-id="e30bf-125">Gövde</span><span class="sxs-lookup"><span data-stu-id="e30bf-125">Body</span></span>  
 <span data-ttu-id="e30bf-126">Gövde ifadesi</span><span class="sxs-lookup"><span data-stu-id="e30bf-126">Body statement</span></span>  
  
 <span data-ttu-id="e30bf-127">Etkinlik öğesinden devralınan <xref:System.Activities.NativeActivity> birini kullanarak çalıştırmak için ek etkinlikler zamanlamak gibi çalışma zamanı özelliklere erişim kazanmak için `ScheduleActivity` yöntemlerinin <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="e30bf-127">The activity inherits from <xref:System.Activities.NativeActivity> to gain access to runtime features such as scheduling additional activities to run, using one of the `ScheduleActivity` methods of <xref:System.Activities.NativeActivityContext>.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e30bf-128">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e30bf-128">To use this sample</span></span>  
  
1.  <span data-ttu-id="e30bf-129">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], For.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e30bf-129">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the For.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e30bf-130">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e30bf-130">Build the solution, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e30bf-131">F5 tuşuna basarak çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e30bf-131">Run the solution, by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e30bf-132">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="e30bf-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e30bf-133">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e30bf-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e30bf-134">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e30bf-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e30bf-135">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e30bf-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\For`