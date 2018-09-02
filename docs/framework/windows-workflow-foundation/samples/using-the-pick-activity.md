---
title: Pick etkinliği kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 193b60bff7b08c0de9a0957668483eb73be97274
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452612"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="6c9f5-102">Pick etkinliği kullanma</span><span class="sxs-lookup"><span data-stu-id="6c9f5-102">Using the Pick Activity</span></span>
<span data-ttu-id="6c9f5-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="6c9f5-104"><xref:System.Activities.Statements.Pick> Etkinlik, olay tabanlı denetim modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="6c9f5-105">Benzer şekilde C# davranışını `switch` dalları yalnızca biri yürüten deyimi `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="6c9f5-106">Farklı `switch` deyimi bir dal yürütüldüğünde bir değere dayalı <xref:System.Activities.Statements.Pick> nasıl bir etkinlik tamamlandıktan sonra bağlı olarak bir dalı etkinliği yürütür.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="6c9f5-107">Bu örnek, bir kullanıcının belirli bir süre içinde konsolda kişinin adını yazın ister.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="6c9f5-108"><xref:System.Activities.Statements.Pick> Örnek etkinlik tabanlı olup kullanıcı adında 5 saniye içinde veya türleri üzerinde yürütülen iki dal vardır.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="6c9f5-109">Kullanıcı 5 saniye içinde adında yazarsa, ilk dalı, bir özel içeren yürütülür `ReadLine` etkinlik; Aksi durumda diğer dal, içeren yürütülen bir <xref:System.Activities.Statements.Delay> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="6c9f5-110">Bir kullanıcının adını konsolda yazılmış sonra kullanıcının adını konsolda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="6c9f5-111">Giriş 5 saniye içinde girilmezse, işlemi zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="6c9f5-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="6c9f5-112">Demonstrates</span></span>  
 <span data-ttu-id="6c9f5-113"><xref:System.Activities.Statements.Pick> Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="6c9f5-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="6c9f5-114">Discussion</span></span>  
 <span data-ttu-id="6c9f5-115">Bir tasarımcı iş akışı ve kodlanmış iş akışı örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="6c9f5-116">Tasarımcı iş akışı</span><span class="sxs-lookup"><span data-stu-id="6c9f5-116">Designer Workflow</span></span>  
 <span data-ttu-id="6c9f5-117">Bir iş akışı Tasarımcısı'nda oluşturma Tasarımcısı sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="6c9f5-118">Aşağıdaki dosyalar dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="6c9f5-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="6c9f5-119">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="6c9f5-120">ReadString.cs: bazı giriş konsoldan okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="6c9f5-121">Sequence1.XAML: kullandığı çekme Tasarımcı kullanılarak oluşturulmuş bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="6c9f5-122">Kodlanmış bir iş akışı</span><span class="sxs-lookup"><span data-stu-id="6c9f5-122">Coded Workflow</span></span>  
 <span data-ttu-id="6c9f5-123">Bir iş akışı Tasarımcısı'nda oluşturma kodlanmış sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="6c9f5-124">Aşağıdaki dosyalar dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="6c9f5-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="6c9f5-125">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="6c9f5-126">ReadString.cs: bazı giriş konsoldan okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6c9f5-127">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6c9f5-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="6c9f5-128">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Pick.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6c9f5-129">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6c9f5-130">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6c9f5-131">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c9f5-132">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6c9f5-133">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c9f5-134">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6c9f5-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`