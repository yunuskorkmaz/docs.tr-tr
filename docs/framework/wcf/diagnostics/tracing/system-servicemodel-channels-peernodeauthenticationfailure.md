---
description: ': System. ServiceModel. Channels. PeerNodeAuthenticationFailure hakkında daha fazla bilgi edinin'
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 751202abd3e199a03fc4ee0bf1252d4a8027e0cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634940"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure

Olası bir komşuyla güvenlik el sıkışması başarılı olmadı.  
  
## <a name="description"></a>Description  

 Bu izleme, güvenli bir komşu bağlantı kurmaya çalışırken oluşur. Bu durum yetersiz veya hatalı kimlik bilgileri nedeniyle oluşabilir.  
  
 PeerChannel, uygulanabilen kimlik doğrulaması ve yetkilendirme türüne göre güçlü bir kimlik modeli sağlayan, güçlü tanımlama, X. 509.440 sertifikaları için tek bir belirteç türünü tanır. PeerChannel Ayrıca parolaların kullanımı aracılığıyla basit uygulamalar için destek sağlar. Parolalar yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması yapmak için kullanılamaz. Bunun nedeni, bir eş payı grubunun paylaştığı bir simetrik belirtecin zor ve kaynak kimlik doğrulaması için kullanılmak üzere uygun olmadığı bir değer.  
  
## <a name="troubleshooting"></a>Sorun giderme  

 Tüm komşuların uygun güvenlik kimlik bilgilerine sahip olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanalı Güvenliği](../../feature-details/peer-channel-security.md)
- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
