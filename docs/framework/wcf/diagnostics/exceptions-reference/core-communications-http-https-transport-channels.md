---
title: "Temel iletişimler: HTTP-HTTPS taşıma kanalları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c0a23c9-a663-461c-bdab-58b4d3e23642
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d67bb810ced381749dca0dc698ca405bb59cfb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="core-communications-httphttps-transport-channels"></a>Çekirdek İletişimler: HTTP/HTTPS Taşıma Kanalları
Bu konu tarafından oluşturulan tüm özel durumları listeler [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] taşıma HTTP/HTTPS kanalları.  
  
## <a name="exception-list"></a>Özel durum listesi  
  
|Kaynak kodu|Kaynak dizesi|  
|-------------------|---------------------|  
|DigestExplicitCredsImpersonationLevel|Belirtilen kimliğe bürünme düzeyi belirtildi. HTTP Digest kimlik doğrulaması, yalnızca açık bir kimlik ile kullanıldığında 'Kimliğe bürünme' düzeyini destekler.|  
|FramingContentTypeMismatch|Belirtilen içerik türü belirtilen hizmeti tarafından desteklenmiyor. İstemci ve hizmet bağlamaları eşleşmiyor olabilir.|  
|Hosting_SslSettingsMisconfigured|Belirtilen hizmet için Güvenli Yuva Katmanı ayarları Internet Information Services içeriğiyle eşleşmiyor.|  
|HttpAuthSchemeAndClientCert|HTTPS dinleme fabrikası, bir istemci sertifikası ve belirtilen kimlik doğrulama şeması gerektirecek şekilde yapılandırıldı. Ancak, istemci kimlik doğrulaması, yalnızca bir formu bir kerede gerekli olabilir.|  
|HttpReceiveFailure|Belirtilen HTTP yanıt alınırken bir hata oluştu. Hizmet uç noktası bağlama HTTP protokolünü kullanarak değil. Başka bir olasılık bir HTTP istek bağlamı hizmet kapatılıyor nedeniyle sunucu tarafından sonlandırıldı olabilir. Daha fazla bilgi için sunucu günlüklerine bakın.|  
|HttpRegistrationAccessDenied|Belirtilen URL HTTP kaydedilemiyor. İşleminizi bu ad alanına erişim hakları yok (Ayrıntılar için http://msdn.microsoft.com/library/default.asp?url=/library/http/http/namespace_reservations_registrations_and_routing.asp bakın).|  
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
