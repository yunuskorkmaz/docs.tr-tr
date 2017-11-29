---
title: "Temel doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d388b3d6acad28e4ff952f72aa64a607d745f307
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-validation"></a><span data-ttu-id="b5990-102">Temel doğrulama</span><span class="sxs-lookup"><span data-stu-id="b5990-102">Basic Validation</span></span>
<span data-ttu-id="b5990-103">Bu örnek bir etkinliğin oluşur `CreateProduct`, hangi doğrular, kendi `Cost` bağımsız değişkeni ' den küçük veya eşit kendi `Price` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="b5990-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b5990-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b5990-104">Sample Details</span></span>  
 <span data-ttu-id="b5990-105">Doğrulama, (doğrulama mantığını etkinliği oluşturur) etkinlik yazar ve belirli bir iş akışında doğrulama hizmetlerini çağıran iş akışı yazarı kullanan iki yazarlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b5990-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="b5990-106">Bu senaryoda, etkinlik Yazar kendi etkinliği her örneği fiyat daha küçük veya buna eşit maliyet olmalıdır yaptırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="b5990-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="b5990-107">Etkinlik yazarın (iç etkinliği) gerekir:</span><span class="sxs-lookup"><span data-stu-id="b5990-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="b5990-108">Kısıtlama oluşturma (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="b5990-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="b5990-109">Tüm doğrulama mantığını bulunduğu budur.</span><span class="sxs-lookup"><span data-stu-id="b5990-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="b5990-110">Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama eklemek (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="b5990-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="b5990-111">İş akışı yazarı (ana programı) gerekir:</span><span class="sxs-lookup"><span data-stu-id="b5990-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="b5990-112">Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="b5990-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="b5990-113">Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="b5990-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="b5990-114">(İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b5990-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5990-115">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b5990-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b5990-116">BasicValidation.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b5990-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b5990-117">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b5990-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5990-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5990-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5990-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b5990-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5990-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b5990-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5990-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b5990-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b5990-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b5990-122">See Also</span></span>
