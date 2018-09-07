---
title: Gelişmiş ilke
ms.date: 03/30/2017
ms.assetid: 75a22c88-5e54-4ae8-84cb-fbb22a612f0a
ms.openlocfilehash: becdc28affd877239474d6f0f007a480297bccb8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083796"
---
# <a name="advanced-policy"></a><span data-ttu-id="70426-102">Gelişmiş ilke</span><span class="sxs-lookup"><span data-stu-id="70426-102">Advanced Policy</span></span>
<span data-ttu-id="70426-103">Bu örnek, basit ilke örneği genişletir.</span><span class="sxs-lookup"><span data-stu-id="70426-103">This sample extends the Simple Policy sample.</span></span> <span data-ttu-id="70426-104">Konut indirim ve iş indirim basit ilke örneği kurallarından ek olarak, birçok yeni kuralı eklendi.</span><span class="sxs-lookup"><span data-stu-id="70426-104">In addition to the residential discount and business discount rules from the Simple Policy example, several new rules have been added.</span></span>  
  
 <span data-ttu-id="70426-105">Yüksek değerli siparişlerini büyük indirimi sağlayan bir yüksek değerli kuralı eklenir.</span><span class="sxs-lookup"><span data-stu-id="70426-105">A high-value rule is added, which provides a bigger discount for high-value orders.</span></span> <span data-ttu-id="70426-106">Öncelik değeri verilir değerinden önceki iki kuralları indirim alanın üzerine ve her iki konut üzerinde önceliği ve iş indirim kuralları alır.</span><span class="sxs-lookup"><span data-stu-id="70426-106">It is given a priority value less than the previous two rules so that it will overwrite the discount field and take precedence over both the residential and business discount rules.</span></span>  
  
 <span data-ttu-id="70426-107">Calculate toplam kural da eklenir, indirim düzeyine dayalı toplam hesaplar.</span><span class="sxs-lookup"><span data-stu-id="70426-107">A calculate total rule is also added, which computes the total based on the discount level.</span></span> <span data-ttu-id="70426-108">Bu, iş akışı etkinlikte tanımlanmış bir yöntem yapmayı yanı sıra başka eylemler kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="70426-108">It shows how to reference a method defined on the workflow activity, as well as how to use else actions.</span></span> <span data-ttu-id="70426-109">Bu kural, ayrıca olacağından, bu davranışı zincirleme dilediğiniz zaman değerlendirilen indirim alan değişiklikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="70426-109">This rule also demonstrates chaining behavior since it will be evaluated anytime the discount field changes.</span></span> <span data-ttu-id="70426-110">Ayrıca, yöntemi öznitelik atanıyor RuleWriteAttribute CalculateTotal yöntemi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="70426-110">Furthermore, method attributing is shown with the RuleWriteAttribute on the CalculateTotal method.</span></span> <span data-ttu-id="70426-111">Bu, etkilenen kurallar (yöntemi yürütülen her yeniden değerlendirilecek ErrorTotalRule) neden olur.</span><span class="sxs-lookup"><span data-stu-id="70426-111">This causes impacted rules (ErrorTotalRule) to be re-evaluated whenever the method gets executed.</span></span>  
  
 <span data-ttu-id="70426-112">Eklenen son kuralı (Bu durumda, toplam 0'dan) hataları tespit biridir.</span><span class="sxs-lookup"><span data-stu-id="70426-112">The last rule added is one that detects errors (in this case, Total less than 0).</span></span> <span data-ttu-id="70426-113">Bu meydana gelirse, ilke yürütme durdurulur.</span><span class="sxs-lookup"><span data-stu-id="70426-113">If this occurs, the policy execution is halted.</span></span>  
  
 <span data-ttu-id="70426-114">Son olarak, `Console.Writeline` çağrıları, kural yürütme daha fazla görünürlük sağlamak için her bir kural olarak eklenir, mümkün olduğunu da gösterirken statik yöntemler erişmeye türleri başvurulan.</span><span class="sxs-lookup"><span data-stu-id="70426-114">Finally, `Console.Writeline` calls are added as actions to each rule to provide more visibility into rule execution, while also showing that it is possible to access static methods on referenced types.</span></span> <span data-ttu-id="70426-115">İzleme, yürütülen kurallara görünürlük elde etmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70426-115">You could also use tracking to get visibility into the rules that are executed.</span></span>  
  
 <span data-ttu-id="70426-116">Bu örnekte kullanılan kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="70426-116">The rules used in this sample are:</span></span>  
  
 <span data-ttu-id="70426-117">**ResidentialDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="70426-117">**ResidentialDiscountRule:**</span></span>  
  
 <span data-ttu-id="70426-118">Eğer sipariş değeri olarak > 500 ve CustomerType konut =</span><span class="sxs-lookup"><span data-stu-id="70426-118">IF OrderValue > 500 AND CustomerType = Residential</span></span>  
  
 <span data-ttu-id="70426-119">ARDINDAN indirim = % 5</span><span class="sxs-lookup"><span data-stu-id="70426-119">THEN Discount = 5%</span></span>  
  
 <span data-ttu-id="70426-120">**BusinessDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="70426-120">**BusinessDiscountRule:**</span></span>  
  
 <span data-ttu-id="70426-121">Eğer sipariş değeri olarak > 10000 ve CustomerType iş =</span><span class="sxs-lookup"><span data-stu-id="70426-121">IF OrderValue > 10000 AND CustomerType = Business</span></span>  
  
 <span data-ttu-id="70426-122">ARDINDAN indirim % 10 =</span><span class="sxs-lookup"><span data-stu-id="70426-122">THEN Discount = 10%</span></span>  
  
 <span data-ttu-id="70426-123">**HighValueDiscountRule:**</span><span class="sxs-lookup"><span data-stu-id="70426-123">**HighValueDiscountRule:**</span></span>  
  
 <span data-ttu-id="70426-124">Eğer sipariş değeri olarak > 20000</span><span class="sxs-lookup"><span data-stu-id="70426-124">IF OrderValue > 20000</span></span>  
  
 <span data-ttu-id="70426-125">ARDINDAN indirim % 15 =</span><span class="sxs-lookup"><span data-stu-id="70426-125">THEN Discount = 15%</span></span>  
  
 <span data-ttu-id="70426-126">**TotalRule:**</span><span class="sxs-lookup"><span data-stu-id="70426-126">**TotalRule:**</span></span>  
  
 <span data-ttu-id="70426-127">Eğer indirim > 0</span><span class="sxs-lookup"><span data-stu-id="70426-127">IF Discount > 0</span></span>  
  
 <span data-ttu-id="70426-128">ARDINDAN CalculateTotal (sipariş değeri olarak, indirim)</span><span class="sxs-lookup"><span data-stu-id="70426-128">THEN CalculateTotal(OrderValue, Discount)</span></span>  
  
 <span data-ttu-id="70426-129">BAŞKA toplam sipariş değeri olarak =</span><span class="sxs-lookup"><span data-stu-id="70426-129">ELSE Total = OrderValue</span></span>  
  
 <span data-ttu-id="70426-130">**ErrorTotalRule:**</span><span class="sxs-lookup"><span data-stu-id="70426-130">**ErrorTotalRule:**</span></span>  
  
 <span data-ttu-id="70426-131">Eğer toplam \< 0</span><span class="sxs-lookup"><span data-stu-id="70426-131">IF Total \< 0</span></span>  
  
 <span data-ttu-id="70426-132">ARDINDAN, hata = "ErrorTotalRule harekete"; Durdurma</span><span class="sxs-lookup"><span data-stu-id="70426-132">THEN Error = "Fired ErrorTotalRule"; Halt</span></span>  
  
 <span data-ttu-id="70426-133">Kural değerlendirmesi ve yürütme, ayrıca izleme ve izleme görülebilir.</span><span class="sxs-lookup"><span data-stu-id="70426-133">Rule evaluation and execution can also be seen through tracing and tracking.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="70426-134">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="70426-134">To build the sample</span></span>  
  
1.  <span data-ttu-id="70426-135">Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70426-135">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="70426-136">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70426-136">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="70426-137">CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70426-137">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="70426-138">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="70426-138">To run the sample</span></span>  
  
-   <span data-ttu-id="70426-139">SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını AdvancedPolicy\bin\debug klasöre (veya Visual Basic sürümünü AdvancedPolicy \bin klasörünü) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="70426-139">In the SDK Command Prompt window, run the .exe file in the AdvancedPolicy\bin\debug folder (or the AdvancedPolicy \bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70426-140">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="70426-140">The samples may already be installed on your computer.</span></span> <span data-ttu-id="70426-141">Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:</span><span class="sxs-lookup"><span data-stu-id="70426-141">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="70426-142">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="70426-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70426-143">Bu örnek, şu dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="70426-143">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\AdvancedPolicy`  
  
## <a name="see-also"></a><span data-ttu-id="70426-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70426-144">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [<span data-ttu-id="70426-145">Basit İlke</span><span class="sxs-lookup"><span data-stu-id="70426-145">Simple Policy</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/simple-policy.md)
