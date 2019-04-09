---
title: Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: d2244ba42b1cf95f77424d32a19ebe11dd3a2a45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148713"
---
# <a name="security-considerations-for-secure-sessions"></a>Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdakileri dikkate almanız gerekir. Güvenlik konuları hakkında daha fazla bilgi için bkz. [güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) ve [en iyi güvenlik uygulamaları](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Güvenli oturumlar ve meta verileri  
 Güvenli bir oturum olduğunda kurulur ve <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği `false`, Windows Communication Foundation (WCF) gönderen bir `mssp:MustNotSendCancel` onaylama Web Hizmetleri Açıklama Dili (WSDL) belge için meta verilerde bir parçası olarak Hizmet uç noktası. `mssp:MustNotSendCancel` Onaylama hizmet güvenli oturum iptal isteklerine yanıt vermezse istemciler bildirir. Zaman <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği `true`, WCF ktıları sonra bir `mssp:MustNotSendCancel` onaylama WSDL belgesi. İstemciler artık güvenli oturum gerektirdiğinde hizmete bir iptal isteği Gönder beklenir. Bir istemci kullanarak oluşturulduğunda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), istemci kodu belirli bir varlığı veya yokluğuna göre uygun şekilde tepki verdiğini `mssp:MustNotSendCancel` onaylama.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Güvenli konuşma ve özel belirteçler  
 Özel belirteçler ve WS-SecureConversation belirtiminde tanımlanan şekilde nedeniyle türetilen anahtarlar karıştırma bazı sorunlar vardır. Belirtimi bildiren `wsse:SecurityTokenReference` türetilmiş belirteç başvuran isteğe bağlı bir öğedir: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Bu isteğe bağlı öğe, güvenlik bağlamı belirteci, güvenlik belirteci veya türetme için kullanılan paylaşılan anahtar/parola belirtmek için kullanılır. Belirtilmezse, alıcının ileti bağlamı paylaşılan anahtarı belirleyebilirsiniz varsayılır. Bağlam belirlenemiyorsa, ardından bir hata gibi `wsc:UnknownDerivationSource` harekete Geçirilmemesi gereken. "  
  
 Bu türetilmiş için özel bir belirteç isterseniz yan tümcesi türüne kaydıracağını anlamına gelir. bir `SecurityTokenReference` öğesi. Türetme devre dışı bırakma seçeneği yoktur, ancak anahtarları türetmek için varsayılandır. Bir anahtarı sarmalama başarısız olursa, türetilmiş anahtar belirtecinde seri hale getirme başarılı, ancak bu seri durumdan çalışılırken bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Güvenlik Değerlendirmeleri](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Güvenlik için En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
