---
title: Kurallarla Ifelse
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483012"
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="7d37f-102">Kurallarla Ifelse</span><span class="sxs-lookup"><span data-stu-id="7d37f-102">IfElse With Rules</span></span>
<span data-ttu-id="7d37f-103">Bu örnek, bir kural koşulu ile kullanımını gösterir. bir <xref:System.Workflow.Activities.IfElseActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7d37f-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="7d37f-104">Örnek içinde geçen bir `OrderValue` konaktan parametresi.</span><span class="sxs-lookup"><span data-stu-id="7d37f-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="7d37f-105">Parametresinin değeri ilk dalı bir kural koşulu kullanılır <xref:System.Workflow.Activities.IfElseActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="7d37f-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="7d37f-106">Değer 10. 000'den az ise ilk dalı yürütür ve <xref:System.Workflow.Activities.CodeActivity> ilk dalı etkinliğinde yazdırır **yönetici onayı alma** konsola.</span><span class="sxs-lookup"><span data-stu-id="7d37f-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="7d37f-107">Değeri, 10.000 büyükse <xref:System.Workflow.Activities.CodeActivity> ikinci daldaki etkinliği yürütür ve yazdırır **VP onay alma**.</span><span class="sxs-lookup"><span data-stu-id="7d37f-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="7d37f-108">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="7d37f-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="7d37f-109">Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d37f-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="7d37f-110">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7d37f-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7d37f-111">CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d37f-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7d37f-112">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7d37f-112">To run the sample</span></span>  
  
-   <span data-ttu-id="7d37f-113">SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını IfElseWithRules\bin\debug klasöre (veya Visual Basic sürümünü IfElseWithRules\bin klasörü) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7d37f-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d37f-114">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="7d37f-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7d37f-115">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="7d37f-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7d37f-116">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7d37f-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d37f-117">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="7d37f-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="7d37f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d37f-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
