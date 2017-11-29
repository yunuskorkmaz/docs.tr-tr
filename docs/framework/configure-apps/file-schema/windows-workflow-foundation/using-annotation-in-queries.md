---
title: "Ek açıklama sorgularda kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8713d84af96fa69df5ace33d76ec21560dab2c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="d3722-102">Ek açıklama sorgularda kullanma</span><span class="sxs-lookup"><span data-stu-id="d3722-102">Using Annotation in Queries</span></span>
<span data-ttu-id="d3722-103">Ek açıklamalar, rasgele yapı zamanından sonra yapılandırılmış bir değerle kayıtları izleme etiketi izin verir.</span><span class="sxs-lookup"><span data-stu-id="d3722-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="d3722-104">Örneğin, "Posta sunucusuyla" etiketli için çeşitli iş akışları arasında birkaç izleme kayıtları istiyor olabilirsiniz "Posta Sunucu1" ==.</span><span class="sxs-lookup"><span data-stu-id="d3722-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="d3722-105">Bu izleme kayıtları daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d3722-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="d3722-106">Ek açıklamaları ekleme</span><span class="sxs-lookup"><span data-stu-id="d3722-106">Adding Annotations</span></span>  
 <span data-ttu-id="d3722-107">Açıklamanın, aşağıdaki örnekte gösterildiği gibi bir izleme sorguya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d3722-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d3722-108">Bu sorgu öğeleri izleme izleme profili oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3722-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="d3722-109">İzleme profili, yapılandırma veya kod kullanarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="d3722-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3722-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3722-110">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [<span data-ttu-id="d3722-111">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="d3722-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [<span data-ttu-id="d3722-112">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="d3722-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d3722-113">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="d3722-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
