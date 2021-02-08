---
description: 'Daha fazla bilgi edinin: etkinlik doğrulamasını yapılandırma'
title: Etkinlik Doğrulamayı Yapılandırma
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 9e40842a18dd2afd9a5ec0104d66e8971d691b5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792758"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="ffffb-103">Etkinlik Doğrulamayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffffb-103">Configuring Activity Validation</span></span>

<span data-ttu-id="ffffb-104">Etkinlik doğrulaması, etkinlik yazarlarının ve kullanıcıların, çalıştırmadan önce bir etkinliğin yapılandırmasındaki hataları tanımlamasına ve rapor etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-104">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="ffffb-105">Windows Workflow Foundation (WF), aşağıdaki üç tür etkinlik doğrulaması sağlar:</span><span class="sxs-lookup"><span data-stu-id="ffffb-105">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="ffffb-106">`RequiredArgument` ve `OverloadGroup` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ffffb-106">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="ffffb-107">Kesinlik temelli kod tabanlı doğrulama.</span><span class="sxs-lookup"><span data-stu-id="ffffb-107">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="ffffb-108">Bildirime dayalı kısıtlamalar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-108">Declarative constraints.</span></span>  
  
 <span data-ttu-id="ffffb-109">`RequiredArgument` ve `OverloadGroup` öznitelikleri, bir etkinlikte belirli bağımsız değişkenlerin gerekli olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffffb-109">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="ffffb-110">Zorunlu kod tabanlı doğrulama, bir etkinliğin kendisi hakkında doğrulama sağlaması için basit bir yol sağlar ve bildirim temelli kısıtlamalar, etkinlik ve kapsayan iş akışıyla ilişkisi hakkında doğrulamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="ffffb-110">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="ffffb-111">Bir etkinlik doğrulama gereksinimlerine göre doğru yapılandırılmamışsa, doğrulama hataları ve uyarıları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ffffb-111">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="ffffb-112">İçeren iş akışı, iş akışı Tasarımcısı kullanılarak oluşturulduysa, Tasarımcıda herhangi bir doğrulama hatası ve uyarı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ffffb-112">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="ffffb-113">İş akışı iş akışı Tasarımcısı dışında oluşturulduysa, iş akışı çağrıldığında herhangi bir doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ffffb-113">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="ffffb-114">İş akışının oluşturulma şeklinden bağımsız olarak, doğrulama hataları olan bir iş akışının yürütülmesine hiçbir şekilde izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ffffb-114">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="ffffb-115">Bu bölüm, bu etkinlik doğrulaması türleri ve etkinlik doğrulamasının nasıl çağrılışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-115">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffffb-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ffffb-116">In This Section</span></span>  

 [<span data-ttu-id="ffffb-117">Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar</span><span class="sxs-lookup"><span data-stu-id="ffffb-117">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="ffffb-118">`RequiredArgument`Ve `OverloadGroup` özniteliklerinin doğrulama sağlamak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-118">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="ffffb-119">Kesin Kod Temelli Doğrulama</span><span class="sxs-lookup"><span data-stu-id="ffffb-119">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="ffffb-120"><xref:System.Activities.CodeActivity>Ve tabanlı etkinlikler için kod tabanlı doğrulamanın nasıl kullanılacağını açıklar <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="ffffb-120">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="ffffb-121">Bildirim Temelli Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="ffffb-121">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="ffffb-122">Karmaşık etkinlik doğrulaması sağlamak için bildirim temelli kısıtlamaların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-122">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="ffffb-123">Etkinlik Doğrulamayı Çağırma</span><span class="sxs-lookup"><span data-stu-id="ffffb-123">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="ffffb-124">Etkinlik doğrulamanın otomatik olarak ne zaman çağrılacağını ve doğrulamanın açıkça nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffffb-124">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ffffb-125">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ffffb-125">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ffffb-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="ffffb-126">Related Sections</span></span>
