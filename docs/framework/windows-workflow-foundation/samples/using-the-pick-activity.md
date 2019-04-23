---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 0b2fbeb9b32406dd913d7e1ee87ac167113d0f28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302991"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="589c4-102">Pick Etkinliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="589c4-102">Using the Pick Activity</span></span>
<span data-ttu-id="589c4-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="589c4-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="589c4-104"><xref:System.Activities.Statements.Pick> Etkinlik, olay tabanlı denetim modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="589c4-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="589c4-105">Benzer şekilde C# davranışını `switch` dalları yalnızca biri yürüten deyimi `switch` deyimi.</span><span class="sxs-lookup"><span data-stu-id="589c4-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="589c4-106">Farklı `switch` deyimi bir dal yürütüldüğünde bir değere dayalı <xref:System.Activities.Statements.Pick> nasıl bir etkinlik tamamlandıktan sonra bağlı olarak bir dalı etkinliği yürütür.</span><span class="sxs-lookup"><span data-stu-id="589c4-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="589c4-107">Bu örnek, bir kullanıcının belirli bir süre içinde konsolda kişinin adını yazın ister.</span><span class="sxs-lookup"><span data-stu-id="589c4-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="589c4-108"><xref:System.Activities.Statements.Pick> Örnek etkinlik tabanlı olup kullanıcı adında 5 saniye içinde veya türleri üzerinde yürütülen iki dal vardır.</span><span class="sxs-lookup"><span data-stu-id="589c4-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="589c4-109">Kullanıcı 5 saniye içinde adında yazarsa, ilk dalı, bir özel içeren yürütülür `ReadLine` etkinlik; Aksi durumda diğer dal, içeren yürütülen bir <xref:System.Activities.Statements.Delay> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="589c4-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="589c4-110">Bir kullanıcının adını konsolda yazılmış sonra kullanıcının adını konsolda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="589c4-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="589c4-111">Giriş 5 saniye içinde girilmezse, işlemi zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="589c4-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="589c4-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="589c4-112">Demonstrates</span></span>
 <span data-ttu-id="589c4-113"><xref:System.Activities.Statements.Pick> Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="589c4-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="589c4-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="589c4-114">Discussion</span></span>
 <span data-ttu-id="589c4-115">Bir tasarımcı iş akışı ve kodlanmış iş akışı örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="589c4-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="589c4-116">Örnek İş Akışı Tasarımcısı sürümü Tasarımcı bir iş akışı Tasarımcısı'nda oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="589c4-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="589c4-117">Aşağıdaki dosyalar dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="589c4-117">The following files are included:</span></span>

-   <span data-ttu-id="589c4-118">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="589c4-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="589c4-119">ReadString.cs: Konsolundan bazı giriş okur özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="589c4-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

-   <span data-ttu-id="589c4-120">Sequence1.XAML: Kullanan çekme Tasarımcı kullanılarak oluşturulmuş bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="589c4-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="589c4-121">Bir iş akışı Tasarımcısı'nda oluşturma kodlanmış iş akışı örneği kodlanmış sürümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="589c4-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="589c4-122">Aşağıdaki dosyalar dahil edilir:</span><span class="sxs-lookup"><span data-stu-id="589c4-122">The following files are included:</span></span>

-   <span data-ttu-id="589c4-123">Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.</span><span class="sxs-lookup"><span data-stu-id="589c4-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

-   <span data-ttu-id="589c4-124">ReadString.cs: Konsolundan bazı giriş okur özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="589c4-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="589c4-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="589c4-125">To use this sample</span></span>

1. <span data-ttu-id="589c4-126">Visual Studio 2010 kullanarak Pick.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="589c4-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="589c4-127">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="589c4-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="589c4-128">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="589c4-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="589c4-129">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="589c4-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="589c4-130">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="589c4-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="589c4-131">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="589c4-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="589c4-132">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="589c4-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`