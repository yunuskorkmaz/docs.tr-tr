---
title: "İş akışı tasarım deneyimini özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9916e30812e167e108a1ca9b958aa6d15fbd1f41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="8dd50-102">İş akışı tasarım deneyimini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8dd50-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="8dd50-103">Özel etkinlikler tasarlama ve yeniden barındırma için senaryolar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] olarak büyük ölçüde basitleştirilmiştir [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd50-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="8dd50-104">Geliştirme ve dağıtım artık daha kolay ve daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="8dd50-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="8dd50-105">Yeni Etkinlik Tasarımcısı programlama modeli üzerinde oluşturulmuştur anahtar infrastructural değişiklik olduğundan [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd50-105">The key infrastructural change is that the new activity designer programming model is built upon [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="8dd50-106">Bu etkinlik tasarımcıları bildirimli olarak tanımlamanızı ve yeniden barındırma olanağı verir [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] karşılaştırmalı kolay olan diğer uygulamalarda.</span><span class="sxs-lookup"><span data-stu-id="8dd50-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="8dd50-107">Yeniden barındırma, özel ifade Düzenleyicisi IntelliSense veya Basitleştirilmiş ifade etki alanı destekleyecek şekilde geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8dd50-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="8dd50-108">İle tümleştirme [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] iş akışı Hizmetleri kullanımı ile daha kolay hale gelmiştir.</span><span class="sxs-lookup"><span data-stu-id="8dd50-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="8dd50-109">Özel Etkinlik tasarımcıları ve Model öğesi ağacı tasarım zamanı rehosted iş akışı tasarımcılarına deneyimleri geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8dd50-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dd50-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8dd50-110">In This Section</span></span>  
 [<span data-ttu-id="8dd50-111">Özel Etkinlik tasarımcıları ve şablonları kullanma</span><span class="sxs-lookup"><span data-stu-id="8dd50-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="8dd50-112">Yeni özel etkinlik tasarımcıları ve şablonları nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dd50-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="8dd50-113">İş Akışı Tasarımcısı yeniden barındırma</span><span class="sxs-lookup"><span data-stu-id="8dd50-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="8dd50-114">Yeniden barındırmak açıklar [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dışında [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ve doğrulama hataları görüntülemek nasıl.</span><span class="sxs-lookup"><span data-stu-id="8dd50-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="8dd50-115">Bir özel ifade Düzenleyicisi'ni kullanarak</span><span class="sxs-lookup"><span data-stu-id="8dd50-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="8dd50-116">İş akışı tasarımcıları dışında rehosted ile kullanılacak bir özel ifade Düzenleyicisi'ni uygulamak açıklar [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd50-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8dd50-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8dd50-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="8dd50-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8dd50-118">See Also</span></span>  
 [<span data-ttu-id="8dd50-119">Windows Workflow Foundation'ı genişletme</span><span class="sxs-lookup"><span data-stu-id="8dd50-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="8dd50-120">Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="8dd50-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="8dd50-121">Özel Etkinlik tasarımcıları</span><span class="sxs-lookup"><span data-stu-id="8dd50-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="8dd50-122">Yeniden barındırma Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="8dd50-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
