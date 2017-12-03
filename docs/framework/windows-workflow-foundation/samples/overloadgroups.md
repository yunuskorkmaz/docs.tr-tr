---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f644f09af3ce9e191dc6c5680472de4ef5ab727d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="4206c-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="4206c-102">OverloadGroups</span></span>
<span data-ttu-id="4206c-103">Bu örnek bir etkinliğin oluşur (`CreateLocation`), iki ilginç özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4206c-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="4206c-104">Bu bazı bağımsız değişkenler ve bazı isteğe bağlı olanları istedi.</span><span class="sxs-lookup"><span data-stu-id="4206c-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="4206c-105">Kullanıcının bağımsız değişkenlerinin iki farklı kümesinden sağlamak seçmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="4206c-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="4206c-106">Bu davranışların bu iki özellik kullanılarak gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="4206c-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="4206c-107">`[isRequired]`belirli bir etkinliğe Ata özelliğidir ve aksi durumda, bir özel durum oluşturur doğrular.</span><span class="sxs-lookup"><span data-stu-id="4206c-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="4206c-108">`[OverloadGroup]`bir küme veya başka bir kullanma arasında kullanıcı etkinliğinin seçebilmeleri birlikte bağımsız değişkenleri, bir dizi koyar.</span><span class="sxs-lookup"><span data-stu-id="4206c-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="4206c-109">Kullanıcı farklı gruplardan aşırı yükleme bağımsız değişkenleri aynı örneğinde kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="4206c-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="4206c-110">Farklı iş akışlarını ayarladıktan sonra arama <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonu <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="4206c-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="4206c-111">Yazdırma <xref:System.Activities.Validation.Constraint> konsoluna nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4206c-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4206c-112">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4206c-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4206c-113">Açık **OverloadGroups.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4206c-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="4206c-114">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4206c-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4206c-115">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4206c-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4206c-116">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4206c-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4206c-117">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4206c-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4206c-118">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4206c-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
