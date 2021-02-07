---
description: 'Daha fazla bilgi edinin: kısıtlanmış paralel ForEach'
title: Kısıtlanmış Paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 2c1d1386f0b8c5b3c68d60bc83386ccfdf5e7875
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741685"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="de620-103">Kısıtlanmış Paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="de620-103">Throttled Parallel ForEach</span></span>

<span data-ttu-id="de620-104">`ThrottleParallelForEach`Etkinlik, <xref:System.Activities.Statements.ParallelForEach%601> eşzamanlı dalların yürütülmesi için eşzamanlılık faktörünün ayarlanmasına izin veren bir özel durumla etkinlik ile benzerdir.</span><span class="sxs-lookup"><span data-stu-id="de620-104">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="de620-105">`ThrottleParallelForEach`Etkinliğin <xref:System.Activities.NativeActivity> , diğer etkinlikleri (alt etkinlikler) zamanlaması gerektiğinden ve bu, yalnızca sınıfı aracılığıyla erişilebilir olduğundan, öğesinden türetilir <xref:System.Activities.NativeActivityContext> .</span><span class="sxs-lookup"><span data-stu-id="de620-105">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="de620-106">Projeler</span><span class="sxs-lookup"><span data-stu-id="de620-106">Projects</span></span>

|<span data-ttu-id="de620-107">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="de620-107">**ProjectName**</span></span>|<span data-ttu-id="de620-108">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="de620-108">**Description**</span></span>|<span data-ttu-id="de620-109">**Ana dosyalar**</span><span class="sxs-lookup"><span data-stu-id="de620-109">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="de620-110">Bir azaltıcı ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="de620-110">ThrottledParallelForEach</span></span>|<span data-ttu-id="de620-111">`ThrottledParallelForEach`Etkinlik ve tasarımcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="de620-111">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="de620-112">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="de620-112">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="de620-113">`ThrottledParallelForEach`Etkinlik tanımı.</span><span class="sxs-lookup"><span data-stu-id="de620-113">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="de620-114">Codetekstclient</span><span class="sxs-lookup"><span data-stu-id="de620-114">CodeTestClient</span></span>|<span data-ttu-id="de620-115">Bir iş akışını yapılandıran ve bu örnek bir kod kullanarak çalıştıran örnek istemci uygulaması `ThrottledParallelForEach` .</span><span class="sxs-lookup"><span data-stu-id="de620-115">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="de620-116">Program.cs</span><span class="sxs-lookup"><span data-stu-id="de620-116">Program.cs</span></span><br /><br /> <span data-ttu-id="de620-117">Örnek iş akışının bir örneğini tanımlar ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="de620-117">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="de620-118">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="de620-118">To use this sample</span></span>

1. <span data-ttu-id="de620-119">Visual Studio 2010 kullanarak, Kısıtledparallelforeach. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="de620-119">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="de620-120">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="de620-120">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="de620-121">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="de620-121">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de620-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="de620-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de620-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="de620-123">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="de620-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="de620-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de620-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="de620-125">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
