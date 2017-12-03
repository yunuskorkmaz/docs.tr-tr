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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a6edccba458bfd3629cab851c5d818a69d26173
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-annotation-in-queries"></a>Ek açıklama sorgularda kullanma
Ek açıklamalar, rasgele yapı zamanından sonra yapılandırılmış bir değerle kayıtları izleme etiketi izin verir. Örneğin, "Posta sunucusuyla" etiketli için çeşitli iş akışları arasında birkaç izleme kayıtları istiyor olabilirsiniz "Posta Sunucu1" ==. Bu izleme kayıtları daha sonra sorgularken bu etikete sahip tüm kayıtları bulmayı kolaylaştırır.  
  
## <a name="adding-annotations"></a>Ek açıklamaları ekleme  
 Açıklamanın, aşağıdaki örnekte gösterildiği gibi bir izleme sorguya eklenebilir.  
  
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
>  Bu sorgu öğeleri izleme izleme profili oluşturmak için kullanılabilir. İzleme profili, yapılandırma veya kod kullanarak oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>  
 <xref:System.Activities.Tracking.TrackingProfile>  
 [\<Katılımcıları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)  
 [İzleme ve izleme iş akışı](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [Profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
