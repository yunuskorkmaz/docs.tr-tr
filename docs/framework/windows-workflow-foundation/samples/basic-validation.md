---
title: Temel doğrulama
ms.date: 03/30/2017
ms.assetid: ba1343cc-aaab-4ade-b0c0-1dd5063bf4ad
ms.openlocfilehash: 74d99e2d426e9ea5701fad80418fdf019112cc9e
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332739"
---
# <a name="basic-validation"></a><span data-ttu-id="9564a-102">Temel doğrulama</span><span class="sxs-lookup"><span data-stu-id="9564a-102">Basic Validation</span></span>
<span data-ttu-id="9564a-103">Bu örnek bir etkinliğin oluşur `CreateProduct`, hangi doğrular, kendi `Cost` değerinden küçük veya eşit olmayan bağımsız değişken, `Price` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="9564a-103">This sample consists of an activity, `CreateProduct`, which validates that its `Cost` argument is smaller than or equal to its `Price` argument.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9564a-104">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="9564a-104">Sample Details</span></span>  
 <span data-ttu-id="9564a-105">Doğrulama, etkinlik yazar (etkinlik için doğrulama mantığını oluşturur) ve belirli bir iş akışı doğrulama hizmetleri çağıran iş akışı Yazar kullanan iki yazarlar vardır.</span><span class="sxs-lookup"><span data-stu-id="9564a-105">There are two authors that use validation, the activity author (creates the validation logic for the activity) and the workflow author that calls validation services on a specific workflow.</span></span> <span data-ttu-id="9564a-106">Bu senaryoda, etkinlik yazarı her örnek kendi etkinlik fiyatının daha küçük veya buna eşit maliyet olmalıdır uygulamak istiyor.</span><span class="sxs-lookup"><span data-stu-id="9564a-106">In this scenario, the activity author wants to enforce that every instance of his activity must have a smaller or equal cost than that of the price.</span></span>  
  
 <span data-ttu-id="9564a-107">Etkinlik yazar (içinde etkinliği) gerekir:</span><span class="sxs-lookup"><span data-stu-id="9564a-107">The activity author (inside the activity) must:</span></span>  
  
-   <span data-ttu-id="9564a-108">Kısıtlama oluşturma (`PriceGreaterThanCost`).</span><span class="sxs-lookup"><span data-stu-id="9564a-108">Create a constraint (`PriceGreaterThanCost`).</span></span> <span data-ttu-id="9564a-109">Doğrulama mantığını bulunduğu budur.</span><span class="sxs-lookup"><span data-stu-id="9564a-109">This is where all the validation logic resides.</span></span>  
  
-   <span data-ttu-id="9564a-110">Geçersiz kılma `System.Activities.CodeActivity.OnGetConstraints()` ve kısıtlama ekleyin (`PriceGreaterThanCost`) kısıtlamaları için <xref:System.Collections.IList>.</span><span class="sxs-lookup"><span data-stu-id="9564a-110">Override `System.Activities.CodeActivity.OnGetConstraints()` and add the constraint (`PriceGreaterThanCost`) to the constraints <xref:System.Collections.IList>.</span></span>  
  
 <span data-ttu-id="9564a-111">İş akışı yazar (ana program) gerekir:</span><span class="sxs-lookup"><span data-stu-id="9564a-111">The workflow author (main program) must:</span></span>  
  
-   <span data-ttu-id="9564a-112">Bir iş akışı etkinlik doğrulamak için bir örneğini oluşturun (`CreateProduct`).</span><span class="sxs-lookup"><span data-stu-id="9564a-112">Create a workflow with an instance of the activity to validate (`CreateProduct`).</span></span>  
  
-   <span data-ttu-id="9564a-113">Çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonunu <xref:System.Activities.Validation.ValidationError>.</span><span class="sxs-lookup"><span data-stu-id="9564a-113">Call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.ValidationError>.</span></span>  
  
-   <span data-ttu-id="9564a-114">(İsteğe bağlı) Yazdırma <xref:System.Activities.Validation.ValidationError> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9564a-114">(Optional) Print the <xref:System.Activities.Validation.ValidationError> objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9564a-115">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9564a-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9564a-116">BasicValidation.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9564a-116">Open the BasicValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="9564a-117">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9564a-117">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9564a-118">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="9564a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9564a-119">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9564a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9564a-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9564a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9564a-121">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9564a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\BasicValidation`