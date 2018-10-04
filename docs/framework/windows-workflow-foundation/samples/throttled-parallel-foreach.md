---
title: Kısıtlanmış paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 8691edb8a5a61204b187be8def553f2f06be0f0d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581868"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="dac0c-102">Kısıtlanmış paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="dac0c-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="dac0c-103">`ThrottleParallelForEach` Etkinlik benzer <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` etkinliği ile bir özel durum olan ayarlamaya olanak tanır eşzamanlılık faktörü yürütmek için eşzamanlı dalların sayısını sınırlamak için.</span><span class="sxs-lookup"><span data-stu-id="dac0c-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="dac0c-104">`ThrottleParallelForEach` Etkinlik türetilir <xref:System.Activities.NativeActivity>, diğer etkinlikleri (alt) zamanlamak gereken ve bu yalnızca üzerinden erişilebilir olduğundan <xref:System.Activities.NativeActivityContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dac0c-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="dac0c-105">Projeler</span><span class="sxs-lookup"><span data-stu-id="dac0c-105">Projects</span></span>

|<span data-ttu-id="dac0c-106">**projectName**</span><span class="sxs-lookup"><span data-stu-id="dac0c-106">**ProjectName**</span></span>|<span data-ttu-id="dac0c-107">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="dac0c-107">**Description**</span></span>|<span data-ttu-id="dac0c-108">**Ana dosyaları**</span><span class="sxs-lookup"><span data-stu-id="dac0c-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="dac0c-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="dac0c-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="dac0c-110">İçeren `ThrottledParallelForEach` etkinlik ve iş Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="dac0c-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="dac0c-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="dac0c-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="dac0c-112">`ThrottledParallelForEach` Etkinlik tanımı.</span><span class="sxs-lookup"><span data-stu-id="dac0c-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="dac0c-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="dac0c-113">CodeTestClient</span></span>|<span data-ttu-id="dac0c-114">Örnek, yapılandırır ve bir iş akışı ile çalışan istemci uygulama bir `ThrottledParallelForEach` kesin kod kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dac0c-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="dac0c-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="dac0c-115">Program.cs</span></span><br /><br /> <span data-ttu-id="dac0c-116">Örnek iş akışı örneğini çalıştıran ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dac0c-116">Defines and runs an instance of the sample workflow.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="dac0c-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dac0c-117">To use this sample</span></span>

1.  <span data-ttu-id="dac0c-118">Visual Studio 2010'u kullanarak, ThrottledParallelForEach.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dac0c-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2.  <span data-ttu-id="dac0c-119">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="dac0c-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="dac0c-120">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="dac0c-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="dac0c-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="dac0c-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dac0c-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dac0c-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dac0c-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="dac0c-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dac0c-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dac0c-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`