---
title: "TryCatch kullanarak akış etkinliğinde işleme hatası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a179ae5aaca959383a88105b96cbba2cebd1919
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="2488e-102">TryCatch kullanarak akış etkinliğinde işleme hatası</span><span class="sxs-lookup"><span data-stu-id="2488e-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="2488e-103">Bu örnek göstermektedir nasıl <xref:System.Activities.Statements.TryCatch> etkinlik karmaşık denetim akışı etkinliği içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2488e-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="2488e-104">Bu örnekte, bir promosyon kodu ve alt sayısını değişkenleri olarak geçirilir bir <xref:System.Activities.Statements.Flowchart> promosyon kodu karşılık gelen formül temelinde bir hesaplar etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2488e-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="2488e-105">Örnek kesinlik temelli kodu ve iş akışı Tasarımcısı sürümlerini örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="2488e-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="2488e-106">Aşağıdaki tabloda değişkenleri ayrıntıları `CreateFlowchartWithFaults` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="2488e-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="2488e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2488e-107">Parameters</span></span>|<span data-ttu-id="2488e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2488e-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="2488e-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="2488e-109">promoCode</span></span>|<span data-ttu-id="2488e-110">Promosyon kodu.</span><span class="sxs-lookup"><span data-stu-id="2488e-110">The promotion code.</span></span> <span data-ttu-id="2488e-111">Türü: dize</span><span class="sxs-lookup"><span data-stu-id="2488e-111">Type: String</span></span><br /><br /> <span data-ttu-id="2488e-112">Parantez içindeki açıklamasıyla olası değerler:</span><span class="sxs-lookup"><span data-stu-id="2488e-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="2488e-113">-Tek (tek)</span><span class="sxs-lookup"><span data-stu-id="2488e-113">-   Single (Single)</span></span><br /><span data-ttu-id="2488e-114">-MNK (Evli ile Çocuğunuz yok.)</span><span class="sxs-lookup"><span data-stu-id="2488e-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="2488e-115">-MWK (Evli çocuklar ile.)</span><span class="sxs-lookup"><span data-stu-id="2488e-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="2488e-116">numKids</span><span class="sxs-lookup"><span data-stu-id="2488e-116">numKids</span></span>|<span data-ttu-id="2488e-117">Alt öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="2488e-117">The number of children.</span></span> <span data-ttu-id="2488e-118">Tür: int</span><span class="sxs-lookup"><span data-stu-id="2488e-118">Type: int</span></span>|  
  
 <span data-ttu-id="2488e-119">`CreateFlowchartWithFaults` Etkinliği kullanan bir <xref:System.Activities.Statements.FlowSwitch%601> anahtarlarını etkinlik `promoCode` bağımsız değişkeni ve aşağıdaki formülü kullanarak hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2488e-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="2488e-120">Değeri`promoCode`</span><span class="sxs-lookup"><span data-stu-id="2488e-120">Value of `promoCode`</span></span>|<span data-ttu-id="2488e-121">İndirim (%)</span><span class="sxs-lookup"><span data-stu-id="2488e-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="2488e-122">Tek</span><span class="sxs-lookup"><span data-stu-id="2488e-122">Single</span></span>|<span data-ttu-id="2488e-123">10</span><span class="sxs-lookup"><span data-stu-id="2488e-123">10</span></span>|  
|<span data-ttu-id="2488e-124">MNK</span><span class="sxs-lookup"><span data-stu-id="2488e-124">MNK</span></span>|<span data-ttu-id="2488e-125">15</span><span class="sxs-lookup"><span data-stu-id="2488e-125">15</span></span>|  
|<span data-ttu-id="2488e-126">MWK</span><span class="sxs-lookup"><span data-stu-id="2488e-126">MWK</span></span>|<span data-ttu-id="2488e-127">15 + (1-1 /`numberOfKids`)\*10 **Not:** potansiyel olarak, bu hesaplama atabilirsiniz bir <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="2488e-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="2488e-128">İndirim hesaplama, bu nedenle, kaydırılan bir <xref:System.Activities.Statements.TryCatch> yakalar etkinlik <xref:System.DivideByZeroException> özel durumu ve indirim sıfır olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2488e-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2488e-129">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="2488e-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="2488e-130">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], FlowchartWithFaultHandling.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="2488e-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="2488e-131">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2488e-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="2488e-132">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2488e-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2488e-133">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="2488e-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2488e-134">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2488e-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2488e-135">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2488e-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2488e-136">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2488e-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="2488e-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2488e-137">See Also</span></span>  
 [<span data-ttu-id="2488e-138">Akış Çizelgesi İş Akışları</span><span class="sxs-lookup"><span data-stu-id="2488e-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="2488e-139">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="2488e-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
