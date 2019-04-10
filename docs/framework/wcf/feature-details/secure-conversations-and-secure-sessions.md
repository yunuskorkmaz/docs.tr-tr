---
title: Güvenli İletişimler ve Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 9b2c22d6db5a773bfb3f3a41e458b530fc889d71
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224409"
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar
Bir Windows Communication Foundation (WCF) doğrulaması ve bir şifreleme ve dijital imza işlemi sırasında kabul ediyorum iki uç noktalar arasında güvenli oturumlar kurma olanağı özelliğidir. Örneğin, hizmet uç noktası kimlik doğrulaması için bir X.509 sertifikası temel bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemci kimliği doğrulandıktan sonra hizmet uç noktası bir güvenlik bağlamı belirteci (SCT) sonra oturum içinde tüm sonraki iletileri güvenli hale getirmek için kullanılan istemciye geri döndürür. Bu güvenli oturum oluşturma, SCT simetrik anahtar içerdiğinden daha verimli olmasını iki uç nokta arasında alınıp verilen iletileri kümesini etkinleştirir. Hangi X.509 sertifikaları üzerine dayalı, asimetrik anahtarlar simetrik ne zaman anahtarları daha önemli ölçüde daha fazla hesaplama gücü gerektiren bir dijital imza oluşturulurken veya veri kümesini şifreleme.  
  
 Önyükleme İlkesi (kısmında 6.2.7 [WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standart) kanalının güvenliğini sağlayın ve lk/SCT ve RSTR/SCT alışverişi yapılmadan önce istemcinin kimliğini doğrulamak için kullanılan ileti güvenlik onayı içeriyor. Bazı WCF standart bağlamaları sahip bir `Security.Message.EstablishSecurityContext` hangi denetimlerin olup güvenli konuşma özelliği kullanılır. Özel bağlamalar kullanırken önyükleme iç içe güvenlik bağlama öğeleri aracılığıyla belirtilir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyasında veya çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> kod.  
  
 Oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
