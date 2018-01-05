---
title: "Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a>Bir İş Akışı Çözümüne Hizmet Başvurusu Ekleme
Bir iş akışı uygulamasında bir hizmet başvurusu ekleme biraz normal bir WCF uygulaması farklı şekilde çalışır. Hizmet Başvurusu Ekle seçtiğinizde ve hizmet URL'sini belirtin meta verileri indirilir ve özel etkinlikler WCF hizmeti çağırmasına olanak tanıyan oluşturulur veya WCF iş akışı hizmeti için bir başvuru eklenir. Oluşturulan etkinlikleri yerleşik şekilde hizmet başvurusu eklendikten sonra çözümü yeniden derleyin. Bunlar daha sonra iş akışı Tasarımcısı araç kutusunda görünür. Ancak, bir iş akışı çözümünde hizmet başvurusu ekliyorsanız bu yalnızca çalışacağını unutmayın. Aşağıdaki web cast diğer tür projelerde hizmet Başvurusu Ekle gösterilmektedir: [bir WCF hizmeti bir Web projesi bir iş akışında arama](http://go.microsoft.com/fwlink/?LinkId=207725).  
  
 Aynı işlemi adını içeren Hizmetleri iki veya daha fazla hizmeti başvuruları ekleme bir sorunu neden olur. Oluşturulan etkinlikleri yalnızca ilk hizmet işlemini çağırır. Bu sorunu yeniden adlandırma hizmet işlemleri çalışmak için bu nedenle bunlar farklı veya oluşturulan her etkinlik uç nokta Yapılandırması adı değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Akışı Hizmetleri](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Nasıl yapılır: Başka Bir İş Akışı Hizmetine Çağrı Yapan Bir İş Akışı Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [Bir WCF hizmeti bir Web projesi bir iş akışında arama](http://go.microsoft.com/fwlink/?LinkId=207725)
