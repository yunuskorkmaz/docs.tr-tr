---
title: TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: e515248594088f9888c3488d83d8079ce5d13089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119814"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="09649-102">TryCatch Kullanarak Akış Çizelgesi Etkinliğine Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="09649-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="09649-103">Bu örnek, gösterir nasıl <xref:System.Activities.Statements.TryCatch> etkinliği bir karmaşık denetim akışı etkinliği içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09649-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>

 <span data-ttu-id="09649-104">Bu örnekte, bir promosyon kodu ve alt öğe sayısı için değişkenleri olarak geçirilen bir <xref:System.Activities.Statements.Flowchart> promosyon kodunu için karşılık gelen formüllerini temel bir hesaplar etkinlik.</span><span class="sxs-lookup"><span data-stu-id="09649-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="09649-105">Örnek, kesinlik temelli kod ve iş akışı Tasarımcısı sürümleri örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="09649-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>

 <span data-ttu-id="09649-106">Aşağıdaki tabloda değişkenleri ayrıntıları `CreateFlowchartWithFaults` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="09649-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>

|<span data-ttu-id="09649-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09649-107">Parameters</span></span>|<span data-ttu-id="09649-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09649-108">Description</span></span>|
|----------------|-----------------|
|<span data-ttu-id="09649-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="09649-109">promoCode</span></span>|<span data-ttu-id="09649-110">Promosyon kodu.</span><span class="sxs-lookup"><span data-stu-id="09649-110">The promotion code.</span></span> <span data-ttu-id="09649-111">Tür: Dize</span><span class="sxs-lookup"><span data-stu-id="09649-111">Type: String</span></span><br /><br /> <span data-ttu-id="09649-112">Parantez içindeki açıklama ile olası değerler:</span><span class="sxs-lookup"><span data-stu-id="09649-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="09649-113">-Tek (tek)</span><span class="sxs-lookup"><span data-stu-id="09649-113">-   Single (Single)</span></span><br /><span data-ttu-id="09649-114">-MNK (Evli ile Çocuğunuz yok.)</span><span class="sxs-lookup"><span data-stu-id="09649-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="09649-115">-MWK (çocuk ile Evli.)</span><span class="sxs-lookup"><span data-stu-id="09649-115">-   MWK (Married with kids.)</span></span>|
|<span data-ttu-id="09649-116">numKids</span><span class="sxs-lookup"><span data-stu-id="09649-116">numKids</span></span>|<span data-ttu-id="09649-117">Alt öğelerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="09649-117">The number of children.</span></span> <span data-ttu-id="09649-118">Tür: int</span><span class="sxs-lookup"><span data-stu-id="09649-118">Type: int</span></span>|

 <span data-ttu-id="09649-119">`CreateFlowchartWithFaults` Etkinliği kullanan bir <xref:System.Activities.Statements.FlowSwitch%601> anahtarlarını etkinlik `promoCode` bağımsız değişken ve şu formülü kullanarak hesaplar.</span><span class="sxs-lookup"><span data-stu-id="09649-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>

|<span data-ttu-id="09649-120">Değeri</span><span class="sxs-lookup"><span data-stu-id="09649-120">Value of</span></span> `promoCode`|<span data-ttu-id="09649-121">İndirim (%)</span><span class="sxs-lookup"><span data-stu-id="09649-121">Discount (%)</span></span>|
|--------------------------|--------------------|
|<span data-ttu-id="09649-122">Tek</span><span class="sxs-lookup"><span data-stu-id="09649-122">Single</span></span>|<span data-ttu-id="09649-123">10</span><span class="sxs-lookup"><span data-stu-id="09649-123">10</span></span>|
|<span data-ttu-id="09649-124">MNK</span><span class="sxs-lookup"><span data-stu-id="09649-124">MNK</span></span>|<span data-ttu-id="09649-125">15</span><span class="sxs-lookup"><span data-stu-id="09649-125">15</span></span>|
|<span data-ttu-id="09649-126">MWK</span><span class="sxs-lookup"><span data-stu-id="09649-126">MWK</span></span>|<span data-ttu-id="09649-127">15 + (1-1 /`numberOfKids`)\*10 **Not:**  Bu hesaplama büyük olasılıkla oluşturabilecek bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="09649-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="09649-128">Bu nedenle, indirim hesaplama içinde sarmalanmış bir <xref:System.Activities.Statements.TryCatch> yakalayan etkinlik <xref:System.DivideByZeroException> özel durum ve indirim sıfır olarak ayarlıyor.</span><span class="sxs-lookup"><span data-stu-id="09649-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="09649-129">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="09649-129">To use this sample</span></span>

1.  <span data-ttu-id="09649-130">Visual Studio 2010 kullanarak FlowchartWithFaultHandling.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="09649-130">Using Visual Studio 2010, open the FlowchartWithFaultHandling.sln solution file.</span></span>

2.  <span data-ttu-id="09649-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="09649-131">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="09649-132">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="09649-132">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="09649-133">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="09649-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="09649-134">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="09649-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="09649-135">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="09649-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="09649-136">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="09649-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="09649-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09649-137">See also</span></span>

- [<span data-ttu-id="09649-138">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="09649-138">Flowchart Workflows</span></span>](../flowchart-workflows.md)
- [<span data-ttu-id="09649-139">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="09649-139">Exceptions</span></span>](../exceptions.md)
