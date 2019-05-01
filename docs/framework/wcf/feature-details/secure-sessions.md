---
title: Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990983"
---
# <a name="secure-sessions"></a>Güvenli Oturumlar
Bir Windows Communication Foundation (WCF) iletiler gönderildikleri sırayla alınır garanti güvenilir oturumlar özelliğidir. Bu bölümdeki konular, bir güvenilir oturum oluştururken dikkate alınması gereken güvenlikle ilgili etkileri açıklanmaktadır. Güvenilir oturumlar hakkında daha fazla bilgi için bkz: [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
> [!NOTE]
>  Kimliğe bürünme Windows XP'de gerektiğinde bir durum bilgisi olan güvenlik bağlamı belirteci (SCT) olmadan güvenli bir oturum kullanın. Durum bilgisi olan SCTs kimliğe bürünme ile kullanıldığında bir <xref:System.InvalidOperationException> oluşturulur. Daha fazla bilgi için [desteklenmeyen senaryolar](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|||  
|-|-|  
|[Güvenli İletişimler ve Güvenli Oturumlar](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|Güvenli konuşma ve güvenli oturumlar eşanlamlıdır. Bu konu, güvenli konuşma, nasıl işlediğini gösteren açıklar ve ne zaman ve neden bu düzeni kullanın.|  
|[Nasıl yapılır: Güvenli oturum oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|Güvenli oturum oluşturma hakkındaki temel bilgileri adım adım açıklanmaktadır.|  
|[Nasıl yapılır: Oluşturma bir güvenlik bağlamı belirteci güvenli bir oturum için](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|Durum ve istemcilerle oturumları tutacaktır bir Web grubu oluşturma adımlarını açıklar.|  
|[Güvenli Oturumlar için Güvenlikle İlgili Önemli Noktalar](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|Güvenli oturumlar için özel hususlar açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İleti yeniden yürütme algılamayı etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Nasıl yapılır: Oturumlarının gerektiren bir hizmet oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
