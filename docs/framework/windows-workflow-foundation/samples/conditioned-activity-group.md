---
title: Koşullu etkinlik grubu
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418175"
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="a6d91-102">Koşullu etkinlik grubu</span><span class="sxs-lookup"><span data-stu-id="a6d91-102">Conditioned Activity Group</span></span>
<span data-ttu-id="a6d91-103">Örnek, bir seyahat kayıt uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a6d91-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="a6d91-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) sahip iki kod etkinliği: bir araba etkinliği ve bir uçak etkinliği.</span><span class="sxs-lookup"><span data-stu-id="a6d91-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="a6d91-105">İçinde `SimpleCAGWorkflow` Oluşturucu, bir "travelNeedType" ArrayList'i gerekli olan seyahat rezervasyonlarının türleri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a6d91-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="a6d91-106">Birini veya her ikisini yorum tarafından `travelNeeds.Add` deyimleri CAG davranışı uygun şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a6d91-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="a6d91-107">Hem araç hem de Havayolu etkinliklerin kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşul ile doldurulur bir <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="a6d91-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="a6d91-108">Yalnızca bir araba etkinliği yürütür `travelNeeds` gruplandırmasında bir `TravelNeeds.Car` girişi ve yalnızca bir etkinliği yürütür Havayolu `travelNeeds` gruplandırmasında bir `TravelNeeds.Airline` girişi.</span><span class="sxs-lookup"><span data-stu-id="a6d91-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="a6d91-109">Her etkinliğin yürütülmesine karşılık gelen bir giriş koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6d91-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="a6d91-110">Varsayılan <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> koşulu belirtir alt yürütülen veya yürütme için hazır CAG çıkılması gerekiyor (göre kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşulları).</span><span class="sxs-lookup"><span data-stu-id="a6d91-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="a6d91-111">Bu örnekte, bu CAG ne zaman çıkar anlamına gelir `travelNeeds` koleksiyonu boş.</span><span class="sxs-lookup"><span data-stu-id="a6d91-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="a6d91-112">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a6d91-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="a6d91-113">Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6d91-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6d91-114">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a6d91-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a6d91-115">CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a6d91-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="a6d91-116">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a6d91-116">To run the sample</span></span>  
  
-   <span data-ttu-id="a6d91-117">SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını SimpleCAG\bin\debug klasöre (veya Visual Basic sürümünü SimpleCAG\bin klasörü) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a6d91-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6d91-118">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="a6d91-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a6d91-119">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="a6d91-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6d91-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a6d91-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6d91-121">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="a6d91-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="a6d91-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d91-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
