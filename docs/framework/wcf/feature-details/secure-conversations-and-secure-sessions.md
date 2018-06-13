---
title: Güvenli İletişimler ve Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497613"
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar
Bir Windows Communication Foundation (WCF) birbirinin kimliğini doğrular ve bir şifreleme ve dijital imza işlemi sırasında kabul iki uç noktalar arasında güvenli oturumları olanağı özelliğidir. Örneğin, hizmet uç noktası kimlik doğrulaması için bir X.509 sertifikası bağlı bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemci kimlik doğrulaması gerçekleştikten sonra hizmet uç noktası bir güvenlik bağlamı belirteci (SCT) sonra oturum içinde tüm sonraki iletileri güvenli hale getirmek için kullanılan istemciye geri döndürür. Bu güvenli oturum oluşturma, bir simetrik anahtar SCT sahip olduğundan daha verimli olmasını iki uç noktaları arasında alınıp verilen iletileri kümesi sağlar. Asimetrik anahtarlar, hangi X.509 sertifikaları dayalı olarak, simetrik ne zaman anahtarları daha önemli ölçüde daha fazla hesaplama gücüne gerektiren bir dijital imza oluşturulurken veya veri kümesi şifreleme.  
  
 Önyükleme İlkesi (bölümünü 6.2.7 tanımlanan [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standart) güvenli kanal ve RST/SCT ve RSTR/SCT exchange önce istemci kimlik doğrulaması için kullanılan ileti güvenlik onayı içeriyor. Bazı WCF standart bağlamaları sahip bir `Security.Message.EstablishSecurityContext` hangi denetimlerin olup güvenli konuşma özelliği kullanılır. Özel bağlamalar kullanırken önyükleme iç içe güvenlik bağlama öğeleri, yoluyla belirtilir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyasında ya da çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> kod.  
  
 Oturumları hakkında daha fazla bilgi için bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
