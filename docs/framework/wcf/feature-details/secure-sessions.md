---
title: Güvenli Oturumlar
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 068615510d7e1d73ae260441ccef6536ee6ff317
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="secure-sessions"></a>Güvenli Oturumlar
Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] iletileri gönderildiği adres sıraya alınan garanti güvenilir oturumdur. Bu bölümdeki konular, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik uygulamalarını tartışın. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için bkz: [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|||  
|-|-|  
|[Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Güvenli görüşmeler ve güvenli oturumlar eşanlamlıdır. Bu konuda, güvenli bir konuşma çalışır, şekilde açıklanmıştır ve dosyası, ne zaman ve neden deseni kullanılacak.|  
|[Nasıl yapılır: Güvenli Oturum Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Güvenli oturum oluşturma temelleri adım adım açıklanmaktadır.|  
|[Nasıl yapılır: Güvenli Bir Oturum için Güvenlik Bağlamı Belirteci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Durum ve oturumlar istemcilerle tutacağı bir Web grubu oluşturma adımları açıklanmaktadır.|  
|[Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Güvenli oturumlar için özel hususlar açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: İleti Yeniden Yürütme Algılamayı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
