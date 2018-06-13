---
title: Temel doğrulama
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: db7db339d0b7bfd756d8ba22fb8488b8f7ecfa3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514095"
---
# <a name="basic-validation"></a><span data-ttu-id="46abb-102">Temel doğrulama</span><span class="sxs-lookup"><span data-stu-id="46abb-102">Basic Validation</span></span>
<span data-ttu-id="46abb-103">Bu örnek bir etkinliğin oluşur `CreateProduct`, hangi doğrular, kendi `Cost` bağımsız değişkeni ' den küçük veya eşit kendi `Price` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="46abb-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="46abb-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="46abb-104">Sample Details</span></span>  
 <span data-ttu-id="46abb-105">Doğrulama, (doğrulama mantığını etkinliği oluşturur) etkinlik yazar ve belirli bir iş akışında doğrulama hizmetlerini çağıran iş akışı yazarı kullanan iki yazarlar vardır.</span><span class="sxs-lookup"><span data-stu-id="46abb-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="46abb-106">Bu senaryoda, etkinlik Yazar kendi etkinliği her örneği fiyat daha küçük veya buna eşit maliyet olmalıdır yaptırmak istiyor.</span><span class="sxs-lookup"><span data-stu-id="46abb-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="46abb-107">Etkinlik yazarın (iç etkinliği) gerekir:</span><span class="sxs-lookup"><span data-stu-id="46abb-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="46abb-108">Kısıtlama oluşturma (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="46abb-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="46abb-109">Tüm doğrulama mantığını bulunduğu budur.</span><span class="sxs-lookup"><span data-stu-id="46abb-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="46abb-110">Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama eklemek (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="46abb-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="46abb-111">İş akışı yazarı (ana programı) gerekir:</span><span class="sxs-lookup"><span data-stu-id="46abb-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="46abb-112">Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="46abb-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="46abb-113">Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="46abb-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="46abb-114">(İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="46abb-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="46abb-115">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="46abb-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="46abb-116">BasicValidation.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46abb-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="46abb-117">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="46abb-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46abb-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="46abb-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="46abb-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="46abb-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46abb-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="46abb-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46abb-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="46abb-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`