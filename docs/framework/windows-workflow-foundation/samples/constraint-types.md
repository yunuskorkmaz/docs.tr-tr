---
title: "Kısıtlama türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d42be018b6a92237b5914c180d329138fb95e7dc
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="constraint-types"></a><span data-ttu-id="79489-102">Kısıtlama türleri</span><span class="sxs-lookup"><span data-stu-id="79489-102">Constraint Types</span></span>
<span data-ttu-id="79489-103">Bu örnek bir iş akışına kısıtlamaları uygulamak için iki farklı yollar gösterir, bir gelen (yapı) etkinliği içinde ve bir gelen dışında (ilke) olur.</span><span class="sxs-lookup"><span data-stu-id="79489-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="79489-104">Bu senaryoda, iki bağımsız değişkenler arasındaki ilişkiyi doğrulamak bir etkinlik yazar (3rth taraf yazılım şirketten) ister.</span><span class="sxs-lookup"><span data-stu-id="79489-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="79489-105">Bu durumda, maliyet fiyatına eşit veya daha küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="79489-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="79489-106">Genel doğrulama yapı kısıtlaması budur.</span><span class="sxs-lookup"><span data-stu-id="79489-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="79489-107">Ardından bir alışveriş sahibi bazı doğrulama Bu genel etkinlik eklemek istiyor.</span><span class="sxs-lookup"><span data-stu-id="79489-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="79489-108">Bu durumda, çoğu $9.99 olmasını ürünlerinde veya daha az istediği.</span><span class="sxs-lookup"><span data-stu-id="79489-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="79489-109">Bu nedenle, kendisinin üstünde olan bir ilke kısıtlaması kullanan `CreateProduct` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="79489-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="79489-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="79489-110">In the sample:</span></span>  
  
 <span data-ttu-id="79489-111">Etkinlik yazar (yapı) gerekir:</span><span class="sxs-lookup"><span data-stu-id="79489-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="79489-112">Kısıtlama oluşturma (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="79489-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="79489-113">Tüm doğrulama mantığını bulunduğu budur.</span><span class="sxs-lookup"><span data-stu-id="79489-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="79489-114">Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama eklemek (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="79489-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="79489-115">İş akışı yazarı (ilke) gerekir:</span><span class="sxs-lookup"><span data-stu-id="79489-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="79489-116">Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="79489-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="79489-117">Kısıtlama oluşturma (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="79489-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="79489-118">Oluşturma bir <xref:System.Activities.Validation.ValidationSettings> örneği (`validationSettings`) ve kısıtlama eklemek (`MaxPrice`) koleksiyonuna `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="79489-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="79489-119">Burada iş akışı yazarı ilke kısıtlamaları dizisi veya paralel gibi herhangi bir etkinlik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79489-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="79489-120">Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="79489-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="79489-121">(İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="79489-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="79489-122">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="79489-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="79489-123">ConstraintTypes.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79489-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="79489-124">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="79489-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79489-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="79489-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="79489-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="79489-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79489-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="79489-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79489-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="79489-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`