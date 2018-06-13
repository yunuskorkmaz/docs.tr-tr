---
title: Yürütme özellikleri
ms.date: 03/30/2017
ms.assetid: 31c009db-397c-4653-87e2-32dc77fa4b13
ms.openlocfilehash: 201fe222de1cb2029696a1694ae97815db5f913d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513028"
---
# <a name="execution-properties"></a><span data-ttu-id="e42d0-102">Yürütme özellikleri</span><span class="sxs-lookup"><span data-stu-id="e42d0-102">Execution Properties</span></span>
<span data-ttu-id="e42d0-103">Bu örnek tanımlamak ve bir yürütme özelliği özel bir aktivite içinde nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e42d0-103">This sample shows how to define and use an execution property in a custom activity.</span></span> <span data-ttu-id="e42d0-104">Bu örnekte, yürütme özelliği konsolun ön plan rengini belirler.</span><span class="sxs-lookup"><span data-stu-id="e42d0-104">In this example, the execution property determines the console's foreground color.</span></span> <span data-ttu-id="e42d0-105">Örnek iş akışı yürütme nasıl farklı mantıksal yollar gösterir (biri dallandırır bir <xref:System.Activities.Statements.Parallel> etkinlik) farklı konsol renkleri etkinliklerin araya eklemeli yürütülmesini rağmen koruyabilirsiniz (dalları arasında <xref:System.Activities.Statements.Parallel> etkinlik).</span><span class="sxs-lookup"><span data-stu-id="e42d0-105">An example workflow shows how different logical paths of execution (branches of a <xref:System.Activities.Statements.Parallel> activity) can maintain different console colors despite interleaved execution of activities (across the branches of the <xref:System.Activities.Statements.Parallel> activity).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e42d0-106">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="e42d0-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e42d0-107">ExecutionProperties.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e42d0-107">Open the ExecutionProperties.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e42d0-108">Kullanılan özel etkinlikler çözümü aynı zamanda oluşturulması gerekir çünkü çözüm oluşturulmadan önce ThreeColors.xaml görüntüleme bir hata görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e42d0-108">Viewing ThreeColors.xaml before building the solution displays an error, because the custom activities used must be built at the same time as the solution.</span></span>  
  
2.  <span data-ttu-id="e42d0-109">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e42d0-109">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e42d0-110">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e42d0-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e42d0-111">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e42d0-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e42d0-112">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="e42d0-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e42d0-113">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e42d0-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\ExecutionProperties`