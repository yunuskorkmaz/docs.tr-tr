---
title: "Bir etkinlik örnek AsyncOperationContext kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa36c3173e4e20d063f93b3583d063057b9bac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="9a375-102">Bir etkinlik örnek AsyncOperationContext kullanma</span><span class="sxs-lookup"><span data-stu-id="9a375-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="9a375-103">Bu örnek, bir özel geliştirmek gösterilmiştir <xref:System.Activities.CodeActivity> kullanan <xref:System.Activities.AsyncCodeActivityContext> iş akışı dışında zaman uyumsuz olarak gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="9a375-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9a375-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9a375-104">Sample Details</span></span>  
 <span data-ttu-id="9a375-105">Örnek etkinlik kullanan <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.EndWrite%2A> yöntemlere <xref:System.IO.FileStream> zaman uyumsuz olarak verileri bir dosyaya yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9a375-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="9a375-106">Burada sunulan düzeni diğer zaman uyumsuz yöntemleri ile kullanılmak üzere uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9a375-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="9a375-107">Zaman uyumsuz işlem yürütülürken, diğer etkinlikler iş akışında yürütebilir, ancak iş akışı kalıcı yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="9a375-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a375-108">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="9a375-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9a375-109">Async.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9a375-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a375-110">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9a375-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9a375-111">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a375-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9a375-112">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9a375-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9a375-113">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9a375-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a375-114">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9a375-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`