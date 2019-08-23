---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: d511a45d990e441c5dcfd8405794ec937c0278d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966068"
---
# <a name="secure-sessions"></a>Güvenli Oturumlar
Windows Communication Foundation (WCF) özelliği, iletilerin gönderildikleri sırada alınabileceğini garanti eden güvenilir oturumlardır. Bu bölümdeki konularda, güvenilir bir oturum oluştururken dikkate alınması gereken güvenlik etkileri ele alınmaktadır. Güvenilir oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
> Windows XP 'de kimliğe bürünme özelliği gerekli olduğunda, durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCN 'ler kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için bkz. [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|||  
|-|-|  
|[Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Güvenli konuşmalar ve güvenli oturumlar eşanlamlı olarak anlamlıdır. Bu konuda, güvenli bir konuşmanın çalışma şekli ve düzenin ne zaman ve neden kullanıldığı açıklanmaktadır.|  
|[Nasıl yapılır: Güvenli oturum oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Güvenli bir oturum oluşturma hakkındaki temel bilgileri adım adım açıklar.|  
|[Nasıl yapılır: Güvenli bir oturum için güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|İstemcilerle durum ve oturumları koruyacak bir Web grubu oluşturma adımlarında size yol gösterir.|  
|[Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Güvenli oturumlar için özel konuları açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Ileti yeniden yürütme algılamayı etkinleştir](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Nasıl yapılır: Oturum gerektiren bir hizmet oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
