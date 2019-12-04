---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: b0997254615ca962fd386dea70c67a8edb36c90a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715523"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="5245c-102">Pick Etkinliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="5245c-102">Using the Pick Activity</span></span>
<span data-ttu-id="5245c-103">Bu örnek, <xref:System.Activities.Statements.Pick> etkinliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5245c-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="5245c-104"><xref:System.Activities.Statements.Pick> etkinliği olay tabanlı denetim modellemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5245c-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="5245c-105">`switch` deyimindeki dallardan yalnızca C# birini yürüten `switch` bildirimine benzer şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="5245c-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="5245c-106">Bir dalın bir değere göre yürütüldüğü `switch` deyimin aksine, <xref:System.Activities.Statements.Pick> etkinliği bir etkinliğin nasıl tamamlantığını temel alarak bir dalı yürütür.</span><span class="sxs-lookup"><span data-stu-id="5245c-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="5245c-107">Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister.</span><span class="sxs-lookup"><span data-stu-id="5245c-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="5245c-108">Örnekteki <xref:System.Activities.Statements.Pick> etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır.</span><span class="sxs-lookup"><span data-stu-id="5245c-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="5245c-109">Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel bir `ReadLine` etkinliği içerir; Aksi takdirde, <xref:System.Activities.Statements.Delay> bir etkinlik içeren diğer dal yürütülür.</span><span class="sxs-lookup"><span data-stu-id="5245c-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="5245c-110">Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="5245c-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="5245c-111">Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="5245c-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="5245c-112">Gösterir</span><span class="sxs-lookup"><span data-stu-id="5245c-112">Demonstrates</span></span>
 <span data-ttu-id="5245c-113"><xref:System.Activities.Statements.Pick> etkinliği.</span><span class="sxs-lookup"><span data-stu-id="5245c-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="5245c-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="5245c-114">Discussion</span></span>
 <span data-ttu-id="5245c-115">Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.</span><span class="sxs-lookup"><span data-stu-id="5245c-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="5245c-116">Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5245c-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="5245c-117">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5245c-117">The following files are included:</span></span>

- <span data-ttu-id="5245c-118">Program.cs: örnek iş akışını yürüten `Main` işlevini Içerir.</span><span class="sxs-lookup"><span data-stu-id="5245c-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="5245c-119">ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5245c-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="5245c-120">Sequence1. xaml: seçimi kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="5245c-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="5245c-121">Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5245c-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="5245c-122">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5245c-122">The following files are included:</span></span>

- <span data-ttu-id="5245c-123">Program.cs: örnek iş akışını yürüten `Main` işlevini Içerir.</span><span class="sxs-lookup"><span data-stu-id="5245c-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="5245c-124">ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5245c-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="5245c-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5245c-125">To use this sample</span></span>

1. <span data-ttu-id="5245c-126">Visual Studio 2010 kullanarak, pick. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5245c-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="5245c-127">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="5245c-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="5245c-128">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="5245c-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5245c-129">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5245c-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5245c-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5245c-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="5245c-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="5245c-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5245c-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5245c-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
