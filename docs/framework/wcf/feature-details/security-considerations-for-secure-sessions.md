---
title: Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f4ee56204d6980f412b9781868714dedb3c2675c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-considerations-for-secure-sessions"></a>Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdaki öğeleri göz önünde bulundurmalısınız. Güvenlik konuları hakkında daha fazla bilgi için bkz: [güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) ve [en iyi güvenlik uygulamaları](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Güvenli oturumlar ve meta veriler  
 Güvenli bir oturum zaman kurulur ve <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği ayarlanmış `false`, Windows Communication Foundation (WCF) gönderir bir `mssp:MustNotSendCancel` ve Web Hizmetleri Açıklama Dili (WSDL) belge için meta veriler bir parçası olarak onaylama Hizmet uç noktası. `mssp:MustNotSendCancel` Onaylama hizmet güvenli oturum iptal etmek için isteklerine yanıt vermemesine istemcileri bildirir. Zaman <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği ayarlanmış `true`, WCF değil yayma sonra bir `mssp:MustNotSendCancel` WSDL belgesinde onaylama. İstemciler artık güvenli oturum gerektirdiğinde hizmete iptal etme isteği göndermek beklenir. Bir istemci kullanarak oluşturulduğunda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), istemci kodu varlığı veya yokluğuna göre uygun şekilde tepki verdiğini `mssp:MustNotSendCancel` onaylama.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Güvenli görüşmeler ve özel belirteçler  
 Özel belirteçler ve türetilen anahtarları WS-SecureConversation belirtiminde tanımlanan şekilde nedeniyle karıştırma bazı sorunlar vardır. Belirtimi bildiren `wsse:SecurityTokenReference` türetilmiş belirteci başvuruda bulunan bir isteğe bağlı bir öğedir: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Bu isteğe bağlı öğe güvenlik bağlamı belirteci, güvenlik belirteci ya da türetme için kullanılan paylaşılan anahtarı/parola belirtmek için kullanılır. Belirtilmezse, alıcı iletiyi bağlamından paylaşılan anahtar belirleyebilirsiniz varsayılır. Bağlam belirlenemiyorsa, ardından bir arıza gibi `wsc:UnknownDerivationSource` oluşmalıdır. "  
  
 Türetilmesi için özel bir belirteç isterseniz, onun yan tümcesi türü kaydırılacağını yani bir `SecurityTokenReference` öğesi. Türetme devre dışı bırakma seçeneği yoktur ancak anahtarlar türetilen varsayılandır. Anahtar kaydırma başarısız olursa, türetilen anahtar belirteci seri hale getirme başarılı olur, ancak bu seri çalışılırken bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Güvenlik için En İyi Uygulamalar](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
