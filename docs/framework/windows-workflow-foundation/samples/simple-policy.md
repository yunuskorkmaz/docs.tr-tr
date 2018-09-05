---
title: Basit ilke
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561270"
---
# <a name="simple-policy"></a><span data-ttu-id="3fe74-102">Basit ilke</span><span class="sxs-lookup"><span data-stu-id="3fe74-102">Simple Policy</span></span>
<span data-ttu-id="3fe74-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Workflow.Activities.PolicyActivity> bir iş akışında etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3fe74-103">This sample shows how to use a <xref:System.Workflow.Activities.PolicyActivity> activity in a workflow.</span></span>  
  
 <span data-ttu-id="3fe74-104">Bu örnekte sıralı iş akışı kullanılarak oluşturulan bir <xref:System.Workflow.Activities.PolicyActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="3fe74-104">The sequential workflow in this sample is created by using a <xref:System.Workflow.Activities.PolicyActivity> activity.</span></span> <span data-ttu-id="3fe74-105">İş akışını tanımlayan `orderValue`, `customerType`, ve `discount` bir ürün tanımlamak için kullanılan alanlar, iş akışı indirim.</span><span class="sxs-lookup"><span data-stu-id="3fe74-105">The workflow defines `orderValue`, `customerType`, and `discount` fields that are used to define a product discount workflow.</span></span> <span data-ttu-id="3fe74-106">Kuralları dosyasında tanımlanan kuralları temel alan bir indirim değeri ayarlamak `orderValue` ve `customerType`.</span><span class="sxs-lookup"><span data-stu-id="3fe74-106">The rules defined in the rules file set a discount value that is based on the `orderValue` and `customerType`.</span></span> <span data-ttu-id="3fe74-107">`orderValue` Ve `customerType` ayarlanan `SimplePolicyWorkflow` sınıf tanımını ve davranışını değiştirmek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3fe74-107">The `orderValue` and `customerType` are set in the `SimplePolicyWorkflow` class definition and can be changed to alter the behavior.</span></span> <span data-ttu-id="3fe74-108">Sonuçta elde edilen indirim konsolda yazılan <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> tanımlanan olay işleyicisi `SimplePolicyWorkflow` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3fe74-108">The resulting discount is written to the console in the <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> event handler that is defined in the `SimplePolicyWorkflow` class.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="3fe74-109">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3fe74-109">To build the sample</span></span>  
  
1.  <span data-ttu-id="3fe74-110">Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3fe74-110">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3fe74-111">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3fe74-111">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="3fe74-112">CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3fe74-112">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="3fe74-113">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3fe74-113">To run the sample</span></span>  
  
-   <span data-ttu-id="3fe74-114">SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını SimplePolicy\bin\debug klasöre (veya Visual Basic sürümünü SimplePolicy\bin klasörü) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3fe74-114">In the SDK Command Prompt window, run the .exe file in the SimplePolicy\bin\debug folder (or the SimplePolicy\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3fe74-115">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="3fe74-115">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3fe74-116">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="3fe74-116">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3fe74-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3fe74-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3fe74-118">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="3fe74-118">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a><span data-ttu-id="3fe74-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3fe74-119">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="3fe74-120">Gelişmiş İlke</span><span class="sxs-lookup"><span data-stu-id="3fe74-120">Advanced Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
