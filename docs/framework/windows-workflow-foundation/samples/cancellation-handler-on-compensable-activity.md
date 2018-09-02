---
title: Compensable etkinliğinde iptal işleyicisi
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442713"
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="7445a-102">Compensable etkinliğinde iptal işleyicisi</span><span class="sxs-lookup"><span data-stu-id="7445a-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="7445a-103">Bu örnek, üzerinde bir iptal işleyicisi kullanımını gösterir. bir <xref:System.Activities.Statements.CompensableActivity>.</span><span class="sxs-lookup"><span data-stu-id="7445a-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="7445a-104">Bu örnek kullanımını gösteren iki senaryo içerir <xref:System.Activities.Statements.CompensableActivity> iptali. İlk senaryoda üç alt compensable etkinlikler içeren bir kök compensable etkinliği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="7445a-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="7445a-105">İki alt etkinlik, etkinlik gövdeleri başarıyla çalıştığını tamamlayın.</span><span class="sxs-lookup"><span data-stu-id="7445a-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="7445a-106">Üçüncü bir alt etkinlik gövdesi çalıştığında, sonra Kök etkinlik iptal tetiklenir üçüncü etkinlik işleme iptal tarafından işlenen özel durum karşılaşır.</span><span class="sxs-lookup"><span data-stu-id="7445a-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="7445a-107">Bu örnekte kök etkinlik mantığı, daha önce tamamlanan bir iki alt etkinlikleri dengelemek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7445a-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
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
  
 <span data-ttu-id="7445a-108">İkinci senaryoda yürütme gösterir bir <xref:System.Activities.Statements.TryCatch> ile paralel bir <xref:System.Activities.Statements.Delay>, önce tamamlanır <xref:System.Activities.Statements.TryCatch> dal.</span><span class="sxs-lookup"><span data-stu-id="7445a-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="7445a-109">Tamamlama koşul kümesine `true` ilk dal tamamlandıktan sonra diğer dal iptal edilmesine neden.</span><span class="sxs-lookup"><span data-stu-id="7445a-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7445a-110">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="7445a-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7445a-111">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CompensationCancellation.sln açın.</span><span class="sxs-lookup"><span data-stu-id="7445a-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="7445a-112">CTRL + SHIFT + B tuşlarına basarak örneği oluşturmak veya derleme menüsünden "Çözümü Derle" seçin...</span><span class="sxs-lookup"><span data-stu-id="7445a-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="7445a-113">F5 tuşuna basarak örneği çalıştırın veya hata ayıklama menüsünden "Hata ayıklamaya Başla"'i seçin.</span><span class="sxs-lookup"><span data-stu-id="7445a-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="7445a-114">Alternatif olarak, Ctrl + F5 tuşlarına basın veya hata ayıklama menüsünden "Hata ayıklama olmadan Başlat"'i seçin.</span><span class="sxs-lookup"><span data-stu-id="7445a-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7445a-115">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="7445a-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7445a-116">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7445a-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7445a-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7445a-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7445a-118">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7445a-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`