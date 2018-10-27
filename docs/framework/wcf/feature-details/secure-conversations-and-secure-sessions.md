---
title: Güvenli İletişimler ve Güvenli Oturumlar
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: d3fd1b82aa05e39e2555ea31955009ea0be881bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182053"
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar
Bir Windows Communication Foundation (WCF) doğrulaması ve bir şifreleme ve dijital imza işlemi sırasında kabul ediyorum iki uç noktalar arasında güvenli oturumlar kurma olanağı özelliğidir. Örneğin, hizmet uç noktası kimlik doğrulaması için bir X.509 sertifikası temel bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemci kimliği doğrulandıktan sonra hizmet uç noktası bir güvenlik bağlamı belirteci (SCT) sonra oturum içinde tüm sonraki iletileri güvenli hale getirmek için kullanılan istemciye geri döndürür. Bu güvenli oturum oluşturma, SCT simetrik anahtar içerdiğinden daha verimli olmasını iki uç nokta arasında alınıp verilen iletileri kümesini etkinleştirir. Hangi X.509 sertifikaları üzerine dayalı, asimetrik anahtarlar simetrik ne zaman anahtarları daha önemli ölçüde daha fazla hesaplama gücü gerektiren bir dijital imza oluşturulurken veya veri kümesini şifreleme.  
  
 Önyükleme İlkesi (kısmında 6.2.7 [WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817) standart) kanalının güvenliğini sağlayın ve lk/SCT ve RSTR/SCT alışverişi yapılmadan önce istemcinin kimliğini doğrulamak için kullanılan ileti güvenlik onayı içeriyor. Bazı WCF standart bağlamaları sahip bir `Security.Message.EstablishSecurityContext` hangi denetimlerin olup güvenli konuşma özelliği kullanılır. Özel bağlamalar kullanırken önyükleme iç içe güvenlik bağlama öğeleri aracılığıyla belirtilir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyasında veya çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> kod.  
  
 Oturumlar hakkında daha fazla bilgi için bkz. [oturumları kullanarak](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
