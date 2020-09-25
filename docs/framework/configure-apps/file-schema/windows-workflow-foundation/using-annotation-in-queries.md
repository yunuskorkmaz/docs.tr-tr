---
title: Sorgularda Ek Açıklama Kullanma
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 3dd5d19cc303314386ae62ba67f7eec978f6d80b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185372"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="709ad-102">Sorgularda Ek Açıklama Kullanma</span><span class="sxs-lookup"><span data-stu-id="709ad-102">Using Annotation in Queries</span></span>

<span data-ttu-id="709ad-103">Ek açıklamalar, derleme zamanından sonra yapılandırılabilecek bir değer ile izleme kayıtlarını rastgele etiketlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="709ad-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="709ad-104">Örneğin, "posta sunucusu" = = "mail Sunucu1" ile etiketlenecek birkaç iş akışı arasında birkaç izleme kaydının olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="709ad-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="709ad-105">Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="709ad-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="709ad-106">Ek açıklamaları ekleme</span><span class="sxs-lookup"><span data-stu-id="709ad-106">Adding Annotations</span></span>  

 <span data-ttu-id="709ad-107">Aşağıdaki örnekte gösterildiği gibi, bir izleme sorgusuna ek açıklama eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="709ad-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="709ad-108">Bu izleme sorgusu öğeleri, bir izleme profili oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="709ad-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="709ad-109">Bir izleme profili, yapılandırma veya kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="709ad-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="709ad-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="709ad-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="709ad-111">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="709ad-111">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="709ad-112">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="709ad-112">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
