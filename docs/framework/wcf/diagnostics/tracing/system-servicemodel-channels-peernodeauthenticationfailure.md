---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 633f497950ab14d7715537eed8f5cc80e7a350a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33479859"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Olası komşu ile güvenlik el sıkışması başarısız oldu.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, bir güvenli komşu bağlantısı kurmaya çalışırken oluşur. Yetersiz veya yanlış kimlik bilgileri nedeniyle oluşabilir.  
  
 PeerChannel'a tek bir belirteç türü güçlü kimlik için kimlik doğrulama ve yetkilendirme uygulanabilir türüne göre bir güçlü kimlik modeli sağlar X.509 sertifikalarını tanır. PeerChannel'a, parolaları ile basit uygulamalar için de destek sağlar. Parolalar, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz. Eşleri grubudur paylaşan simetrik belirteç zor ve kaynak kimlik doğrulaması için kullanılacak uygun olmasıdır.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm Komşuları uygun güvenlik kimlik bilgilerini olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eş Kanalı Güvenliği](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
