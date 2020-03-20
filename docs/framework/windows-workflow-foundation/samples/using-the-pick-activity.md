---
title: Pick Etkinliği Kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142621"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="e0970-102">Pick Etkinliği Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0970-102">Using the Pick Activity</span></span>
<span data-ttu-id="e0970-103">Bu örnek, etkinliğin nasıl <xref:System.Activities.Statements.Pick> kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0970-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="e0970-104">Etkinlik <xref:System.Activities.Statements.Pick> olay tabanlı denetim modellemesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0970-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="e0970-105">İfadedeki dallardan yalnızca birini `switch` çalıştıran C# deyimine benzer `switch` şekilde direnir.</span><span class="sxs-lookup"><span data-stu-id="e0970-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="e0970-106">Bir `switch` dalın bir değere bağlı olarak yürütüldettiği ifadeden <xref:System.Activities.Statements.Pick> farklı olarak, etkinlik bir etkinliğin nasıl tamamlandığına bağlı olarak bir dalı yürütür.</span><span class="sxs-lookup"><span data-stu-id="e0970-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="e0970-107">Bu örnek, bir kullanıcıdan belirli bir süre içinde konsola kendi adını yazmasını ister.</span><span class="sxs-lookup"><span data-stu-id="e0970-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="e0970-108">Örnekteki etkinlik, <xref:System.Activities.Statements.Pick> kullanıcının 5 saniye içinde kendi adına tip yapıp yapmamaya bağlı olarak yürütülen iki dala sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0970-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="e0970-109">Kullanıcı 5 saniye içinde kendi adına tiplerse, ilk dal `ReadLine` yürütülür ve bu da özel bir etkinlik içerir; aksi takdirde diğer dal yürütülür, bir <xref:System.Activities.Statements.Delay> etkinlik içerir.</span><span class="sxs-lookup"><span data-stu-id="e0970-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="e0970-110">Konsola bir kullanıcının adı yazıldıktan sonra, kullanıcının adı konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="e0970-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="e0970-111">Bir giriş 5 saniye içinde girmezse, işlem zaman lanır.</span><span class="sxs-lookup"><span data-stu-id="e0970-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e0970-112">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e0970-112">Demonstrates</span></span>
 <span data-ttu-id="e0970-113"><xref:System.Activities.Statements.Pick>Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e0970-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="e0970-114">Tartışma</span><span class="sxs-lookup"><span data-stu-id="e0970-114">Discussion</span></span>
 <span data-ttu-id="e0970-115">Örnek, Tasarımcı iş akışı ve kodlanmış iş akışı içerir.</span><span class="sxs-lookup"><span data-stu-id="e0970-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="e0970-116">Tasarımcı İş Akışı Örneğin Tasarımcı sürümü, tasarımcıda nasıl bir iş akışı oluşturulacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0970-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="e0970-117">Aşağıdaki dosyalar dahildir:</span><span class="sxs-lookup"><span data-stu-id="e0970-117">The following files are included:</span></span>

- <span data-ttu-id="e0970-118">Program.cs : `Main` Örnek iş akışını yürüten işlevi içerir.</span><span class="sxs-lookup"><span data-stu-id="e0970-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="e0970-119">ReadString.cs: Konsoldan bazı girdileri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e0970-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="e0970-120">Sequence1.xaml: Pick kullanan tasarımcı kullanılarak oluşturulan bir iş akışı.</span><span class="sxs-lookup"><span data-stu-id="e0970-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="e0970-121">Kodlanmış İş Akışı Örneğin kodlanmış sürümü, tasarımcıda nasıl bir iş akışı oluşturulacak larını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0970-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="e0970-122">Aşağıdaki dosyalar dahildir:</span><span class="sxs-lookup"><span data-stu-id="e0970-122">The following files are included:</span></span>

- <span data-ttu-id="e0970-123">Program.cs : `Main` Örnek iş akışını yürüten işlevi içerir.</span><span class="sxs-lookup"><span data-stu-id="e0970-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="e0970-124">ReadString.cs: Konsoldan bazı girdileri okuyan özel bir etkinlik.</span><span class="sxs-lookup"><span data-stu-id="e0970-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="e0970-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e0970-125">To use this sample</span></span>

1. <span data-ttu-id="e0970-126">Visual Studio 2010'u kullanarak Pick.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e0970-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="e0970-127">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0970-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="e0970-128">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0970-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0970-129">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0970-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e0970-130">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e0970-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e0970-131">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e0970-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e0970-132">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0970-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
