---
title: Özel Etkinlikler Tasarlama ve Uygulama
description: Bu makale, bileşik etkinlikler oluşturarak veya yeni etkinlik türleri oluşturarak Workflow Foundation 'da özel etkinlikler oluşturmaya yönelik kaynaklar sağlar.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: cb6e189cf5f59630ce8d89610eb0c2fc2acc92a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280396"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="eb192-103">Özel Etkinlikler Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="eb192-103">Designing and Implementing Custom Activities</span></span>

<span data-ttu-id="eb192-104">İçindeki özel etkinlikler [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] , sistem tarafından belirtilen etkinlikleri bileşik etkinliklere dağıtarak ya da, veya ' den türetilen yeni türler oluşturularak oluşturulur <xref:System.Activities.CodeActivity> <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.NativeActivity> .</span><span class="sxs-lookup"><span data-stu-id="eb192-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="eb192-105">Bu bölümde, her iki yöntemle de özel etkinliklerin nasıl oluşturulduğu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb192-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb192-106">Varsayılan olarak özel etkinlikler, etkinlik adı ile basit bir dikdörtgen olarak iş akışı Tasarımcısı içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="eb192-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="eb192-107">İş akışı tasarımcısında etkinliğinizin özel görsel temsilini sağlamak için özel bir tasarımcı da oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb192-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="eb192-108">Daha fazla bilgi için bkz. [özel etkinlik tasarımcıları ve şablonları kullanma](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="eb192-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb192-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eb192-109">In This Section</span></span>  

 [<span data-ttu-id="eb192-110">Etkinlik Yazma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="eb192-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="eb192-111">' De bulunan yazma stillerini açıklar [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="eb192-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="eb192-112">Özel etkinlik kullanma</span><span class="sxs-lookup"><span data-stu-id="eb192-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="eb192-113">Bir iş akışı projesine özel bir etkinliğin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="eb192-114">Zaman Uyumsuz Etkinlikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb192-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="eb192-115">Zaman uyumsuz etkinliklerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="eb192-116">Etkinlik Doğrulamayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eb192-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="eb192-117">Etkinlik doğrulamanın yürütmeden önce bir etkinliğin yapılandırmasındaki hataları tanımlamak ve raporlamak için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="eb192-118">Çalışma Zamanında Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb192-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="eb192-119">Kullanarak çalışma zamanında etkinliklerin nasıl oluşturulduğunu açıklar <xref:System.Activities.DynamicActivity> .</span><span class="sxs-lookup"><span data-stu-id="eb192-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="eb192-120">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="eb192-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="eb192-121">Bir etkinliğin ortamına bağlama özgü özellikler eklemek için iş akışı yürütme özelliklerinin nasıl kullanılacağını açıklar</span><span class="sxs-lookup"><span data-stu-id="eb192-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="eb192-122">Etkinlik Temsilcileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb192-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="eb192-123">Etkinlik temsilcileri içeren etkinliklerin nasıl yazılacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="eb192-124">Etkinlik Uzantıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb192-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="eb192-125">Etkinlik uzantılarının nasıl yazılacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="eb192-126">İş Akışından OData Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="eb192-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="eb192-127">Bir iş akışından bir WCF veri hizmetini çağırmak için çeşitli yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb192-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="eb192-128">Etkinlik Tanımı Kapsamı ve Görünürlüğü</span><span class="sxs-lookup"><span data-stu-id="eb192-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="eb192-129">Etkinlik için veri kapsamını ve üye görünürlüğünü tanımlamaya yönelik seçenekleri ve kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb192-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
