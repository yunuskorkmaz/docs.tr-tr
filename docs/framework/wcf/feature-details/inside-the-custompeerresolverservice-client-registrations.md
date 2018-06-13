---
title: 'CustomPeerResolverService İçinde: İstemci Kayıtları'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 1f8b6f5ac3a41fdc7f817553693b0621ee0ea3de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494062"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>CustomPeerResolverService İçinde: İstemci Kayıtları
Uç nokta bilgileri kafes içindeki her bir düğümün Çözümleyici hizmeti aracılığıyla yayımlar `Register` işlevi. Çözümleyici hizmeti bu bilgileri bir kayıt depolar. Bu kayıt, benzersiz bir tanımlayıcı (RegistrationId) ve düğüm için uç nokta bilgileri (PeerNodeAddress) içerir.  
  
## <a name="stale-records-and-expiration-time"></a>Eskimiş kayıtları ve süre sonu  
 İdeal olarak, bir düğüm kafes ayrıldığında çağırır `Unregister` çözümleyicisini kayıt girişi kaldırmak neden işlev. Bazı durumlarda, düğümleri kapatıldı veya çağırmadan önce erişilemez hale `Unregister`, eski bir kayıt arkasında bırakma.  
  
 Çözümleyici hizmetinizde eskimiş kayıtları bağlantının başarısız olmasına neden. Bir kafes bağlanmaya çalışırken bir düğümü eski bağlantı bilgilerini çözme hizmetinden alırsa, kafes başarıyla katılmaya uzun sürebilir. Eskimiş kayıtları de bellekte olur. Bir etkili temizleme işlemi, kayıtları depolamak için kullanılan önbellek sonunda Taşması ve çözümleyicisini kilitlenme.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Her kaydıyla sona erme süresi (saat) işaretler ve bu bilgileri kaydının bir parçası depolar. Hizmet sona erme zamanı eskimiş kayıtları tanımlamak için kullanır. Özel uyarlama benzer bir şey yapmanız gerekir.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval ve CleanupInterval  
 `RefreshInterval` Özelliği <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> ne kadar süreyle kayıt kayıtları hizmetin kayıt arama tablosunda geçerli kalır tanımlar. Ne zaman kaydını eski haline gelir ve silinmek üzere işaretlenmiş verilen bir kayıt için bu özelliğe sağlanan süre geçti.  
  
 `CleanupInterval` Özelliği <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> aramak ve eski kayıt kayıtları silmek için hizmet ne sıklıkta söyler. `CleanupInterval` Değerinden büyük veya eşit bir süre için ayarlanmalıdır `RefreshInterval` hizmette ayarlayın.  
  
 Kendi çözümleyicisini uygulamak için eski kayıt kayıtlarını kaldırmak için bir bakım işlevi yazmanız gerekir. Bunu yapmanın birkaç yolu vardır:  
  
-   **Düzenli bakım**: düzenli aralıklarla kapalı ve eski kayıtları silmek için veri deposu Git gitmek için bir zamanlayıcı ayarlayın. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Bu yaklaşımı kullanır.  
  
-   **Pasif silme**: eskimiş kayıtları için düzenli aralıklarla etkin olarak aramak yerine, tanımlamak ve hizmetiniz zaten başka bir işlev gerçekleştirirken eskimiş kayıtları silin. Bu büyük olasılıkla yanıt isteklerine çözümleyici istemcilerden yavaşlatabilir ancak bir süreölçer gereksinimini ortadan kaldırır ve az sayıda düğüm varsa daha verimli arama olmadan bırakmak için beklenen bir durum olabilir `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime ve yenileme  
 Bir düğüm çözümleyicisini ile kaydolduğunda, aldığı bir <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> hizmetinden nesnesi. Bu nesneye sahip bir `RegistrationLifetime` ne kadar zaman önce kayıt var. süresi dolar ve Çözümleyici hizmeti tarafından kaldırılır düğüme belirten özellik. Örneğin, eğer `RegistrationLifetime` 2 dakika, düğüm çağırmayı gerektiren `Refresh` kaydı yeni kalır ve silinmez emin olmak için altında 2 dakika içinde. Ne zaman çözümleyicisini alır bir `Refresh` istek, kaydı arar ve bitiş zamanını sıfırlar. Döndürür Yenile bir <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> nesnesi ile bir `RegistrationLifetime` özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Çözücüler](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
