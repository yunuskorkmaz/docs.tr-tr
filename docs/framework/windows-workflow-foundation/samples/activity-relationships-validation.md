---
title: Etkinlik ilişkileri doğrulama
ms.date: 03/30/2017
ms.assetid: 6f11a34e-ed67-4bce-88ce-7e96bbb4d052
ms.openlocfilehash: e6dd0e6a7b48444073ebae378e21c1b45977a1f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515114"
---
# <a name="activity-relationships-validation"></a><span data-ttu-id="24e6b-102">Etkinlik ilişkileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="24e6b-102">Activity Relationships Validation</span></span>
<span data-ttu-id="24e6b-103">Bu örnek üç etkinliklerinin oluşur `CreateCity`, `CreateState`, ve `CreateCountry`.</span><span class="sxs-lookup"><span data-stu-id="24e6b-103">This sample consists of three activities, `CreateCity`, `CreateState`, and `CreateCountry`.</span></span> <span data-ttu-id="24e6b-104">`CreateCity` içinde olmalıdır bir `CreateState` etkinliği ve `CreateState` içinde olmalıdır bir `CreateCountry` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="24e6b-104">`CreateCity` must be inside a `CreateState` activity, and `CreateState` must be inside a `CreateCountry` activity.</span></span> <span data-ttu-id="24e6b-105">Bu örnek amacıyla kod için doğrulama mantığını bulunduğu `CreateState` etkinliği ve XAML için `CreateCity` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="24e6b-105">For the purpose of this sample, the validation logic is in code for the `CreateState` activity, and in XAML for the `CreateCity` activity.</span></span> <span data-ttu-id="24e6b-106">Her iki kısıtlamaları aynı davranışı sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24e6b-106">Both constraints have the same behavior.</span></span>  
  
 <span data-ttu-id="24e6b-107">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Etkinlikleri arasındaki ilişkileri doğrulamak Geliştirici izin aşağıdaki üç Yardımcısı etkinlikler sağlar:</span><span class="sxs-lookup"><span data-stu-id="24e6b-107">The [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] provides the following three helper activities that allow the developer to validate relationships between activities:</span></span>  
  
 <xref:System.Activities.Validation.GetParentChain>  
 <span data-ttu-id="24e6b-108">Geçerli düğüm üst öğeye ait tüm etkinliklerin koleksiyonunu sağlar</span><span class="sxs-lookup"><span data-stu-id="24e6b-108">Provides the collection of all activities that belong to the parent of the current node</span></span>  
  
 <xref:System.Activities.Validation.GetChildSubtree>  
 <span data-ttu-id="24e6b-109">Geçerli düğüm hariç geçerli düğüm alt ağacına ait tüm etkinliklerin koleksiyonunu sağlar</span><span class="sxs-lookup"><span data-stu-id="24e6b-109">Provides the collection of all activities that belong to the sub-tree of the current node, excluding the current node</span></span>  
  
 <xref:System.Activities.Validation.GetWorkflowTree>  
 <span data-ttu-id="24e6b-110">Geçerli düğüm aynı ağaç tüm etkinliklerin koleksiyonunu sağlar</span><span class="sxs-lookup"><span data-stu-id="24e6b-110">Provides the collection of all activities in the same tree as the current node</span></span>  
  
 <span data-ttu-id="24e6b-111">Örnekte, bir <xref:System.Activities.Statements.ForEach%601> etkinlik tarafından döndürülen koleksiyonunun rehberlik için kullanılan <xref:System.Activities.Validation.GetParentChain>.</span><span class="sxs-lookup"><span data-stu-id="24e6b-111">In the sample, a <xref:System.Activities.Statements.ForEach%601> activity is used to walk through the collection returned by <xref:System.Activities.Validation.GetParentChain>.</span></span> <span data-ttu-id="24e6b-112">Türünü karşılaştırılır koleksiyondaki her öğe için `CreateCountry` (veya `CreateState` varsa `CreateCity` Doğrulanmakta olan), ve ne zaman bir eşleşme bulunduğunda sonuç bayrağı ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="24e6b-112">For every element in the collection, its type is compared to `CreateCountry` (or `CreateState` if `CreateCity` is being validated), and when a match is found the result flag is set to `true`.</span></span> <span data-ttu-id="24e6b-113">Son olarak, bir <xref:System.Activities.Validation.AssertValidation> sonuç bayrağı ayarlanmışsa bir doğrulama hatası oluşturmak için kullanılan `false`.</span><span class="sxs-lookup"><span data-stu-id="24e6b-113">Finally, an <xref:System.Activities.Validation.AssertValidation> is used to generate a validation error if the result flag is set to `false`.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="24e6b-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="24e6b-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="24e6b-115">ContainmentValidation.sln örnek çözümü açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24e6b-115">Open the ContainmentValidation.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="24e6b-116">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="24e6b-116">Build the solution.</span></span>  
  
3.  <span data-ttu-id="24e6b-117">Programını başlatmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="24e6b-117">Press CTRL + F5 to launch the program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24e6b-118">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="24e6b-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="24e6b-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="24e6b-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24e6b-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="24e6b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24e6b-121">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="24e6b-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\ActivityRelationships`
