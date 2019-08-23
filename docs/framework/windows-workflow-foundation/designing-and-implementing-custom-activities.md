---
title: Özel Etkinlikler Tasarlama ve Uygulama
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: b0d04572c65fd4e3e0ae96241217c9ae9aa0e2c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915358"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="6bdfe-102">Özel Etkinlikler Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="6bdfe-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="6bdfe-103">İçindeki [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] özel etkinlikler, sistem tarafından belirtilen etkinlikleri bileşik etkinliklere dağıtarak ya da, <xref:System.Activities.AsyncCodeActivity>veya <xref:System.Activities.NativeActivity>' den <xref:System.Activities.CodeActivity>türetilen yeni türler oluşturularak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="6bdfe-104">Bu bölümde, her iki yöntemle de özel etkinliklerin nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6bdfe-105">Varsayılan olarak özel etkinlikler, etkinlik adı ile basit bir dikdörtgen olarak iş akışı Tasarımcısı içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="6bdfe-106">İş akışı tasarımcısında etkinliğinizin özel görsel temsilini sağlamak için özel bir tasarımcı da oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="6bdfe-107">Daha fazla bilgi için bkz. [özel etkinlik tasarımcıları ve şablonları kullanma](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="6bdfe-107">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6bdfe-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6bdfe-108">In This Section</span></span>  
 [<span data-ttu-id="6bdfe-109">Etkinlik Yazma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6bdfe-109">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="6bdfe-110">' De [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]bulunan yazma stillerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="6bdfe-111">Özel etkinlik kullanma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-111">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="6bdfe-112">Bir iş akışı projesine özel bir etkinliğin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="6bdfe-113">Zaman Uyumsuz Etkinlikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-113">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="6bdfe-114">Zaman uyumsuz etkinliklerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="6bdfe-115">Etkinlik Doğrulamayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-115">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="6bdfe-116">Etkinlik doğrulamanın yürütmeden önce bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="6bdfe-117">Çalışma Zamanında Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-117">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="6bdfe-118">Kullanarak <xref:System.Activities.DynamicActivity>çalışma zamanında etkinliklerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="6bdfe-119">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6bdfe-119">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="6bdfe-120">Bir etkinliğin ortamına bağlama özgü özellikler eklemek için iş akışı yürütme özelliklerinin nasıl kullanılacağını açıklar</span><span class="sxs-lookup"><span data-stu-id="6bdfe-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="6bdfe-121">Etkinlik Temsilcileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-121">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="6bdfe-122">Etkinlik temsilcileri içeren etkinliklerin nasıl yazılacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-122">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="6bdfe-123">Etkinlik Uzantıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-123">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="6bdfe-124">Etkinlik uzantılarının nasıl yazılacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-124">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="6bdfe-125">İş Akışından OData Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="6bdfe-125">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="6bdfe-126">Bir iş akışından bir WCF veri hizmetini çağırmak için çeşitli yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-126">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="6bdfe-127">Etkinlik Tanımı Kapsamı ve Görünürlüğü</span><span class="sxs-lookup"><span data-stu-id="6bdfe-127">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="6bdfe-128">Etkinlik için veri kapsamını ve üye görünürlüğünü tanımlamaya yönelik seçenekleri ve kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="6bdfe-128">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
