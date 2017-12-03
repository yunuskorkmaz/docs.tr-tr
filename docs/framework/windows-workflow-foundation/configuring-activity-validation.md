---
title: "Etkinlik doğrulama yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 440f3ee85fe24707c6bb433736bf6104d9e0dfc5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="f51ef-102">Etkinlik doğrulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f51ef-102">Configuring Activity Validation</span></span>
<span data-ttu-id="f51ef-103">Etkinlik yazarlar ve kullanıcıları tanımlamak ve hataları yürütülmesinin önce bir etkinliğin yapılandırmasında raporlar etkinlik doğrulamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f51ef-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="f51ef-104">Etkinlik doğrulama aşağıdaki üç türlerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="f51ef-104"> provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="f51ef-105">`RequiredArgument`ve `OverloadGroup` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="f51ef-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="f51ef-106">Kesinlik temelli kod tabanlı doğrulama.</span><span class="sxs-lookup"><span data-stu-id="f51ef-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="f51ef-107">Bildirim temelli kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="f51ef-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="f51ef-108">`RequiredArgument`ve `OverloadGroup` öznitelikleri gösteren bir etkinlikte bazı bağımsız değişkenler zorunludur.</span><span class="sxs-lookup"><span data-stu-id="f51ef-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="f51ef-109">Kesinlik temelli kod tabanlı doğrulama kendisi hakkında doğrulama sağlamak bir etkinlik için basit bir yol sağlar ve doğrulama ve etkinliğini içeren iş akışı ile ilişkisini hakkında bildirim temelli kısıtlamalarını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f51ef-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="f51ef-110">Bir etkinlik doğrulama gereksinimlerine göre düzgün şekilde yapılandırılmazsa, doğrulama hataları ve Uyarıları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f51ef-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="f51ef-111">İş Akışı Tasarımcısı'nı kullanarak içeren iş akışı oluşturduysanız, doğrulama hataları ve Uyarıları Tasarımcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f51ef-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="f51ef-112">İş akışını iş akışı Tasarımcısı dışında oluşturulursa, iş akışı çalıştırıldığında herhangi bir doğrulama hatası döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f51ef-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="f51ef-113">İş akışının nasıl oluşturulduğuna bakılmaksızın, doğrulama hataları içeren bir iş akışının asla yürütmek için izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="f51ef-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="f51ef-114">Bu bölümde, bu tür etkinlik doğrulama ve etkinlik doğrulama nasıl çağrıldığını genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="f51ef-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f51ef-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f51ef-115">In This Section</span></span>  
 [<span data-ttu-id="f51ef-116">Gerekli bağımsız değişkenleri ve aşırı grupları</span><span class="sxs-lookup"><span data-stu-id="f51ef-116">Required Arguments and Overload Groups</span></span>](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md)  
 <span data-ttu-id="f51ef-117">Nasıl kullanılacağını açıklar `RequiredArgument` ve `OverloadGroup` doğrulama sağlamak için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="f51ef-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="f51ef-118">Kesinlik temelli kod tabanlı doğrulama</span><span class="sxs-lookup"><span data-stu-id="f51ef-118">Imperative Code-Based Validation</span></span>](../../../docs/framework/windows-workflow-foundation/imperative-code-based-validation.md)  
 <span data-ttu-id="f51ef-119">Kod tabanlı doğrulama için kullanılacak açıklar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> etkinlikleri tabanlı.</span><span class="sxs-lookup"><span data-stu-id="f51ef-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="f51ef-120">Bildirim temelli kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="f51ef-120">Declarative Constraints</span></span>](../../../docs/framework/windows-workflow-foundation/declarative-constraints.md)  
 <span data-ttu-id="f51ef-121">Bildirim temelli kısıtlamaları karmaşık etkinlik doğrulama sağlamak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f51ef-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="f51ef-122">Etkinlik doğrulama çağırma</span><span class="sxs-lookup"><span data-stu-id="f51ef-122">Invoking Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)  
 <span data-ttu-id="f51ef-123">Etkinlik doğrulama otomatik olarak ne zaman çağrılır ve açıkça doğrulamayı çağırmak nasıl anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f51ef-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f51ef-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f51ef-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f51ef-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f51ef-125">Related Sections</span></span>
