---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 1ed037c548f1d833f2a20118ee1e017cd19e3391
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628246"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Olası bir komşu ile güvenlik el sıkışması başarısız oldu.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, güvenli komşu bağlantısı kurmaya çalışırken ortaya çıkar. Bu, yetersiz ya da yanlış kimlik bilgileri nedeniyle oluşabilir.  
  
 PeerChannel'a güçlü tanımlama için tek bir belirteç türü uygulanabilir yetkilendirme ve kimlik doğrulaması türüne göre bir güçlü kimlik modeli sağlayan X.509 sertifikalarını tanır. PeerChannel'a parolaları kullanarak basit uygulamalar için de destek sağlar. Parolaları, yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması gerçekleştirmek için kullanılamaz. Eşleri grubudur paylaştığı simetrik bir belirteç zor veya uygunsuz kaynak kimlik doğrulaması için kullanılacak olmasıdır.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm Komşuları uygun güvenlik kimlik bilgilerini kullandığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Eş Kanalı Güvenliği](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
