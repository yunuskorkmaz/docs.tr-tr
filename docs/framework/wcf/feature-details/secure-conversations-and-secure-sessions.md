---
title: Güvenli İletişimler ve Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 887b2e6e6553a910de046950514869907519cf35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746456"
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar
Windows Communication Foundation (WCF) özelliği, birbirlerinin kimliğini doğrulayan ve şifreleme ve dijital imza sürecini kabul eden iki uç nokta arasında güvenli oturumlar oluşturma olanağıdır. Örneğin, hizmet uç noktası, kimlik doğrulaması için bir X. 509.440 sertifikasını temel alan bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemcinin kimliği doğrulandıktan sonra, hizmet uç noktası, daha sonra oturum içindeki tüm sonraki iletileri güvenli hale getirmek için kullanılan bir güvenlik bağlamı belirteci (SCT) istemciye geri döndürür. Bu güvenli oturum oluşturmak, SCT 'nin simetrik bir anahtara sahip olması nedeniyle iki uç nokta arasında değiş tokuş edilen ileti kümesinin daha verimli olmasını sağlar. X. 509.440 sertifikalarının temel aldığı asimetrik anahtarlar, dijital imza oluştururken veya bir veri kümesini şifrelerken simetrik anahtarlara göre önemli ölçüde daha fazla hesaplama gücü gerektirir.  
  
 Önyükleme ilkesi ( [WS-SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) Standard 'ın 6.2.7 bölümünde tanımlanmıştır), kanalı güvenli hale getirmek ve RST/SCT ve rstr/SCT Exchange 'den önce istemcinin kimliğini doğrulamak için kullanılan ileti güvenlik onaylamalarını içerir. Belirli WCF standart bağlamaları, güvenli konuşmanın kullanılıp kullanılmadığını denetleyen bir `Security.Message.EstablishSecurityContext` özelliğine sahiptir. Özel Bağlamalar kullanılırken, önyükleme, yapılandırma dosyasında [\<securemanagementtionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) aracılığıyla veya kodda <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> çağırarak, güvenlik bağlama öğelerinin iç içe geçme yoluyla belirtilir.  
  
 Oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanma](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
