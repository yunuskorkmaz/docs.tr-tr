---
title: 'Temel İletişimler: HTTP-HTTPS taşıma kanalları'
ms.date: 03/30/2017
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
ms.openlocfilehash: 4c4a2537ae615943ffac299a8c8cd00c67094360
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998757"
---
# <a name="core-communications-httphttps-transport-channels"></a>Temel İletişimler: HTTP/HTTPS Taşıma Kanalları
Bu konu, Windows Communication Foundation (WCF) taşıma HTTP/HTTPS kanalları tarafından oluşturulan tüm özel durumları listeler.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Belirtilen kimliğe bürünme düzeyi belirtildi. HTTP Digest kimlik doğrulaması, yalnızca bir açık kimlik bilgileri ile kullanıldığında 'Kimliğe bürünme' düzeyini destekler.|  
|FramingContentTypeMismatch|Belirtilen içerik türü belirtilen hizmet tarafından desteklenmiyor. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|Hosting_SslSettingsMisconfigured|Belirtilen hizmet için Güvenli Yuva Katmanı ayarları, Internet Information Services içeriğiyle eşleşmiyor.|  
|HttpAuthSchemeAndClientCert|HTTPS dinleyici fabrikası, bir istemci sertifikası ve belirtilen kimlik doğrulama şeması gerektirecek şekilde yapılandırıldı. Ancak, istemci kimlik doğrulaması, yalnızca bir form tek seferde gerekli olabilir.|  
|HttpReceiveFailure|Belirtilen HTTP yanıtı alınırken bir hata oluştu. Hizmet uç noktası bağlaması HTTP protokolünü kullanarak değil. Bir HTTP isteği bağlamına hizmet kapatılıyor nedeniyle sunucu tarafından sonlandırıldı başka bir olasılıktır. Daha fazla ayrıntı için sunucu günlüklerine bakın.|  
|HttpRegistrationAccessDenied|Belirtilen URL HTTP kaydedilemiyor. İşleminiz bu ad alanı için erişim haklarına sahip olmayan (bkz [Namespace ayırmalar, kayıtlar ve yönlendirme](/windows/desktop/http/namespace-reservations-registrations-and-routing) Ayrıntılar için).|  
|HttpRegistrationAlreadyExists|Belirtilen URL HTTP kaydedilemiyor. Başka bir uygulama zaten bu URL ile HTTP kayıtlı. SYS.|  
|HttpRegistrationPortInUse|Belirtilen TCP bağlantı noktası başka bir uygulama tarafından kullanıldığı için belirtilen URL HTTP kaydedilemiyor.|  
|HttpSendFailure|Belirtilen HTTP isteği yaparken bir hata oluştu. Neden güvenlik bağlama uyumsuzluğu olmadığından emin olun. Ayrıca hizmet Güvenli Yuva katmanı için yapılandırılmadığından emin olun.|  
|MessageXmlProtocolError|Ağdan alınan XML ile ilgili bir sorun oluştu. Daha fazla ayrıntı için iç özel duruma bakın.|  
|MissingContentType|Alıcı, istekte belirtilen içerik türü eksik olduğunu bildiren bir hata döndürdü. Daha fazla bilgi için iç özel duruma bakın.|  
|ProxyAuthenticationLevelMismatch|HTTP proxy kimlik doğrulama bilgileri hedef sunucu kimlik doğrulaması için daha katı bir karşılıklı kimlik doğrulama gereksinimini belirtildi.|  
|ProxyImpersonationLevelMismatch|HTTP proxy kimlik doğrulama bilgileri hedef sunucu kimlik doğrulaması için bir kısıtlama katıdır bir kimliğe bürünme düzeyi kısıtlaması belirtildi.|  
|SecureChannelFailure|Güvenli bir kanal için Güvenli Yuva Katmanı/Aktarım Katmanı Güvenliği belirtilen yetkilisi ile iletişim kurulamıyor.|  
|TrustFailure|Güvenli Yuva katmanı için bir güven ilişkisi kurulamıyor / Aktarım Katmanı Güvenliği Güvenli kanal belirtilen yetkisine sahip.|  
|UseDefaultWebProxyCantBeUsedWithExplicitProxyAddress|Bir açık proxy adresi yanı sıra UseDefaultWebProxy belirtemezsiniz HttpTransportBinding öğeniz true =.|
