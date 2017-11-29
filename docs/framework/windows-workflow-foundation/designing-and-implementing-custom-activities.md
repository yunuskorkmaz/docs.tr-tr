---
title: "Tasarlama ve uygulama özel etkinlikler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9243761803bc8b68ce37b3d3ad310e8bb7f93d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="d273a-102">Tasarlama ve uygulama özel etkinlikler</span><span class="sxs-lookup"><span data-stu-id="d273a-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="d273a-103">Özel etkinlikleri [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ya da assembling sistem tarafından sağlanan etkinliklerine bileşik etkinlikleri veya öğesinden türetilen yeni türleri oluşturma tarafından oluşturulan <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="d273a-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="d273a-104">Bu bölümde, her iki yöntemle özel etkinlikler oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d273a-105">Varsayılan olarak özel etkinlikler iş akışı Tasarımcısı'nda etkinliğe ilişkin adlı basit bir dikdörtgen olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d273a-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="d273a-106">İş akışı etkinlik özel görsel gösterimi sağlamak için tasarımcı da özel bir tasarımcı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d273a-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d273a-107">[Özel etkinlik tasarımcıları ve şablonlar kullanarak](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="d273a-107"> [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d273a-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d273a-108">In This Section</span></span>  
 [<span data-ttu-id="d273a-109">Etkinlik yazma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d273a-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="d273a-110">Kullanılabilir geliştirme stilleri anlatılmaktadır [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d273a-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="d273a-111">Özel Etkinlik kullanma</span><span class="sxs-lookup"><span data-stu-id="d273a-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="d273a-112">Bir iş akışı projeye özel bir etkinlik eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="d273a-113">Zaman uyumsuz etkinlikleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d273a-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="d273a-114">Zaman uyumsuz etkinlikleri oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="d273a-115">Etkinlik doğrulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d273a-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="d273a-116">Etkinlik doğrulama tanımlamak için nasıl kullanılabileceğini ve rapor hataları yürütülmesinin önce bir etkinliğin yapılandırmasında açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="d273a-117">Çalışma zamanında bir etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="d273a-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="d273a-118">Çalışma zamanı kullanarak etkinlikleri oluşturmak nasıl ele <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="d273a-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="d273a-119">İş akışı yürütme özellikleri</span><span class="sxs-lookup"><span data-stu-id="d273a-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="d273a-120">Bir etkinliğin ortama bağlam belirli özellikleri eklemek için iş akışı yürütme özelliklerini kullanmayı açıklar</span><span class="sxs-lookup"><span data-stu-id="d273a-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="d273a-121">Etkinlik temsilcileri kullanma</span><span class="sxs-lookup"><span data-stu-id="d273a-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="d273a-122">Etkinlik temsilciler içeren etkinlikleri yazar ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-122">Discusses how to author and use activities that contain activity delegates.</span></span>  
  
 [<span data-ttu-id="d273a-123">Etkinlik yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d273a-123">Activity Localization</span></span>](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 <span data-ttu-id="d273a-124">Dize kaynakları yerelleştirme aktivitelerde kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-124">Describes how to use localization of string resources in activities.</span></span>  
  
 [<span data-ttu-id="d273a-125">Etkinlik uzantıları kullanma</span><span class="sxs-lookup"><span data-stu-id="d273a-125">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="d273a-126">Etkinlik uzantıları yazar ve nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-126">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="d273a-127">Bir iş akışından akışları OData kullanma</span><span class="sxs-lookup"><span data-stu-id="d273a-127">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="d273a-128">Bir iş akışından bir WCF veri hizmeti çağrılırken için bazı yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d273a-128">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="d273a-129">Etkinlik tanımı kapsam ve görünürlük</span><span class="sxs-lookup"><span data-stu-id="d273a-129">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="d273a-130">Seçenekler ve etkinlikler için veri kapsamı ve üye görünürlüğü tanımlamak için kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="d273a-130">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
