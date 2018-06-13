---
title: Bir etkinlik örnek AsyncOperationContext kullanma
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: da7b62ef9e29621d1e6ee1046afb5455af1164bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515503"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="0187d-102">Bir etkinlik örnek AsyncOperationContext kullanma</span><span class="sxs-lookup"><span data-stu-id="0187d-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="0187d-103">Bu örnek, bir özel geliştirmek gösterilmiştir <xref:System.Activities.CodeActivity> kullanan <xref:System.Activities.AsyncCodeActivityContext> iş akışı dışında zaman uyumsuz olarak gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="0187d-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0187d-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0187d-104">Sample Details</span></span>  
 <span data-ttu-id="0187d-105">Örnek etkinlik kullanan <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.EndWrite%2A> yöntemlere <xref:System.IO.FileStream> zaman uyumsuz olarak verileri bir dosyaya yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0187d-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="0187d-106">Burada sunulan düzeni diğer zaman uyumsuz yöntemleri ile kullanılmak üzere uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0187d-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="0187d-107">Zaman uyumsuz işlem yürütülürken, diğer etkinlikler iş akışında yürütebilir, ancak iş akışı kalıcı yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0187d-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0187d-108">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="0187d-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0187d-109">Async.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0187d-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0187d-110">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0187d-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0187d-111">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0187d-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0187d-112">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0187d-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0187d-113">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0187d-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0187d-114">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0187d-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`