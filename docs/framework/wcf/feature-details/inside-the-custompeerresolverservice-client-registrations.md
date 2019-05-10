---
title: 'CustomPeerResolverService İçinde: İstemci Kayıtları'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: 3d1e1c6493da54bc3ae0e74a33985da59382ea52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619775"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>CustomPeerResolverService İçinde: İstemci Kayıtları
Uç nokta bilgilerini ağı içindeki her bir düğümün çözümleyicisini yayımlar `Register` işlevi. Çözümleyicisini bu bilgileri bir kayıt depolar. Bu kayıt, benzersiz tanımlayıcı (RegistrationId) ve düğüm (PeerNodeAddress) uç noktası bilgilerini içerir.  
  
## <a name="stale-records-and-expiration-time"></a>Eskimiş kayıtları ve süre sonu  
 İdeal olarak, bir düğüm kafes ayrıldığında, çağırır `Unregister` çözümleyicisini kayıt girdisini kaldırmak neden işlev. Bazı durumlarda, düğümleri kapatın veya çağırmadan önce erişilemez duruma `Unregister`, eski bir kaydı arkasında bırakma.  
  
 Çözümleyici hizmetinizdeki eskimiş kayıtları başarısız bağlantılar neden olabilir. Bir düğüm için ağ bağlantısı kurulurken çözümleyici hizmetinden eski bağlantı bilgilerini alırsa, başarıyla kafes katılmak için daha uzun sürebilir. Eskimiş kayıtları da belleği yararlanın. Etkili bir temizleme işlemi, kayıtları depolamak için kullanılan önbellek sonunda overflow ve çözümleyicisini kilitlenme.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Her kaydı bir sona erme saati (tarih/saat) ile işaretler ve bu bilgileri kaydının bir parçası depolar. Hizmet sona erme zamanı eskimiş kayıtları tanımlamak için kullanır. Özel uygulamalar benzer bir şey yapmanız gerekir.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval ve CleanupInterval  
 `RefreshInterval` Özelliği <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> kayıt kayıtları hizmetin kayıt arama tablosunda geçerli ne kadar süre beklediğini tanımlar. Ne zaman kayıt eski hale gelir ve silinmek üzere işaretlenmiş olan belirli bir kaydı için bu özelliği için sağlanan süre geçti.  
  
 `CleanupInterval` Özelliği <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> aramak ve eski kayıt kayıtları silmek için hizmetin ne sıklıkta söyler. `CleanupInterval` Değerinden büyük veya eşit bir süre için ayarlamanız gerekir `RefreshInterval` hizmette ayarlayın.  
  
 Kendi çözümleyicisini uygulamak için eski kayıt kayıtları kaldırmak için bir bakım işlevi yazmanız gerekir. Bunu yapmanın birkaç yolu vardır:  
  
- **Düzenli bakım**: Bir Zamanlayıcı, düzenli aralıklarla alarmın ve eski kayıtları silmek için data store ayarlayın. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> Bu yaklaşımı kullanır.  
  
- **Pasif silme**: Etkin bir şekilde eskimiş kayıtları için düzenli aralıklarla aramak yerine belirleyin ve hizmetinizi zaten başka bir işleve gerçekleştirirken eskimiş kayıtları silin. Bu büyük olasılıkla yanıt isteklerine çözümleyici istemcilerden yavaşlatabilir ancak bir zamanlayıcı gereksinimini ortadan ve az sayıda düğüm varsa daha verimli olmadan arama bırakmak beklenebilir `Unregister`.  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime ve yenileme  
 Bir düğüm ile çözümleyicisini kaydettiğinde, aldığı bir <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> hizmetinden nesne. Bu nesneye sahip bir `RegistrationLifetime` düğüme ne kadar zaman önce kayıt sahip süresi dolar ve çözümleyici hizmet tarafından kaldırılır gösteren özellik. Eğer, örneğin, `RegistrationLifetime` 2 dakika, düğüm çağırmayı gerektiren `Refresh` kaydı yeni kalır ve silinmediğinden emin olmak için altında 2 dakika içinde. Çözümleyicisini aldığında bir `Refresh` istek, kaydı arar ve sona erme zamanını sıfırlar. Yenileme döndürür bir <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> nesnesi ile bir `RegistrationLifetime` özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Çözücüler](../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
