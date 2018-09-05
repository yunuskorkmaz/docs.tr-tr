---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514142"
---
# <a name="overloadgroups"></a><span data-ttu-id="848fa-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="848fa-102">OverloadGroups</span></span>
<span data-ttu-id="848fa-103">Bu örnek bir etkinlik içerir (`CreateLocation`), iki ilginç özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="848fa-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="848fa-104">Bazı bağımsız değişkenler ve bazı isteğe bağlı vm'lere zorunludur.</span><span class="sxs-lookup"><span data-stu-id="848fa-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="848fa-105">Bunu iki farklı kümesinden bağımsız değişken sağlamayı tercih izin verir.</span><span class="sxs-lookup"><span data-stu-id="848fa-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="848fa-106">Bu davranış, bu iki özelliği kullanılarak gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="848fa-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="848fa-107">`[isRequired]` ata, belirli bir etkinliğe özelliğidir ve aksi durumda, bir özel durum oluşturur. doğrular.</span><span class="sxs-lookup"><span data-stu-id="848fa-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="848fa-108">`[OverloadGroup]` Kullanıcı etkinliğinin bir küme veya başka bir kullanma arasında seçebilmeniz birlikte bir dizi bağımsız değişken geçirir.</span><span class="sxs-lookup"><span data-stu-id="848fa-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="848fa-109">Kullanıcı, farklı gruplardan aşırı yükleme bağımsız değişkenleri aynı örneğinde kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="848fa-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="848fa-110">Farklı iş akışlarını ayarladıktan sonra çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonunu <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="848fa-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="848fa-111">Yazdırma <xref:System.Activities.Validation.Constraint> konsola nesneleri.</span><span class="sxs-lookup"><span data-stu-id="848fa-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="848fa-112">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="848fa-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="848fa-113">Açık **OverloadGroups.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="848fa-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="848fa-114">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="848fa-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="848fa-115">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="848fa-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="848fa-116">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="848fa-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="848fa-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="848fa-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="848fa-118">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="848fa-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
