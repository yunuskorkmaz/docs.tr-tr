---
title: Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: 587897cc296523e0bfd5a4d4fa50b1e145cb69fb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601055"
---
# <a name="security-considerations-for-secure-sessions"></a>Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
Güvenli oturumları uygularken güvenliği etkileyen aşağıdaki öğeleri göz önünde bulundurmanız gerekir. Güvenlik konuları hakkında daha fazla bilgi için bkz. Güvenlik [konuları](security-considerations-in-wcf.md) ve [güvenlik Için en iyi uygulamalar](best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Güvenli Oturumlar ve meta veriler  
 Güvenli bir oturum oluşturulduğunda ve <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özellik olarak ayarlandığında `false` , WINDOWS COMMUNICATION FOUNDATION (WCF) `mssp:MustNotSendCancel` hizmet uç noktası Için Web Hizmetleri Açıklama Dili (wsdl) belgesinde meta verilerin bir parçası olarak bir onaylama gönderir. `mssp:MustNotSendCancel`Onaylama, istemcilere hizmetin güvenli oturumu iptal etmek için isteklere yanıt vermemediğini bildirir. <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A>Özelliği olarak ayarlandığında `true` , WCF `mssp:MustNotSendCancel` WSDL belgesinde bir onaylama işlemi yapmaz. İstemcilerin artık güvenli oturum gerektirdiklerinde hizmete bir iptal isteği gönderilmesi beklenir. İstemci, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak oluşturulduğunda, istemci kodu onaylaması veya onay yokluğuna uygun şekilde davranır `mssp:MustNotSendCancel` .  
  
## <a name="secure-conversations-and-custom-tokens"></a>Güvenli konuşmalar ve özel belirteçler  
 WS-SecureConversation belirtiminde tanımlanma yöntemi nedeniyle özel belirteçleri ve türetilmiş anahtarları karıştırma konusunda bazı sorunlar vardır. Belirtim, `wsse:SecurityTokenReference` türetilmiş belirtece başvuran bir isteğe bağlı öğe olduğunu söyler: " `/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Bu isteğe bağlı öğe, türetme için kullanılan güvenlik bağlamı belirtecini, güvenlik belirtecini veya paylaşılan anahtar/gizli anahtarı belirtmek için kullanılır. Belirtilmemişse, alıcının ileti bağlamından paylaşılan anahtarı belirleyebilmesi varsayılır. Bağlam belirlenemiyorsa, gibi bir hata `wsc:UnknownDerivationSource` oluşmamalıdır. "  
  
 Bu, bir özel belirtecin türetilemeyeceğini istiyorsanız, yan tümce türünü bir öğesi içine sarmalısınız `SecurityTokenReference` . Türetmenin devre dışı bırakma seçeneği vardır, ancak varsayılan olarak anahtarlar türetilemiyor. Anahtarı sarmaya devam ederseniz, türetilmiş anahtar belirtecinin serileştirilmesi başarılı olur, ancak serisini kaldırmak için bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Güvenlik konuları](security-considerations-in-wcf.md)
- [Güvenlik için En İyi Uygulamalar](best-practices-for-security-in-wcf.md)
