---
title: "İş akışı tasarım deneyimini özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ca6e23febf14b2db28bad950d2cd012fdce30fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="5dba1-102">İş akışı tasarım deneyimini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5dba1-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="5dba1-103">Özel etkinlikler tasarlama ve yeniden barındırma için senaryolar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] olarak büyük ölçüde basitleştirilmiştir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dba1-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="5dba1-104">Geliştirme ve dağıtım artık daha kolay ve daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="5dba1-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="5dba1-105">Yeni Etkinlik Tasarımcısı programlama modeli üzerinde oluşturulmuştur anahtar infrastructural değişiklik olduğundan [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dba1-105">The key infrastructural change is that the new activity designer programming model is built upon [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="5dba1-106">Bu etkinlik tasarımcıları bildirimli olarak tanımlamanızı ve yeniden barındırma olanağı verir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] karşılaştırmalı kolay olan diğer uygulamalarda.</span><span class="sxs-lookup"><span data-stu-id="5dba1-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="5dba1-107">Yeniden barındırma, özel ifade Düzenleyicisi IntelliSense veya Basitleştirilmiş ifade etki alanı destekleyecek şekilde geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5dba1-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="5dba1-108">İle tümleştirme [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] iş akışı Hizmetleri kullanımı ile daha kolay hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="5dba1-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="5dba1-109">Özel Etkinlik tasarımcıları ve Model öğesi ağacı tasarım zamanı rehosted iş akışı tasarımcılarına deneyimleri geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5dba1-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5dba1-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5dba1-110">In This Section</span></span>  
 [<span data-ttu-id="5dba1-111">Özel Etkinlik Tasarımcıları ve Şablonları Kullanma</span><span class="sxs-lookup"><span data-stu-id="5dba1-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="5dba1-112">Yeni özel etkinlik tasarımcıları ve şablonları nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="5dba1-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="5dba1-113">İş Akışı Tasarımcısını Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="5dba1-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="5dba1-114">Yeniden barındırmak açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dışında [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ve doğrulama hataları görüntülemek nasıl.</span><span class="sxs-lookup"><span data-stu-id="5dba1-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="5dba1-115">Özel İfade Düzenleyicisi Kullanma</span><span class="sxs-lookup"><span data-stu-id="5dba1-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="5dba1-116">İş akışı tasarımcıları dışında rehosted ile kullanılacak bir özel ifade Düzenleyicisi'ni uygulamak açıklar [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5dba1-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5dba1-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5dba1-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="5dba1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dba1-118">See Also</span></span>  
 [<span data-ttu-id="5dba1-119">Windows Workflow Foundation’ı Genişletme</span><span class="sxs-lookup"><span data-stu-id="5dba1-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="5dba1-120">Tasarımcı</span><span class="sxs-lookup"><span data-stu-id="5dba1-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="5dba1-121">Özel Etkinlik Tasarımcıları</span><span class="sxs-lookup"><span data-stu-id="5dba1-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="5dba1-122">Tasarımcıyı Yeniden Barındırma</span><span class="sxs-lookup"><span data-stu-id="5dba1-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
