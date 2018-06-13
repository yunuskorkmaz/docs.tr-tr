---
title: 'Temel iletişimler: HTTP-HTTPS taşıma kanalları'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: fbdb5b350425aad7108402dec939f036e971d053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473333"
---
# <a name="core-communications-httphttps-transport-channels"></a>Çekirdek İletişimler: HTTP/HTTPS Taşıma Kanalları
Bu konu, Windows Communication Foundation (WCF) aktarım HTTP/HTTPS kanalları tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Belirtilen kimliğe bürünme düzeyi belirtildi. HTTP Digest kimlik doğrulaması, yalnızca açık bir kimlik ile kullanıldığında 'Kimliğe bürünme' düzeyini destekler.|  
|FramingContentTypeMismatch|Belirtilen içerik türü belirtilen hizmeti tarafından desteklenmiyor. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|Hosting_SslSettingsMisconfigured|Belirtilen hizmet için Güvenli Yuva Katmanı ayarları Internet Information Services içeriğiyle eşleşmiyor.|  
|HttpAuthSchemeAndClientCert|HTTPS dinleme fabrikası, bir istemci sertifikası ve belirtilen kimlik doğrulama şeması gerektirecek şekilde yapılandırıldı. Ancak, istemci kimlik doğrulaması, yalnızca bir formu bir kerede gerekli olabilir.|  
|HttpReceiveFailure|Belirtilen HTTP yanıt alınırken bir hata oluştu. Hizmet uç noktası bağlama HTTP protokolünü kullanarak değil. Başka bir olasılık bir HTTP istek bağlamı hizmet kapatılıyor nedeniyle sunucu tarafından sonlandırıldı olabilir. Daha fazla bilgi için sunucu günlüklerine bakın.|  
|HttpRegistrationAccessDenied|Belirtilen URL HTTP kaydedilemiyor. İşleminizi bu ad alanına erişim hakları yok (bkz http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp Ayrıntılar için).|  
|HttpRegistrationAlreadyExists|Belirtilen URL HTTP kaydedilemiyor. Başka bir uygulama zaten bu URL ile HTTP kayıtlı. SYS.|  
|HttpRegistrationPortInUse|Belirtilen TCP bağlantı noktası başka bir uygulama tarafından kullanıldığından HTTP belirtilen URL kaydedilemiyor.|  
|HttpSendFailure|Belirtilen HTTP isteği yaparken bir hata oluştu. Neden bir güvenlik bağlama uyumsuzluğu olmadığından emin olun. Ayrıca hizmet Güvenli Yuva katmanı için yapılandırılmamış emin olun.|  
|MessageXmlProtocolError|Ağdan alındı XML ile ilgili bir sorun oluştu. Daha fazla ayrıntı için iç özel duruma bakın.|  
|MissingContentType|Alıcı, içerik türü istekte belirtilen eksik olduğunu bildiren bir hata döndürdü. Daha fazla bilgi için iç özel duruma bakın.|  
|ProxyAuthenticationLevelMismatch|HTTP proxy kimlik doğrulama bilgileri hedef sunucu kimlik doğrulaması için daha katı bir karşılıklı kimlik doğrulama gereksinimini belirtilmiş.|  
|ProxyImpersonationLevelMismatch|HTTP proxy kimlik doğrulama bilgileri hedef sunucu kimlik doğrulaması için kısıtlama daha katı bir kimliğe bürünme düzeyi kısıtlaması belirtildi.|  
|SecureChannelFailure|Güvenli bir kanal için Güvenli Yuva Katmanı/Aktarım Katmanı Güvenliği ile belirtilen yetkilisi kurulamıyor.|  
|TrustFailure|Güvenli Yuva katmanı için bir güven ilişkisi kurulamıyor / Aktarım Katmanı Güvenliği Güvenli kanal belirtilen yetkisine sahip.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Bir açık proxy adresi yanı sıra UseDefaultWebProxy belirtemezsiniz = true, HttpTransportBinding öğesindeki.|
