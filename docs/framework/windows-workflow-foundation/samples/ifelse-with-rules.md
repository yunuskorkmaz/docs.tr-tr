---
title: Ifelse kurallarla
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bec818ca5492e9a49a602a4f7baef4b45cb073c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="1f536-102">Ifelse kurallarla</span><span class="sxs-lookup"><span data-stu-id="1f536-102">IfElse With Rules</span></span>
<span data-ttu-id="1f536-103">Bu örnek, bir kural koşulu ile kullanımını göstermektedir bir <xref:System.Workflow.Activities.IfElseActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1f536-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="1f536-104">Örnek olarak geçirir bir `OrderValue` ana bilgisayardan parametresi.</span><span class="sxs-lookup"><span data-stu-id="1f536-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="1f536-105">Bir kural koşulu ilk dalı parametresinin değeri kullanılıyor <xref:System.Workflow.Activities.IfElseActivity> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="1f536-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="1f536-106">Değer 10. 000'den az ise, ilk dal yürütür ve <xref:System.Workflow.Activities.CodeActivity> ilk şube etkinliğinde yazdırır **Yöneticisi Onayı alma** konsoluna.</span><span class="sxs-lookup"><span data-stu-id="1f536-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="1f536-107">Değer, 10.000 büyük olduğunda <xref:System.Workflow.Activities.CodeActivity> etkinlik ikinci dal yürütür ve yazdırır **VP onay almak**.</span><span class="sxs-lookup"><span data-stu-id="1f536-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="1f536-108">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="1f536-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="1f536-109">Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f536-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="1f536-110">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1f536-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1f536-111">CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f536-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="1f536-112">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1f536-112">To run the sample</span></span>  
  
-   <span data-ttu-id="1f536-113">Örnek için ana klasörü altında bulunan .exe dosyasını IfElseWithRules\bin\debug klasöründe (veya örnek Visual Basic sürümü için IfElseWithRules\bin klasör) SDK komut istemi penceresinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f536-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f536-114">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1f536-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1f536-115">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="1f536-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1f536-116">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1f536-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f536-117">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="1f536-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="1f536-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f536-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
