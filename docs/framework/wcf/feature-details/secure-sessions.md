---
title: "Güvenli Oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 724ea72c52296c448ead80a8f357235d625f5842
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="secure-sessions"></a>Güvenli Oturumlar
Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iletileri gönderildiği adres sıraya alınan garanti güvenilir oturumdur. Bu bölümdeki konular, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik uygulamalarını tartışın. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]güvenilir oturumlar bkz [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|||  
|-|-|  
|[Güvenli iletişimler ve güvenli oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Güvenli görüşmeler ve güvenli oturumlar eşanlamlıdır. Bu konuda, güvenli bir konuşma çalışır, şekilde açıklanmıştır ve dosyası, ne zaman ve neden deseni kullanılacak.|  
|[Nasıl yapılır: güvenli oturum oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Güvenli oturum oluşturma temelleri adım adım açıklanmaktadır.|  
|[Nasıl yapılır: bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Durum ve oturumlar istemcilerle tutacağı bir Web grubu oluşturma adımları açıklanmaktadır.|  
|[Güvenli oturumlar için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Güvenli oturumlar için özel hususlar açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Oturumlar, örnek oluşturma ve eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Hizmetleri Tasarlama ve uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: ileti yeniden yürütme algılamayı etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Yeniden yürütme saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Nasıl yapılır: oturum gerektiren bir hizmet oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
