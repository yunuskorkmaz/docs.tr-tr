---
title: 'CustomPeerResolverService İçinde: İstemci Kayıtları'
ms.date: 03/30/2017
ms.assetid: 40236953-a916-4236-84a6-928859e1331a
ms.openlocfilehash: ce694408edbb40309d1750be49b8414ebcbce3f7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596844"
---
# <a name="inside-the-custompeerresolverservice-client-registrations"></a>CustomPeerResolverService İçinde: İstemci Kayıtları
Kafesteki her düğüm, kendi uç nokta bilgilerini işlev aracılığıyla çözümleyici hizmetine yayımlar `Register` . Çözümleyici Hizmeti bu bilgileri kayıt kaydı olarak depolar. Bu kayıt, düğüm için benzersiz bir tanımlayıcı (RegistrationId) ve uç nokta bilgileri (PeerNodeAddress) içerir.  
  
## <a name="stale-records-and-expiration-time"></a>Eski kayıtlar ve sona erme saati  
 İdeal olarak, bir düğüm ağı terk ettiğinde, `Unregister` çözümleyici hizmetinin kayıt girdisini kaldırmasına neden olan işlevini çağırır. Bazen düğümler `Unregister` , eski bir kayıt kaydının arkasında bırakarak, çağrılmadan önce kapanır veya erişilemez duruma gelir.  
  
 Çözümleyici hizmetinizdeki eski kayıtlar başarısız bağlantılara neden olabilir. Bir ağ bağlantısını bağlamaya çalışan bir düğüm, çözümleyici hizmetinden eski bağlantı bilgilerini alırsa, bu, kafesin başarıyla katılması daha uzun sürebilir. Eski kayıtlar da bellek alır. Etkili bir temizleme işlemi olmadan, kayıtları depolamak için kullanılan önbellek, son olarak çözümleyici hizmetini temizleyebilir ve çökebilir.  
  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Her kaydı bir sona erme saati (DateTime) ile işaretler ve bu bilgileri kaydın bir parçası olarak depolar. Hizmet eski kayıtları tanımlamak için sona erme süresini kullanır. Özel uygulamalar benzer bir şeyler yapmanız gerekir.  
  
## <a name="refreshinterval-and-cleanupinterval"></a>RefreshInterval ve CleanupInterval  
 `RefreshInterval`Öğesinin özelliği, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> kayıt kayıtlarının hizmetin kayıt arama tablosunda ne kadar süreyle geçerli kalacağını tanımlar. Bu özelliğe sağlanan süre miktarı belirli bir kayıt için geçtiğinde, bu kayıt eskimiş olur ve silinmek üzere işaretlenir.  
  
 `CleanupInterval`Öğesinin özelliği, <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService> hizmete eski kayıt kayıtlarını ne sıklıkla arayacağını ve sildiğini söyler. `CleanupInterval`Hizmetin, hizmette ayarlanan değere eşit veya ondan daha büyük bir zamana ayarlanmış olması gerekir `RefreshInterval` .  
  
 Kendi çözümleyici hizmetinizi uygulamak için, eski kayıt kayıtlarını kaldırmak üzere bir bakım işlevi yazmanız gerekir. Bunu yapmak için çeşitli yollar vardır:  
  
- **Düzenli bakım**: bir zamanlayıcıyı düzenli aralıklarla kapatılacak şekilde ayarlayın ve eski kayıtları silmek için Veri deponuzdan ilerleyin. <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>Bu yaklaşımı kullanır.  
  
- **Pasif silme**: eski kayıtları düzenli aralıklarla etkin şekilde aramak yerine, hizmetiniz zaten başka bir işlev gerçekleştirirken eski kayıtları tanımlayabilir ve silebilirsiniz. Bu durum, çözümleyici istemcilerinden gelen isteklere yanıt süresini yavaşlatabilir, ancak bir Zamanlayıcı gereksinimini ortadan kaldırır ve çok sayıda düğümün çağrılmadan bırakması bekleniyorsa daha verimli olabilir `Unregister` .  
  
## <a name="registrationlifetime-and-refresh"></a>RegistrationLifetime ve Yenile  
 Bir düğüm çözümleyici hizmetine kaydolduktan sonra <xref:System.ServiceModel.PeerResolvers.RegisterResponseInfo> hizmetten bir nesne alır. Bu nesne, `RegistrationLifetime` kayıt süresi dolmadan önce düğüme ne kadar zaman kaldığını ve çözümleyici hizmeti tarafından kaldırılması gerektiğini belirten bir özelliğe sahiptir. Örneğin, `RegistrationLifetime` 2 dakikadır, düğümün, `Refresh` kaydın yeni kalmasını sağlamak ve silinmediğinden emin olmak için 2 dakika altında çağrı yapması gerekir. Çözümleyici hizmeti bir `Refresh` istek aldığında, kaydı arar ve sona erme süresini sıfırlar. Refresh <xref:System.ServiceModel.PeerResolvers.RefreshResponseInfo> özelliği ile bir nesne döndürür `RegistrationLifetime` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Çözücüler](peer-resolvers.md)
