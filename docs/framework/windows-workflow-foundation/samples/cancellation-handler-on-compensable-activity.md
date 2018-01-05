---
title: "İptal işleyicisi Compensable etkinlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f0f8e05d9a43b02412e7445480f7204fd2e7e13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="7c52e-102">İptal işleyicisi Compensable etkinlik</span><span class="sxs-lookup"><span data-stu-id="7c52e-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="7c52e-103">Bu örnek üzerinde iptal işleyicisi kullanımını gösteren bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="7c52e-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="7c52e-104">Bu örnek kullanımını gösteren iki senaryo içerir <xref:System.Activities.Statements.CompensableActivity> iptali. İlk senaryoda üç alt compensable etkinlikler içeren bir kök compensable etkinlik içerir.</span><span class="sxs-lookup"><span data-stu-id="7c52e-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="7c52e-105">İki alt etkinlik kendi etkinlik gövdeleri başarıyla çalıştırmadan tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="7c52e-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="7c52e-106">Üçüncü alt etkinlik gövde çalıştığında, daha sonra Kök etkinlik iptaline tetiklenir üçüncü etkinlik işleme iptal ederek işlenmiş bir özel durum karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="7c52e-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="7c52e-107">Bu örnekte kök etkinlik mantık önceden tamamlanmış bir iki alt etkinlikler dengelemek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7c52e-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="7c52e-108">İkinci senaryo yürütme gösterir bir <xref:System.Activities.Statements.TryCatch> ile paralel bir <xref:System.Activities.Statements.Delay>, hangi bitmeden önce <xref:System.Activities.Statements.TryCatch> dal.</span><span class="sxs-lookup"><span data-stu-id="7c52e-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="7c52e-109">Tamamlanma durumu kümesine `true` ilk şube tamamlandıktan sonra iptal başka bir şube neden.</span><span class="sxs-lookup"><span data-stu-id="7c52e-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7c52e-110">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7c52e-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7c52e-111">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CompensationCancellation.sln açın.</span><span class="sxs-lookup"><span data-stu-id="7c52e-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="7c52e-112">CTRL + SHIFT + B tuşuna basarak örneği oluşturmak veya "Yapı çözümü" yapı menüsünden seçin...</span><span class="sxs-lookup"><span data-stu-id="7c52e-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="7c52e-113">F5 tuşuna basarak örneği çalıştırmak veya hata ayıklama menüsünden "Hata ayıklamayı Başlat" ı seçin.</span><span class="sxs-lookup"><span data-stu-id="7c52e-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="7c52e-114">Alternatif olarak Ctrl + F5 tuşuna basın veya "Hata ayıklama olmadan Başlat" hata ayıklama menüsünden seçin.</span><span class="sxs-lookup"><span data-stu-id="7c52e-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c52e-115">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c52e-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7c52e-116">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7c52e-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7c52e-117">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7c52e-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7c52e-118">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7c52e-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`