---
description: 'Daha fazla bilgi edinin: temel Iletişimler: HTTP/HTTPS taşıma kanalları'
title: 'Temel Iletişimler: HTTP-HTTPS taşıma kanalları'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 585e7511a8c3291c09b40f5895bd700534e6faad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635915"
---
# <a name="core-communications-httphttps-transport-channels"></a>Temel İletişimler: HTTP/HTTPS Taşıma Kanalları

Bu konu, Windows Communication Foundation (WCF) aktarım HTTP/HTTPS kanalları tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Belirtilen kimliğe bürünme düzeyi belirtildi. HTTP Özet kimlik doğrulaması, açık bir kimlik bilgisiyle kullanıldığında yalnızca ' kimliğe bürünme ' düzeyini destekler.|  
|Framingcontenttypeuyuşmazlık|Belirtilen içerik türü belirtilen hizmet tarafından desteklenmiyor. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|Hosting_SslSettingsMisconfigured|Belirtilen hizmetin Güvenli Yuva Katmanı ayarları Internet Information Services ile eşleşmiyor.|  
|HttpAuthSchemeAndClientCert|HTTPS dinleyicisi fabrikası, bir istemci sertifikası ve belirtilen kimlik doğrulama düzeni gerektirecek şekilde yapılandırıldı. Bununla birlikte, tek seferde yalnızca bir istemci kimlik doğrulaması biçimi gerekli olabilir.|  
|HttpReceiveFailure|Belirtilen HTTP yanıtı alınırken bir hata oluştu. Hizmet uç noktası bağlaması HTTP protokolünü kullanmıyor olabilir. Başka bir olasılık da, bir hizmetin kapanmasından dolayı bir HTTP istek bağlamının sunucu tarafından sonlandırıldığı bir hizmettir. Daha fazla ayrıntı için sunucu günlüklerine bakın.|  
|Httpregistrationaccessreddedildi|HTTP belirtilen URL 'YI kaydedemiyor. İşleminiz bu ad alanına erişim haklarına sahip değil (Ayrıntılar için bkz. [ad alanı ayırmaları, kayıtlar ve yönlendirme](/windows/desktop/http/namespace-reservations-registrations-and-routing) ).|  
|HttpRegistrationAlreadyExists|HTTP belirtilen URL 'YI kaydedemiyor. Başka bir uygulama bu URL 'YI HTTP.SYS zaten kaydetti.|  
|Httpregistrationportınuse|Belirtilen TCP bağlantı noktası başka bir uygulama tarafından kullanıldığından, HTTP belirtilen URL 'YI kaydedemiyor.|  
|HttpSendFailure|Belirtilen HTTP isteği yapılırken bir hata oluştu. Nedenin bir güvenlik bağlama uyumsuzluğu olmadığından emin olun. Ayrıca hizmetin Güvenli Yuva Katmanı için yapılandırılmadığından emin olun.|  
|MessageXmlProtocolError|Ağdan alınan XML ile ilgili bir sorun oluştu. Daha fazla ayrıntı için iç özel duruma bakın.|  
|MissingContentType|Alıcı, belirtilen istekte içerik türünün eksik olduğunu gösteren bir hata döndürdü. Daha fazla bilgi için iç özel duruma bakın.|  
|ProxyAuthenticationLevelMismatch|HTTP proxy kimlik doğrulama kimlik bilgileri, hedef sunucu kimlik doğrulaması gereksiniminden daha sıkı bir karşılıklı kimlik doğrulama gereksinimini belirtti.|  
|Proxyımpersonationleveluyuşmazlığını|HTTP proxy kimlik doğrulama kimlik bilgileri, hedef sunucu kimlik doğrulaması kısıtlamasından daha sıkı bir kimliğe bürünme düzeyi kısıtlaması belirtti.|  
|SecureChannelFailure|Belirtilen yetkiliyle Güvenli Yuva Katmanı/Aktarım Katmanı Güvenliği için güvenli bir kanal oluşturulamıyor.|  
|TrustFailure hatası|Belirtilen yetkiliyle Güvenli Yuva Katmanı/Aktarım Katmanı Güvenliği güvenli kanalı için bir güven ilişkisi sağlanamadı.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|HttpTransportBinding öğesinde bir açık proxy adresi ve UseDefaultWebProxy = true belirtemezsiniz.|
