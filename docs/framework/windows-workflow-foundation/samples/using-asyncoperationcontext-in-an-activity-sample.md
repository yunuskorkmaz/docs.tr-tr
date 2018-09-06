---
title: Bir etkinlik örnek AsyncOperationContext kullanma
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872702"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="c3f7e-102">Bir etkinlik örnek AsyncOperationContext kullanma</span><span class="sxs-lookup"><span data-stu-id="c3f7e-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="c3f7e-103">Bu örnek bir özel nasıl geliştirilebileceğini gösterir <xref:System.Activities.CodeActivity> kullanan <xref:System.Activities.AsyncCodeActivityContext> iş akışı dışında zaman uyumsuz olarak gerçekleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="c3f7e-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="c3f7e-104">Sample Details</span></span>  
 <span data-ttu-id="c3f7e-105">Örnek etkinlik kullanan <xref:System.IO.FileStream.BeginWrite%2A> ve <xref:System.IO.FileStream.EndWrite%2A> yöntemlerde <xref:System.IO.FileStream> sınıfı zaman uyumsuz olarak bir dosyaya veri yazmak için.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="c3f7e-106">Burada sunulan deseni diğer zaman uyumsuz yöntemleri ile kullanılmak üzere uyarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="c3f7e-107">Zaman uyumsuz işlemi yürütülürken, diğer etkinlikler ile iş akışı çalıştırabilirsiniz, ancak iş akışı kalıcı yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c3f7e-108">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c3f7e-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c3f7e-109">Async.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c3f7e-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3f7e-110">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3f7e-111">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3f7e-112">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3f7e-113">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3f7e-114">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c3f7e-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`