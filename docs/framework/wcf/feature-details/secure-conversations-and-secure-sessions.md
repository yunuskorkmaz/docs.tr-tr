---
title: Güvenli İletişimler ve Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 6cbf877c80b7d10705868120c4ec4a7b40895114
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288508"
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar

Windows Communication Foundation (WCF) özelliği, birbirlerinin kimliğini doğrulayan ve şifreleme ve dijital imza sürecini kabul eden iki uç nokta arasında güvenli oturumlar oluşturma olanağıdır. Örneğin, hizmet uç noktası, kimlik doğrulaması için bir X. 509.440 sertifikasını temel alan bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemcinin kimliği doğrulandıktan sonra, hizmet uç noktası, daha sonra oturum içindeki tüm sonraki iletileri güvenli hale getirmek için kullanılan bir güvenlik bağlamı belirteci (SCT) istemciye geri döndürür. Bu güvenli oturum oluşturmak, SCT 'nin simetrik bir anahtara sahip olması nedeniyle iki uç nokta arasında değiş tokuş edilen ileti kümesinin daha verimli olmasını sağlar. X. 509.440 sertifikalarının temel aldığı asimetrik anahtarlar, dijital imza oluştururken veya bir veri kümesini şifrelerken simetrik anahtarlara göre önemli ölçüde daha fazla hesaplama gücü gerektirir.  
  
 Önyükleme ilkesi ( [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) Standard 'ın 6.2.7 bölümünde tanımlanmıştır), kanalı güvenli hale getirmek ve RST/SCT ve rstr/SCT Exchange 'den önce istemcinin kimliğini doğrulamak için kullanılan ileti güvenlik onaylamalarını içerir. Belirli WCF standart bağlamaları `Security.Message.EstablishSecurityContext` , güvenli konuşmanın kullanılıp kullanılmadığını denetleyen bir özelliğe sahiptir. Özel Bağlamalar kullanılırken, önyükleme, [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyası aracılığıyla veya kod içinde çağırarak güvenlik bağlama öğelerinin iç içe geçme yoluyla belirtilir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> .  
  
 Oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](sessions-instancing-and-concurrency.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](how-to-create-a-service-that-requires-sessions.md)
