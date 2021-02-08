---
description: 'Hakkında daha fazla bilgi edinin: çekme etkinliğini kullanma'
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 3c7a96c6250db8b9301dfeba858568d5638a29f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787753"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="aaea6-103">Pick Etkinliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="aaea6-103">Using the Pick Activity</span></span>

<span data-ttu-id="aaea6-104">Bu örnek, etkinliğin nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Pick> .</span><span class="sxs-lookup"><span data-stu-id="aaea6-104">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="aaea6-105"><xref:System.Activities.Statements.Pick>Etkinlik, olay tabanlı denetim modelleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="aaea6-105">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="aaea6-106">`switch`Deyimdeki dallardan yalnızca birini yürüten C# ifadesiyle benzer şekilde davranır `switch` .</span><span class="sxs-lookup"><span data-stu-id="aaea6-106">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="aaea6-107">Bir `switch` dalın bir değere göre yürütüldüğü deyimin aksine, <xref:System.Activities.Statements.Pick> etkinlik bir etkinliğin nasıl tamamlantığını temel alarak bir dalı yürütür.</span><span class="sxs-lookup"><span data-stu-id="aaea6-107">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="aaea6-108">Bu örnek, bir kullanıcının belirli bir süre içinde konsola kendi adını yazmayı ister.</span><span class="sxs-lookup"><span data-stu-id="aaea6-108">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="aaea6-109"><xref:System.Activities.Statements.Pick>Örnekteki etkinliğin, kullanıcının adında 5 saniye içinde olup olmadığına bağlı olarak yürütülen iki dalı vardır.</span><span class="sxs-lookup"><span data-stu-id="aaea6-109">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="aaea6-110">Kullanıcı adlarını 5 saniye içinde yazdığında, ilk dal yürütülür ve özel bir `ReadLine` etkinlik içerir; Aksi takdirde, bir etkinlik içeren diğer dal yürütülür <xref:System.Activities.Statements.Delay> .</span><span class="sxs-lookup"><span data-stu-id="aaea6-110">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="aaea6-111">Konsola bir kullanıcının adı yazıldığında, kullanıcının adı konsolunda yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="aaea6-111">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="aaea6-112">Bir giriş 5 saniye içinde girilmezse, işlem zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="aaea6-112">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="aaea6-113">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="aaea6-113">Demonstrates</span></span>

 <span data-ttu-id="aaea6-114"><xref:System.Activities.Statements.Pick> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aaea6-114"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="aaea6-115">Tartışma</span><span class="sxs-lookup"><span data-stu-id="aaea6-115">Discussion</span></span>

 <span data-ttu-id="aaea6-116">Örnek, tasarımcı iş akışını ve kodlanmış iş akışını içerir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-116">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="aaea6-117">Tasarımcı Iş akışı Örneğin tasarımcı sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-117">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="aaea6-118">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aaea6-118">The following files are included:</span></span>

- <span data-ttu-id="aaea6-119">Program.cs: `Main` örnek iş akışını yürüten Işlevi içerir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="aaea6-120">ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aaea6-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="aaea6-121">Sequence1. xaml: seçimi kullanan Tasarımcı kullanılarak oluşturulan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="aaea6-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="aaea6-122">Kodlanmış Iş akışı Örneğin kodlanmış sürümü, tasarımcıda bir iş akışının nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-122">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="aaea6-123">Aşağıdaki dosyalar dahil edilmiştir:</span><span class="sxs-lookup"><span data-stu-id="aaea6-123">The following files are included:</span></span>

- <span data-ttu-id="aaea6-124">Program.cs: `Main` örnek iş akışını yürüten Işlevi içerir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-124">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="aaea6-125">ReadString.cs: konsolundan bazı girişleri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="aaea6-125">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="aaea6-126">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="aaea6-126">To use this sample</span></span>

1. <span data-ttu-id="aaea6-127">Visual Studio 2010 kullanarak, pick. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="aaea6-127">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="aaea6-128">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="aaea6-128">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="aaea6-129">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="aaea6-129">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aaea6-130">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="aaea6-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aaea6-131">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="aaea6-131">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="aaea6-132">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="aaea6-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aaea6-133">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aaea6-133">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
