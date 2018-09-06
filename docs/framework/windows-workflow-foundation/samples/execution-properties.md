---
title: Yürütme özellikleri
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 4906c2ad11c8b5822764435d2b39a5b51f2673ba
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748200"
---
# <a name="execution-properties"></a><span data-ttu-id="5700f-102">Yürütme özellikleri</span><span class="sxs-lookup"><span data-stu-id="5700f-102">Execution Properties</span></span>
<span data-ttu-id="5700f-103">Bu örnek, bir yürütme özelliği özel bir etkinlikte kullanmadan nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5700f-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="5700f-104">Bu örnekte, yürütme özelliği konsolun ön plan rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="5700f-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="5700f-105">Bir örnek iş akışı yürütme mantıksal nasıl farklı yolları gösterir (dallar, bir <xref:System.Activities.Statements.Parallel> etkinlik) aralıklı yürütme etkinlikleri rağmen farklı konsol renkleri koruyabilirsiniz (dalları arasında <xref:System.Activities.Statements.Parallel> etkinliği).</span><span class="sxs-lookup"><span data-stu-id="5700f-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5700f-106">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5700f-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5700f-107">ExecutionProperties.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5700f-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5700f-108">Çözümü oluşturmadan önce ThreeColors.xaml görüntüleme, kullanılan özel etkinlikler çözümü olarak aynı anda oluşturulması gereken olduğundan bir hata görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5700f-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="5700f-109">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5700f-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5700f-110">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5700f-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5700f-111">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5700f-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5700f-112">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5700f-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5700f-113">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5700f-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`