---
title: Etkinlik doğrulamayı yapılandırma
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: 65928de1dc8b8d9914648463a136790c7978f53c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704563"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="d7ea2-102">Etkinlik doğrulamayı yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7ea2-102">Configuring Activity Validation</span></span>
<span data-ttu-id="d7ea2-103">Etkinlik yazarlar ve kullanıcıları tanımlama ve yürütme öncesi bir etkinliğin yapılandırma hatalarını raporlamak etkinlik doğrulamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="d7ea2-104">Windows Workflow Foundation (WF) aşağıdaki üç tür etkinliği doğrulama sağlar:</span><span class="sxs-lookup"><span data-stu-id="d7ea2-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
-   <span data-ttu-id="d7ea2-105">`RequiredArgument` ve `OverloadGroup` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
-   <span data-ttu-id="d7ea2-106">Kesin kod temelli doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-106">Imperative code-based validation.</span></span>  
  
-   <span data-ttu-id="d7ea2-107">Bildirim temelli kısıtlamalar.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="d7ea2-108">`RequiredArgument` ve `OverloadGroup` öznitelikleri gösteren belirli bağımsız değişkenler bir etkinlikte gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="d7ea2-109">Kesin kod temelli doğrulama doğrulama kendisi hakkında sağlamaya bir etkinlik için basit bir yol sağlar ve doğrulama etkinliği ve ilişkisini içeren iş akışı ile ilgili bildirim temelli kısıtlamalar etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="d7ea2-110">Bir etkinlik doğrulama gereksinimlerine göre düzgün şekilde yapılandırılmadıysa, doğrulama hataları ve Uyarıları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="d7ea2-111">Kapsanan iş akışını iş akışı Tasarımcısı'nı kullanarak oluşturulduysa, doğrulama hataları ve Uyarıları Tasarımcısı'nda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="d7ea2-112">İş akışı iş akışı Tasarımcısı dışında oluşturulursa tüm doğrulama hatalarını iş akışı çalıştırıldığında döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="d7ea2-113">İş akışını nasıl oluşturulduğuna bakılmaksızın, bir iş akışı doğrulama hataları asla yürütmek için izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="d7ea2-114">Bu bölümde, bu tür etkinlik doğrulamayı ve etkinlik doğrulamayı nasıl çağrıldığını'ne genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7ea2-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d7ea2-115">In This Section</span></span>  
 [<span data-ttu-id="d7ea2-116">Gerekli Bağımsız Değişkenler ve Aşırı Yüklenmiş Gruplar</span><span class="sxs-lookup"><span data-stu-id="d7ea2-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="d7ea2-117">Nasıl kullanılacağını açıklar `RequiredArgument` ve `OverloadGroup` doğrulama sağlamak için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="d7ea2-118">Kesin Kod Temelli Doğrulama</span><span class="sxs-lookup"><span data-stu-id="d7ea2-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="d7ea2-119">Kod temelli doğrulama için kullanmayı açıklar <xref:System.Activities.CodeActivity> ve <xref:System.Activities.NativeActivity> etkinlikleri temel.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="d7ea2-120">Bildirim Temelli Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="d7ea2-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="d7ea2-121">Bildirim temelli kısıtlamalar karmaşık etkinlik doğrulama sağlamak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="d7ea2-122">Etkinlik Doğrulamayı Çağırma</span><span class="sxs-lookup"><span data-stu-id="d7ea2-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="d7ea2-123">Etkinlik doğrulamayı otomatik olarak ne zaman çağrılır ve doğrulama açıkça çağırmak nasıl ele alır.</span><span class="sxs-lookup"><span data-stu-id="d7ea2-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d7ea2-124">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d7ea2-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7ea2-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d7ea2-125">Related Sections</span></span>
