---
title: Tasarlama ve uygulama özel etkinlikler
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 673145c856e950c8648a87cb3dcb9665ffa51ba9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873394"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="bc292-102">Tasarlama ve uygulama özel etkinlikler</span><span class="sxs-lookup"><span data-stu-id="bc292-102">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="bc292-103">Özel etkinlikleri [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bileşik etkinlikleri assembling ya da sistem tarafından sağlanan etkinliklerine veya öğesinden türeyen yeni türleri oluşturarak oluşturulan <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, veya <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="bc292-103">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="bc292-104">Bu bölümde, iki yöntemden biriyle özel etkinlikler oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc292-104">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc292-105">Varsayılan olarak özel etkinlikler iş akışı Tasarımcısı'nda etkinliğin adı ile basit bir dikdörtgen olarak görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="bc292-105">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="bc292-106">İş akışı etkinliklerinizi özel görsel bir temsilini sağlamak için tasarımcı, ayrıca özel bir tasarımcı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc292-106">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="bc292-107">Daha fazla bilgi için [kullanarak özel etkinlik tasarımcıları ve şablonları](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="bc292-107">For more information, see [Using Custom Activity Designers and Templates](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc292-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bc292-108">In This Section</span></span>  
 [<span data-ttu-id="bc292-109">Etkinlik Yazma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bc292-109">Activity Authoring Options</span></span>](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 <span data-ttu-id="bc292-110">Kullanılabilir yazma stilleri açıklar [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc292-110">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="bc292-111">Özel etkinlik kullanma</span><span class="sxs-lookup"><span data-stu-id="bc292-111">Using a custom activity</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 <span data-ttu-id="bc292-112">Bir iş akışı projesine özel bir etkinlik eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc292-112">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="bc292-113">Zaman Uyumsuz Etkinlikler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc292-113">Creating Asynchronous Activities</span></span>](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="bc292-114">Zaman uyumsuz etkinlikler oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc292-114">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="bc292-115">Etkinlik Doğrulamayı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bc292-115">Configuring Activity Validation</span></span>](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 <span data-ttu-id="bc292-116">Etkinlik doğrulamayı belirlemek için nasıl kullanılabileceğini ve rapor yürütme öncesi bir etkinliğe ilişkin yapılandırma hataları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bc292-116">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="bc292-117">Çalışma Zamanında Etkinlik Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bc292-117">Creating an Activity at Runtime</span></span>](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="bc292-118">Etkinliklerini kullanarak çalışma zamanı oluşturma açıklanır <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="bc292-118">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="bc292-119">İş Akışı Yürütme Özellikleri</span><span class="sxs-lookup"><span data-stu-id="bc292-119">Workflow Execution Properties</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 <span data-ttu-id="bc292-120">Bir etkinliğin ortama özgü özellikleri bağlam eklemek için iş akışı yürütme özelliklerini kullanmayı açıklar</span><span class="sxs-lookup"><span data-stu-id="bc292-120">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="bc292-121">Etkinlik Temsilcileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc292-121">Using Activity Delegates</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 <span data-ttu-id="bc292-122">Yazar ve etkinlik temsilcileri içeren etkinlikler kullanma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bc292-122">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="bc292-123">Etkinlik Uzantıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc292-123">Using Activity Extensions</span></span>](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 <span data-ttu-id="bc292-124">Yazar ve etkinlik uzantıları kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc292-124">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="bc292-125">İş Akışından OData Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="bc292-125">Consuming OData Feeds from a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="bc292-126">Bir iş akışından bir WCF veri hizmeti çağırmak için çeşitli yöntemler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="bc292-126">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="bc292-127">Etkinlik Tanımı Kapsamı ve Görünürlüğü</span><span class="sxs-lookup"><span data-stu-id="bc292-127">Activity Definition Scoping and Visibility</span></span>](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="bc292-128">Seçenekleri ve etkinlikler için veri üyesi kapsam ve görünürlük tanımlamak için kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="bc292-128">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
