---
title: Sorgularda Ek Açıklama Kullanma
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: fd2d98852ca44e3485ddcf4be29d505b39011698
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208650"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="2d3e7-102">Sorgularda Ek Açıklama Kullanma</span><span class="sxs-lookup"><span data-stu-id="2d3e7-102">Using Annotation in Queries</span></span>
<span data-ttu-id="2d3e7-103">Ek açıklamaları, rasgele yapı saatinden yapılandırılabilir bir değerle kayıtları izleme etiket izin verir.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="2d3e7-104">Örneğin, "Posta sunucusu ile" etiketlemek için birkaç iş akışları arasında birkaç izleme kayıtları isteyebilirsiniz "Posta Sunucu1" ==.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="2d3e7-105">Bu etikete sahip tüm kayıtları izleme kayıtları daha sonra sorgulanırken bulma kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="2d3e7-106">Ek açıklamaları ekleme</span><span class="sxs-lookup"><span data-stu-id="2d3e7-106">Adding Annotations</span></span>  
 <span data-ttu-id="2d3e7-107">Aşağıdaki örnekte gösterildiği gibi bir ek açıklama bir izleme sorguya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="2d3e7-108">Bu sorgu öğeleri izleme bir izleme profili oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="2d3e7-109">Bir izleme profili yapılandırma veya kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d3e7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d3e7-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="2d3e7-111">\<Katılımcıları ></span><span class="sxs-lookup"><span data-stu-id="2d3e7-111">\<participants></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [<span data-ttu-id="2d3e7-112">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2d3e7-112">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2d3e7-113">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2d3e7-113">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
