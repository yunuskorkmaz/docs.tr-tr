---
title: "Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3154080682d406598b47122c64cc856ff8cb1f15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-considerations-for-secure-sessions"></a>Güvenli Oturumlar için Güvenlikli İlgili Önemli Noktalar
Güvenli oturumlar uygularken güvenliğini etkileyen aşağıdaki öğeleri göz önünde bulundurmalısınız. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]güvenlik konuları Bkz [güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) ve [en iyi güvenlik uygulamaları](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Güvenli oturumlar ve meta veriler  
 Güvenli bir oturum zaman kurulur ve <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği ayarlanmış `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gönderir bir `mssp:MustNotSendCancel` onaylama meta veri Hizmeti uç noktası için Web Hizmetleri Açıklama Dili (WSDL) belgedeki bir parçası olarak. `mssp:MustNotSendCancel` Onaylama hizmet güvenli oturum iptal etmek için isteklerine yanıt vermemesine istemcileri bildirir. Zaman <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> özelliği ayarlanmış `true`, ardından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] değil yayma bir `mssp:MustNotSendCancel` WSDL belgesinde onaylama. İstemciler artık güvenli oturum gerektirdiğinde hizmete iptal etme isteği göndermek beklenir. Bir istemci kullanarak oluşturulduğunda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), istemci kodu varlığı veya yokluğuna göre uygun şekilde tepki verdiğini `mssp:MustNotSendCancel` onaylama.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Güvenli görüşmeler ve özel belirteçler  
 Özel belirteçler ve türetilen anahtarları WS-SecureConversation belirtiminde tanımlanan şekilde nedeniyle karıştırma bazı sorunlar vardır. Belirtimi bildiren `wsse:SecurityTokenReference` türetilmiş belirteci başvuruda bulunan bir isteğe bağlı bir öğedir: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Bu isteğe bağlı öğe güvenlik bağlamı belirteci, güvenlik belirteci ya da türetme için kullanılan paylaşılan anahtarı/parola belirtmek için kullanılır. Belirtilmezse, alıcı iletiyi bağlamından paylaşılan anahtar belirleyebilirsiniz varsayılır. Bağlam belirlenemiyorsa, ardından bir arıza gibi `wsc:UnknownDerivationSource` oluşmalıdır. "  
  
 Türetilmesi için özel bir belirteç isterseniz, onun yan tümcesi türü kaydırılacağını yani bir `SecurityTokenReference` öğesi. Türetme devre dışı bırakma seçeneği yoktur ancak anahtarlar türetilen varsayılandır. Anahtar kaydırma başarısız olursa, türetilen anahtar belirteci seri hale getirme başarılı olur, ancak bu seri çalışılırken bir özel durum oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Güvenli WSFederationHttpBinding gücenli oturumlarını devre dışı bırak](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [En iyi güvenlik uygulamaları](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
