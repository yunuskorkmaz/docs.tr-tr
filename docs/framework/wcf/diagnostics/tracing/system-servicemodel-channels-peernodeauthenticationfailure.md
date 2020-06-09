---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577311"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Olası bir komşuyla güvenlik el sıkışması başarılı olmadı.  
  
## <a name="description"></a>Açıklama  
 Bu izleme, güvenli bir komşu bağlantı kurmaya çalışırken oluşur. Bu durum yetersiz veya hatalı kimlik bilgileri nedeniyle oluşabilir.  
  
 PeerChannel, uygulanabilen kimlik doğrulaması ve yetkilendirme türüne göre güçlü bir kimlik modeli sağlayan, güçlü tanımlama, X. 509.440 sertifikaları için tek bir belirteç türünü tanır. PeerChannel Ayrıca parolaların kullanımı aracılığıyla basit uygulamalar için destek sağlar. Parolalar yalnızca oturum girişine izin vermek için kullanılabilir; ileti kimlik doğrulaması yapmak için kullanılamaz. Bunun nedeni, bir eş payı grubunun paylaştığı bir simetrik belirtecin zor ve kaynak kimlik doğrulaması için kullanılmak üzere uygun olmadığı bir değer.  
  
## <a name="troubleshooting"></a>Sorun giderme  
 Tüm komşuların uygun güvenlik kimlik bilgilerine sahip olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Eş Kanalı Güvenliği](../../feature-details/peer-channel-security.md)
- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
