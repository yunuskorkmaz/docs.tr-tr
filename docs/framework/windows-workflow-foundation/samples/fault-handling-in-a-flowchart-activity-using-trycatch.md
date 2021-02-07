---
description: 'Daha fazla bilgi edinin: bir akış çizelgesi etkinliğinde TryCatch kullanarak hata Işleme'
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 9ab323117e5b26696a07624117e8acc8c0beacff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755358"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="5a207-103">TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="5a207-103">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="5a207-104">Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a207-104">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="5a207-105">Bu örnekte, promosyon kodu ve alt öğe sayısı, <xref:System.Activities.Statements.Flowchart> promosyon koduna karşılık gelen formüle göre bir iskontoyu hesaplayan bir etkinliğe değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5a207-105">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="5a207-106">Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a207-106">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="5a207-107">Aşağıdaki tabloda etkinlik değişkenlerinin ayrıntıları verilmiştir `CreateFlowchartWithFaults` .</span><span class="sxs-lookup"><span data-stu-id="5a207-107">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="5a207-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a207-108">Parameters</span></span>|<span data-ttu-id="5a207-109">Description</span><span class="sxs-lookup"><span data-stu-id="5a207-109">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="5a207-110">promoCode</span><span class="sxs-lookup"><span data-stu-id="5a207-110">promoCode</span></span>|<span data-ttu-id="5a207-111">Promosyon kodu.</span><span class="sxs-lookup"><span data-stu-id="5a207-111">The promotion code.</span></span> <span data-ttu-id="5a207-112">Türü: Dize</span><span class="sxs-lookup"><span data-stu-id="5a207-112">Type: String</span></span><br /><br /> <span data-ttu-id="5a207-113">Parantez içinde Açıklama içeren olası değerler:</span><span class="sxs-lookup"><span data-stu-id="5a207-113">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="5a207-114">-Tek (tek)</span><span class="sxs-lookup"><span data-stu-id="5a207-114">-   Single (Single)</span></span><br /><span data-ttu-id="5a207-115">-MNK (çocuk olmadan evli.)</span><span class="sxs-lookup"><span data-stu-id="5a207-115">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="5a207-116">-MWK (çocuklarla evli)</span><span class="sxs-lookup"><span data-stu-id="5a207-116">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="5a207-117">numKids</span><span class="sxs-lookup"><span data-stu-id="5a207-117">numKids</span></span>|<span data-ttu-id="5a207-118">Alt öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="5a207-118">The number of children.</span></span> <span data-ttu-id="5a207-119">Tür: int</span><span class="sxs-lookup"><span data-stu-id="5a207-119">Type: int</span></span>|

<span data-ttu-id="5a207-120">`CreateFlowchartWithFaults`Etkinlik, <xref:System.Activities.Statements.FlowSwitch%601> `promoCode` bağımsız değişkene geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan bir etkinlik kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a207-120">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="5a207-121">Değeri `promoCode`</span><span class="sxs-lookup"><span data-stu-id="5a207-121">Value of `promoCode`</span></span>|<span data-ttu-id="5a207-122">İndirim (%)</span><span class="sxs-lookup"><span data-stu-id="5a207-122">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="5a207-123">Tek</span><span class="sxs-lookup"><span data-stu-id="5a207-123">Single</span></span>|<span data-ttu-id="5a207-124">10</span><span class="sxs-lookup"><span data-stu-id="5a207-124">10</span></span>|
|<span data-ttu-id="5a207-125">MNK</span><span class="sxs-lookup"><span data-stu-id="5a207-125">MNK</span></span>|<span data-ttu-id="5a207-126">15</span><span class="sxs-lookup"><span data-stu-id="5a207-126">15</span></span>|
|<span data-ttu-id="5a207-127">MWK</span><span class="sxs-lookup"><span data-stu-id="5a207-127">MWK</span></span>|<span data-ttu-id="5a207-128">15 + (1 – 1/ `numberOfKids` ) \* 10 **Note:**  potansiyel olarak bu hesaplama bir oluşturabilir <xref:System.DivideByZeroException> .</span><span class="sxs-lookup"><span data-stu-id="5a207-128">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="5a207-129">Bu nedenle, indirim hesaplaması <xref:System.Activities.Statements.TryCatch> özel durumu yakalayan bir etkinliğe sarmalanır <xref:System.DivideByZeroException> ve iskontoyu sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5a207-129">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="5a207-130">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5a207-130">To use this sample</span></span>

1. <span data-ttu-id="5a207-131">Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="5a207-131">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="5a207-132">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="5a207-132">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="5a207-133">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="5a207-133">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a207-134">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a207-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5a207-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5a207-135">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5a207-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5a207-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a207-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5a207-137">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="5a207-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a207-138">See also</span></span>

- [<span data-ttu-id="5a207-139">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="5a207-139">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="5a207-140">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5a207-140">Exceptions</span></span>](../exceptions.md)
