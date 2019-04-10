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
# <a name="using-annotation-in-queries"></a>Sorgularda Ek Açıklama Kullanma
Ek açıklamaları, rasgele yapı saatinden yapılandırılabilir bir değerle kayıtları izleme etiket izin verir. Örneğin, "Posta sunucusu ile" etiketlemek için birkaç iş akışları arasında birkaç izleme kayıtları isteyebilirsiniz "Posta Sunucu1" ==. Bu etikete sahip tüm kayıtları izleme kayıtları daha sonra sorgulanırken bulma kolaylaştırır.  
  
## <a name="adding-annotations"></a>Ek açıklamaları ekleme  
 Aşağıdaki örnekte gösterildiği gibi bir ek açıklama bir izleme sorguya eklenebilir.  
  
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
>  Bu sorgu öğeleri izleme bir izleme profili oluşturmak için kullanılabilir. Bir izleme profili yapılandırma veya kod kullanılarak oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)
- [İş Akışı Takip ve İzleme](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [İzleme Profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
