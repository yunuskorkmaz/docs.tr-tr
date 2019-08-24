---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016027"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="50475-102">TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="50475-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>

<span data-ttu-id="50475-103">Bu örnek, <xref:System.Activities.Statements.TryCatch> etkinliğin karmaşık bir denetim akışı etkinliği içinde nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="50475-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

<span data-ttu-id="50475-104">Bu örnekte, promosyon kodu ve alt öğe sayısı, promosyon koduna karşılık gelen formüle göre bir <xref:System.Activities.Statements.Flowchart> iskontoyu hesaplayan bir etkinliğe değişken olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="50475-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="50475-105">Örnek, örneğin, örnek kod ve iş akışı Tasarımcısı sürümlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="50475-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

<span data-ttu-id="50475-106">Aşağıdaki tabloda `CreateFlowchartWithFaults` etkinlik değişkenlerinin ayrıntıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="50475-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="50475-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50475-107">Parameters</span></span>|<span data-ttu-id="50475-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50475-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="50475-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="50475-109">promoCode</span></span>|<span data-ttu-id="50475-110">Promosyon kodu.</span><span class="sxs-lookup"><span data-stu-id="50475-110">The promotion code.</span></span> <span data-ttu-id="50475-111">Tür: Dize</span><span class="sxs-lookup"><span data-stu-id="50475-111">Type: String</span></span><br /><br /> <span data-ttu-id="50475-112">Parantez içinde Açıklama içeren olası değerler:</span><span class="sxs-lookup"><span data-stu-id="50475-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="50475-113">-Tek (tek)</span><span class="sxs-lookup"><span data-stu-id="50475-113">-   Single (Single)</span></span><br /><span data-ttu-id="50475-114">-MNK (çocuk olmadan evli.)</span><span class="sxs-lookup"><span data-stu-id="50475-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="50475-115">-MWK (çocuklarla evli)</span><span class="sxs-lookup"><span data-stu-id="50475-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="50475-116">numKids</span><span class="sxs-lookup"><span data-stu-id="50475-116">numKids</span></span>|<span data-ttu-id="50475-117">Alt öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="50475-117">The number of children.</span></span> <span data-ttu-id="50475-118">Tür: int</span><span class="sxs-lookup"><span data-stu-id="50475-118">Type: int</span></span>|

<span data-ttu-id="50475-119">Etkinlik, `promoCode` bağımsız değişkene <xref:System.Activities.Statements.FlowSwitch%601> geçiş yapan ve aşağıdaki formülü kullanarak indirimi hesaplayan bir etkinlik kullanır. `CreateFlowchartWithFaults`</span><span class="sxs-lookup"><span data-stu-id="50475-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="50475-120">Değeri`promoCode`</span><span class="sxs-lookup"><span data-stu-id="50475-120">Value of `promoCode`</span></span>|<span data-ttu-id="50475-121">İndirim (%)</span><span class="sxs-lookup"><span data-stu-id="50475-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="50475-122">Tek</span><span class="sxs-lookup"><span data-stu-id="50475-122">Single</span></span>|<span data-ttu-id="50475-123">10</span><span class="sxs-lookup"><span data-stu-id="50475-123">10</span></span>|
|<span data-ttu-id="50475-124">MNK</span><span class="sxs-lookup"><span data-stu-id="50475-124">MNK</span></span>|<span data-ttu-id="50475-125">15</span><span class="sxs-lookup"><span data-stu-id="50475-125">15</span></span>|
|<span data-ttu-id="50475-126">MWK</span><span class="sxs-lookup"><span data-stu-id="50475-126">MWK</span></span>|<span data-ttu-id="50475-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potansiyel olarak, bu hesaplama bir <xref:System.DivideByZeroException>oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="50475-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="50475-128">Bu nedenle, indirim hesaplaması <xref:System.Activities.Statements.TryCatch> <xref:System.DivideByZeroException> özel durumu yakalayan bir etkinliğe sarmalanır ve iskontoyu sıfıra ayarlar.</span><span class="sxs-lookup"><span data-stu-id="50475-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="50475-129">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="50475-129">To use this sample</span></span>

1. <span data-ttu-id="50475-130">Visual Studio 2010 kullanarak FlowchartWithFaultHandling. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="50475-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2. <span data-ttu-id="50475-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="50475-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="50475-132">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="50475-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="50475-133">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="50475-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="50475-134">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="50475-134">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="50475-135">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="50475-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50475-136">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="50475-136">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a><span data-ttu-id="50475-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50475-137">See also</span></span>

- [<span data-ttu-id="50475-138">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="50475-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="50475-139">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="50475-139">Exceptions</span></span>](../exceptions.md)
