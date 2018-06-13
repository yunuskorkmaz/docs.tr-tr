---
title: Daraltılmış paralel ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 195c627d62665f832384989d4ef03105c4af3757
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516268"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="6f7bb-102">Daraltılmış paralel ForEach</span><span class="sxs-lookup"><span data-stu-id="6f7bb-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="6f7bb-103">`ThrottleParallelForEach` Etkinlik benzer <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` etkinliği bir özel durum ile onun bir eşzamanlılık faktörü ayarını yürütmek için eşzamanlı dalların sayısını kısıtlayın izin verir.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="6f7bb-104">`ThrottleParallelForEach` Etkinlik türer <xref:System.Activities.NativeActivity>, diğer etkinlikleri (alt) zamanlama gerekir ve bu yalnızca üzerinden erişilebilir olduğundan <xref:System.Activities.NativeActivityContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>  
  
## <a name="projects"></a><span data-ttu-id="6f7bb-105">Projeler</span><span class="sxs-lookup"><span data-stu-id="6f7bb-105">Projects</span></span>  
  
|<span data-ttu-id="6f7bb-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="6f7bb-106">**ProjectName**</span></span>|<span data-ttu-id="6f7bb-107">**Açıklama**</span><span class="sxs-lookup"><span data-stu-id="6f7bb-107">**Description**</span></span>|<span data-ttu-id="6f7bb-108">**Ana dosyaları**</span><span class="sxs-lookup"><span data-stu-id="6f7bb-108">**Main Files**</span></span>|  
|-|-|-|  
|<span data-ttu-id="6f7bb-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="6f7bb-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="6f7bb-110">İçeren `ThrottledParallelForEach` etkinliği ve onun Tasarımcısı.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="6f7bb-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="6f7bb-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="6f7bb-112">`ThrottledParallelForEach` Etkinlik tanımı.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-112">The `ThrottledParallelForEach` activity definition.</span></span>|  
|<span data-ttu-id="6f7bb-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="6f7bb-113">CodeTestClient</span></span>|<span data-ttu-id="6f7bb-114">Örnek yapılandırır ve bir iş akışı ile çalıştıran istemci uygulamanın bir `ThrottledParallelForEach` kesinlik temelli kod kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="6f7bb-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="6f7bb-115">Program.cs</span></span><br /><br /> <span data-ttu-id="6f7bb-116">Örnek iş akışı örneğini çalıştıran ve tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-116">Defines and runs an instance of the sample workflow.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6f7bb-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6f7bb-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="6f7bb-118">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ThrottledParallelForEach.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ThrottledParallelForEach.sln file.</span></span>  
  
2.  <span data-ttu-id="6f7bb-119">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-119">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6f7bb-120">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-120">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f7bb-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6f7bb-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6f7bb-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f7bb-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`