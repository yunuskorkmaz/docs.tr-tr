---
title: "Güvenli İletişimler ve Güvenli Oturumlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d519640c40daf248a01a19f0450f3aea8de6cc04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="secure-conversations-and-secure-sessions"></a>Güvenli İletişimler ve Güvenli Oturumlar
Bir özellik olan [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] birbirinin kimliğini doğrular ve bir şifreleme ve dijital imza işlemi sırasında kabul iki uç noktalar arasında güvenli oturumları yeteneğidir. Örneğin, hizmet uç noktası kimlik doğrulaması için bir X.509 sertifikası bağlı bir güvenlik belirteci göndermek için bir istemci uç noktası gerektirebilir. İstemci kimlik doğrulaması gerçekleştikten sonra hizmet uç noktası bir güvenlik bağlamı belirteci (SCT) sonra oturum içinde tüm sonraki iletileri güvenli hale getirmek için kullanılan istemciye geri döndürür. Bu güvenli oturum oluşturma, bir simetrik anahtar SCT sahip olduğundan daha verimli olmasını iki uç noktaları arasında alınıp verilen iletileri kümesi sağlar. Asimetrik anahtarlar, hangi X.509 sertifikaları dayalı olarak, simetrik ne zaman anahtarları daha önemli ölçüde daha fazla hesaplama gücüne gerektiren bir dijital imza oluşturulurken veya veri kümesi şifreleme.  
  
 Önyükleme İlkesi (bölümünü 6.2.7 tanımlanan [WS-SecurityPolicy](http://go.microsoft.com/fwlink/?LinkId=99817) standart) güvenli kanal ve RST/SCT ve RSTR/SCT exchange önce istemci kimlik doğrulaması için kullanılan ileti güvenlik onayı içeriyor. Belirli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] standart bağlamaları sahip bir `Security.Message.EstablishSecurityContext` hangi denetimlerin olup güvenli konuşma özelliği kullanılır. Özel bağlamalar kullanırken önyükleme iç içe güvenlik bağlama öğeleri, yoluyla belirtilir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) yapılandırma dosyasında ya da çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> kod.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]oturumları, bkz: [kullanarak oturumları](../../../../docs/framework/wcf/using-sessions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oturumlar, Örnek Oluşturma ve Eşzamanlılık](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [Nasıl yapılır: Oturum Gerektiren Bir Hizmet Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
