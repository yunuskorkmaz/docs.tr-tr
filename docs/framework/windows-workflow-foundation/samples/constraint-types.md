---
title: Kısıtlama türleri
ms.date: 03/30/2017
ms.assetid: b6b246e6-1130-4698-9625-c5c42abcbfed
ms.openlocfilehash: 202a2c7b3a3fc400552e42c8606457964af66af2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506618"
---
# <a name="constraint-types"></a><span data-ttu-id="5ad86-102">Kısıtlama türleri</span><span class="sxs-lookup"><span data-stu-id="5ad86-102">Constraint Types</span></span>
<span data-ttu-id="5ad86-103">Bu örnek, bir iş akışı kısıtlamaları uygulamak için iki farklı yol gösterir, bir etkinlik içinde (derleme) arasındadır ve bir gelen dışında (ilke) olur.</span><span class="sxs-lookup"><span data-stu-id="5ad86-103">This sample shows two different ways to apply constraints to a workflow, one is from inside the activity (build) and one is from outside of it (policy).</span></span> <span data-ttu-id="5ad86-104">Bu senaryoda, bir etkinlik yazar (şirketten 3rth taraf yazılım) iki bağımsız değişken arasındaki ilişkiyi doğrulamak istiyor.</span><span class="sxs-lookup"><span data-stu-id="5ad86-104">In this scenario, an activity author (from a 3rth-party software company) wants to validate the relationship between two arguments.</span></span> <span data-ttu-id="5ad86-105">Bu durumda, maliyet fiyatına eşit veya değerinden küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ad86-105">In this case, the cost should be smaller than or equal to the price.</span></span> <span data-ttu-id="5ad86-106">Genel bir doğrulama yapı kısıtlaması budur.</span><span class="sxs-lookup"><span data-stu-id="5ad86-106">This is a general validation build constraint.</span></span>  
  
 <span data-ttu-id="5ad86-107">Ardından bu genel etkinlik bazı doğrulama eklemek bir Atölye sahibi istiyor.</span><span class="sxs-lookup"><span data-stu-id="5ad86-107">Then a shop owner wants to add some validation to this generic activity.</span></span> <span data-ttu-id="5ad86-108">Bu durumda, çoğu ürünlerinden $9.99 olması veya daha az istediği.</span><span class="sxs-lookup"><span data-stu-id="5ad86-108">In his case, he wants the majority of its products to be $9.99 or less.</span></span> <span data-ttu-id="5ad86-109">Bu nedenle, üstünde olan bir ilke kısıtlaması kullandığı `CreateProduct` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="5ad86-109">So, he uses a policy constraint that is on top of the `CreateProduct` activity.</span></span>  
  
 <span data-ttu-id="5ad86-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5ad86-110">In the sample:</span></span>  
  
 <span data-ttu-id="5ad86-111">Etkinlik yazar (derleme) gerekir:</span><span class="sxs-lookup"><span data-stu-id="5ad86-111">The activity author (build) must:</span></span>  
  
-   <span data-ttu-id="5ad86-112">Kısıtlama oluşturma (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="5ad86-112">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="5ad86-113">Doğrulama mantığını bulunduğu budur.</span><span class="sxs-lookup"><span data-stu-id="5ad86-113">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="5ad86-114">Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama ekleyin (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="5ad86-114">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="5ad86-115">İş akışı yazar (ilke) gerekir:</span><span class="sxs-lookup"><span data-stu-id="5ad86-115">The workflow author (policy) must:</span></span>  
  
-   <span data-ttu-id="5ad86-116">Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="5ad86-116">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="5ad86-117">Kısıtlama oluşturma (`MaxPrice`).</span><span class="sxs-lookup"><span data-stu-id="5ad86-117">Create a constraint (`MaxPrice`).</span></span>  
  
-   <span data-ttu-id="5ad86-118">Oluşturma bir <xref:System.Activities.Validation.ValidationSettings> örneği (`validationSettings`) ve kısıtlama ekleyin (`MaxPrice`) koleksiyonuna `AdditionalConstraints`.</span><span class="sxs-lookup"><span data-stu-id="5ad86-118">Create a <xref:System.Activities.Validation.ValidationSettings> instance (`validationSettings`) and add the constraint (`MaxPrice`) to the collection `AdditionalConstraints`.</span></span> <span data-ttu-id="5ad86-119">Burada iş akışı Yazar ilke kısıtlamaları sıralı veya paralel gibi herhangi bir etkinlik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ad86-119">Here the workflow author can add policy constraints to any activity, such as a sequence or parallel.</span></span>  
  
-   <span data-ttu-id="5ad86-120">Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonunu <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5ad86-120">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
-   <span data-ttu-id="5ad86-121">(İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5ad86-121">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ad86-122">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5ad86-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5ad86-123">ConstraintTypes.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5ad86-123">Open the ConstraintTypes.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5ad86-124">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5ad86-124">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5ad86-125">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5ad86-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ad86-126">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5ad86-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5ad86-127">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5ad86-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ad86-128">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5ad86-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Validation\ConstraintLibrary`