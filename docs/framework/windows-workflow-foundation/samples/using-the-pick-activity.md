---
title: "Çekme etkinliğini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5a95567afd955848b81bc343109acfe3fd138c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="b4be7-102">Çekme etkinliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="b4be7-102">Using the Pick Activity</span></span>
<span data-ttu-id="b4be7-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b4be7-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="b4be7-104"><xref:System.Activities.Statements.Pick> Etkinlik olay tabanlı denetim modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4be7-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="b4be7-105">C# benzer şekilde davranır `switch` dallarda yalnızca biri yürütür deyimi `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b4be7-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="b4be7-106">Farklı `switch` bir dal yürütüldüğünde deyimi dayalı olarak bir değer üzerinde <xref:System.Activities.Statements.Pick> etkinlik nasıl bir etkinlik tamamlandıktan sonra dayalı bir dal yürütür.</span><span class="sxs-lookup"><span data-stu-id="b4be7-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="b4be7-107">Bu örnek adlarının konsolunda belirli bir süre içinde yazmak için bir kullanıcıya sorar.</span><span class="sxs-lookup"><span data-stu-id="b4be7-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="b4be7-108"><xref:System.Activities.Statements.Pick> Örnek etkinlik sahip olup olmadığını kullanıcı adında 5 saniye içinde veya türleri üzerinde temel yürütülen iki dalı.</span><span class="sxs-lookup"><span data-stu-id="b4be7-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="b4be7-109">Kullanıcı adında 5 saniye içinde yazdığında ilk dal, özel bir içeren yürütülür `ReadLine` etkinlik; Aksi takdirde diğer dal, içeren yürütülür bir <xref:System.Activities.Statements.Delay> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b4be7-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="b4be7-110">Bir kullanıcının adını konsolda yazılmış sonra kullanıcı adını konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="b4be7-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="b4be7-111">Giriş 5 saniye içinde girilmezse, işlemi zaman aşımına.</span><span class="sxs-lookup"><span data-stu-id="b4be7-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b4be7-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="b4be7-112">Demonstrates</span></span>  
 <span data-ttu-id="b4be7-113"><xref:System.Activities.Statements.Pick>Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b4be7-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b4be7-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b4be7-114">Discussion</span></span>  
 <span data-ttu-id="b4be7-115">Örnek İş Akışı Tasarımcısı ve kodlanmış iş akışı içerir.</span><span class="sxs-lookup"><span data-stu-id="b4be7-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="b4be7-116">İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="b4be7-116">Designer Workflow</span></span>  
 <span data-ttu-id="b4be7-117">Örnek Tasarımcısı sürümü, bir iş akışı Tasarımcısı'nda oluşturma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4be7-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="b4be7-118">Aşağıdaki dosyalar eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="b4be7-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="b4be7-119">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="b4be7-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="b4be7-120">ReadString.cs: bazı giriş konsoldan okuyan bir özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b4be7-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="b4be7-121">Sequence1.XAML: kullanır çekme Tasarımcı kullanarak bir iş akışı oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="b4be7-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="b4be7-122">Kodlanmış iş akışı</span><span class="sxs-lookup"><span data-stu-id="b4be7-122">Coded Workflow</span></span>  
 <span data-ttu-id="b4be7-123">Örnek kodlanmış sürümü, bir iş akışı Tasarımcısı'nda oluşturma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b4be7-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="b4be7-124">Aşağıdaki dosyalar eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="b4be7-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="b4be7-125">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="b4be7-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="b4be7-126">ReadString.cs: bazı giriş konsoldan okuyan bir özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b4be7-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b4be7-127">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b4be7-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="b4be7-128">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Pick.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b4be7-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b4be7-129">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b4be7-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b4be7-130">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b4be7-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4be7-131">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4be7-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b4be7-132">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b4be7-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b4be7-133">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b4be7-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4be7-134">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4be7-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`  
  
## <a name="see-also"></a><span data-ttu-id="b4be7-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4be7-135">See Also</span></span>
