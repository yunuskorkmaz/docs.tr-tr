---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710830"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="e7da4-102">TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="e7da4-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="e7da4-103">Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğinin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="e7da4-104">Bu örnekte, bir promosyon kodu ve alt öğe sayısı, promosyon koduna karşılık gelen formüle göre bir iskontoyu hesaplayan <xref:System.Activities.Statements.Flowchart> etkinliğe değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="e7da4-105">Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="e7da4-106">Aşağıdaki tabloda `CreateFlowchartWithFaults` etkinliğinin değişkenleri ayrıntılı olarak verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="e7da4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7da4-107">Parameters</span></span>|<span data-ttu-id="e7da4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7da4-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="e7da4-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="e7da4-109">promoCode</span></span>|<span data-ttu-id="e7da4-110">Promosyon kodu.</span><span class="sxs-lookup"><span data-stu-id="e7da4-110">The promotion code.</span></span> <span data-ttu-id="e7da4-111">Tür: dize</span><span class="sxs-lookup"><span data-stu-id="e7da4-111">Type: String</span></span><br /><br /> <span data-ttu-id="e7da4-112">Parantez içinde Açıklama içeren olası değerler:</span><span class="sxs-lookup"><span data-stu-id="e7da4-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="e7da4-113">-Tek (tek)</span><span class="sxs-lookup"><span data-stu-id="e7da4-113">-   Single (Single)</span></span><br /><span data-ttu-id="e7da4-114">-MNK (çocuk olmadan evli.)</span><span class="sxs-lookup"><span data-stu-id="e7da4-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="e7da4-115">-MWK (çocuklarla evli)</span><span class="sxs-lookup"><span data-stu-id="e7da4-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="e7da4-116">numKids</span><span class="sxs-lookup"><span data-stu-id="e7da4-116">numKids</span></span>|<span data-ttu-id="e7da4-117">Alt öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e7da4-117">The number of children.</span></span> <span data-ttu-id="e7da4-118">Tür: int</span><span class="sxs-lookup"><span data-stu-id="e7da4-118">Type: int</span></span>|

<span data-ttu-id="e7da4-119">`CreateFlowchartWithFaults` etkinliği, `promoCode` bağımsız değişkenine geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan <xref:System.Activities.Statements.FlowSwitch%601> etkinliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7da4-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="e7da4-120">`promoCode` değeri</span><span class="sxs-lookup"><span data-stu-id="e7da4-120">Value of `promoCode`</span></span>|<span data-ttu-id="e7da4-121">İndirim (%)</span><span class="sxs-lookup"><span data-stu-id="e7da4-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="e7da4-122">Tek</span><span class="sxs-lookup"><span data-stu-id="e7da4-122">Single</span></span>|<span data-ttu-id="e7da4-123">10</span><span class="sxs-lookup"><span data-stu-id="e7da4-123">10</span></span>|
|<span data-ttu-id="e7da4-124">MNK</span><span class="sxs-lookup"><span data-stu-id="e7da4-124">MNK</span></span>|<span data-ttu-id="e7da4-125">15</span><span class="sxs-lookup"><span data-stu-id="e7da4-125">15</span></span>|
|<span data-ttu-id="e7da4-126">MWK</span><span class="sxs-lookup"><span data-stu-id="e7da4-126">MWK</span></span>|<span data-ttu-id="e7da4-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:** olası, bu hesaplama <xref:System.DivideByZeroException>oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="e7da4-128">Bu nedenle, indirim hesaplaması, <xref:System.DivideByZeroException> özel durumunu yakalayan ve iskontoyu sıfıra ayarlayan bir <xref:System.Activities.Statements.TryCatch> etkinliğine sarmalanır.</span><span class="sxs-lookup"><span data-stu-id="e7da4-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="e7da4-129">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="e7da4-129">To use this sample</span></span>

1. <span data-ttu-id="e7da4-130">Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e7da4-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="e7da4-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="e7da4-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="e7da4-132">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="e7da4-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e7da4-133">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7da4-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e7da4-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e7da4-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e7da4-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e7da4-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7da4-136">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e7da4-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="e7da4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7da4-137">See also</span></span>

- [<span data-ttu-id="e7da4-138">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="e7da4-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="e7da4-139">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="e7da4-139">Exceptions</span></span>](../exceptions.md)
