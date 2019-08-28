---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 03b9ff7f552ad0cdcfbe9c46121a2f46f35de52a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037875"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="86e25-102">Pick Etkinliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="86e25-102">Using the Pick Activity</span></span>
<span data-ttu-id="86e25-103">Bu örnek, <xref:System.Activities.Statements.Pick> etkinliğin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86e25-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="86e25-104">Etkinlik <xref:System.Activities.Statements.Pick> , olay tabanlı denetim modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="86e25-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="86e25-105">C# `switch` Deyimdeki`switch` dallardan yalnızca birini yürüten deyimle benzer şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="86e25-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="86e25-106">Bir dalın bir değere göre yürütüldüğü <xref:System.Activities.Statements.Pick> deyiminaksine,etkinlikbiretkinliğinnasıltamamlantığınıtemelalarakbirdalıyürütür.`switch`</span><span class="sxs-lookup"><span data-stu-id="86e25-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="86e25-107">Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister.</span><span class="sxs-lookup"><span data-stu-id="86e25-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="86e25-108">Örnekteki <xref:System.Activities.Statements.Pick> etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır.</span><span class="sxs-lookup"><span data-stu-id="86e25-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="86e25-109">Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel `ReadLine` bir etkinlik içerir; Aksi takdirde, bir <xref:System.Activities.Statements.Delay> etkinlik içeren diğer dal yürütülür.</span><span class="sxs-lookup"><span data-stu-id="86e25-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="86e25-110">Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="86e25-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="86e25-111">Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="86e25-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="86e25-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="86e25-112">Demonstrates</span></span>
 <span data-ttu-id="86e25-113"><xref:System.Activities.Statements.Pick>etkinlik.</span><span class="sxs-lookup"><span data-stu-id="86e25-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="86e25-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="86e25-114">Discussion</span></span>
 <span data-ttu-id="86e25-115">Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.</span><span class="sxs-lookup"><span data-stu-id="86e25-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="86e25-116">Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86e25-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="86e25-117">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="86e25-117">The following files are included:</span></span>

- <span data-ttu-id="86e25-118">Program.cs: Örnek iş akışını yürüten işleviiçerir.`Main`</span><span class="sxs-lookup"><span data-stu-id="86e25-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="86e25-119">ReadString.cs: Konsolundan bir girişi okuyan özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="86e25-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="86e25-120">Sequence1. xaml: Seçme kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="86e25-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="86e25-121">Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="86e25-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="86e25-122">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="86e25-122">The following files are included:</span></span>

- <span data-ttu-id="86e25-123">Program.cs: Örnek iş akışını yürüten işleviiçerir.`Main`</span><span class="sxs-lookup"><span data-stu-id="86e25-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="86e25-124">ReadString.cs: Konsolundan bir girişi okuyan özel etkinlik.</span><span class="sxs-lookup"><span data-stu-id="86e25-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="86e25-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="86e25-125">To use this sample</span></span>

1. <span data-ttu-id="86e25-126">Visual Studio 2010 kullanarak, pick. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="86e25-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="86e25-127">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="86e25-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="86e25-128">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="86e25-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86e25-129">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="86e25-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="86e25-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="86e25-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="86e25-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="86e25-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="86e25-132">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="86e25-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
