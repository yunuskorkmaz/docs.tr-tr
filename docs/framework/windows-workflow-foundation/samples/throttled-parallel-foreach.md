---
title: Kısıtlanmış Paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 340e4ff154b63221ec911c872a1154bdb672cf8c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715915"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="89c8f-102">Kısıtlanmış Paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="89c8f-102">Throttled Parallel ForEach</span></span>

<span data-ttu-id="89c8f-103">`ThrottleParallelForEach` etkinliği, eş zamanlı dalların yürütülmesi için eşzamanlılık faktörünün ayarlanmasına izin veren bir özel durumla <xref:System.Activities.Statements.ParallelForEach%601> etkinliğe benzer.</span><span class="sxs-lookup"><span data-stu-id="89c8f-103">The `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="89c8f-104">`ThrottleParallelForEach` etkinliği, diğer etkinlikleri (alt etkinlikler) zamanlaması gerektiğinden ve bu yalnızca <xref:System.Activities.NativeActivityContext> sınıfı aracılığıyla erişilebilir olduğu için <xref:System.Activities.NativeActivity>türetilir.</span><span class="sxs-lookup"><span data-stu-id="89c8f-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="89c8f-105">Projeler</span><span class="sxs-lookup"><span data-stu-id="89c8f-105">Projects</span></span>

|<span data-ttu-id="89c8f-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="89c8f-106">**ProjectName**</span></span>|<span data-ttu-id="89c8f-107">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="89c8f-107">**Description**</span></span>|<span data-ttu-id="89c8f-108">**Ana dosyalar**</span><span class="sxs-lookup"><span data-stu-id="89c8f-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="89c8f-109">Bir azaltıcı ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="89c8f-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="89c8f-110">`ThrottledParallelForEach` etkinliği ve tasarımcısını içerir.</span><span class="sxs-lookup"><span data-stu-id="89c8f-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="89c8f-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="89c8f-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="89c8f-112">`ThrottledParallelForEach` etkinlik tanımı.</span><span class="sxs-lookup"><span data-stu-id="89c8f-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="89c8f-113">Codetekstclient</span><span class="sxs-lookup"><span data-stu-id="89c8f-113">CodeTestClient</span></span>|<span data-ttu-id="89c8f-114">Zorunlu kod kullanarak bir `ThrottledParallelForEach` iş akışı yapılandıran ve çalıştıran örnek istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="89c8f-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="89c8f-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="89c8f-115">Program.cs</span></span><br /><br /> <span data-ttu-id="89c8f-116">Örnek iş akışının bir örneğini tanımlar ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="89c8f-116">Defines and runs an instance of the sample workflow.</span></span>|

## <a name="to-use-this-sample"></a><span data-ttu-id="89c8f-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="89c8f-117">To use this sample</span></span>

1. <span data-ttu-id="89c8f-118">Visual Studio 2010 kullanarak, Kısıtledparallelforeach. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="89c8f-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2. <span data-ttu-id="89c8f-119">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="89c8f-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="89c8f-120">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="89c8f-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89c8f-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="89c8f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="89c8f-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="89c8f-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="89c8f-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="89c8f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89c8f-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="89c8f-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`
