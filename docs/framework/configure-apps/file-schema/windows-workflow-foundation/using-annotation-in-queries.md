---
title: Sorgularda Ek Açıklama Kullanma
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 728408e744bc1eca62158fab1a7a17e985fe3b6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947280"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="9ed39-102">Sorgularda Ek Açıklama Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ed39-102">Using Annotation in Queries</span></span>
<span data-ttu-id="9ed39-103">Ek açıklamalar, derleme zamanından sonra yapılandırılabilecek bir değer ile izleme kayıtlarını rastgele etiketlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9ed39-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="9ed39-104">Örneğin, "posta sunucusu" = = "mail Sunucu1" ile etiketlenecek birkaç iş akışı arasında birkaç izleme kaydının olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ed39-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="9ed39-105">Bu, izleme kayıtlarını daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9ed39-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="9ed39-106">Ek açıklamaları ekleme</span><span class="sxs-lookup"><span data-stu-id="9ed39-106">Adding Annotations</span></span>  
 <span data-ttu-id="9ed39-107">Aşağıdaki örnekte gösterildiği gibi, bir izleme sorgusuna ek açıklama eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="9ed39-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="9ed39-108">Bu izleme sorgusu öğeleri, bir izleme profili oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed39-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="9ed39-109">Bir izleme profili, yapılandırma veya kod kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="9ed39-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed39-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed39-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="9ed39-111">\<Katılımcılar ></span><span class="sxs-lookup"><span data-stu-id="9ed39-111">\<participants></span></span>](participants.md)
- [<span data-ttu-id="9ed39-112">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9ed39-112">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ed39-113">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9ed39-113">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
