---
title: Federasyon ve Verilen Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: b6a5411b74b53cb5e3b18cced7fd8fc09e9a9676
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="federation-and-issued-tokens"></a>Federasyon ve Verilen Belirteçler
Windows Communication Foundation (WCF) ile güvenli bir şekilde WS-Federasyon ve WS-Trust belirtimleri uygulayan Hizmetleri ile iletişim kuran istemciler oluşturabilirsiniz. Belirtimleri, kimlik doğrulama ve yetkilendirme farklı güven bölgelerinde etkinleştirmek mekanizmalar için XML, SOAP ve Web Hizmetleri Açıklama Dili (WSDL) kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 Federasyon genel bir bakış sağlar.  
  
 [Federasyon ve Güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Ne zaman oluşturma hizmetleri veya istemciler Federasyon in farkında olması için tasarım konuları listeler.  
  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 WCF ile federe istemci oluşturma temelleri açıklanır.  
  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Bir Federasyon Hizmeti oluşturma adımları açıklanmaktadır.  
  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 İstemcileri yapılandırmak açıklar ve hizmetleri kullanan `WSFederationHttpBinding`.  
  
 [Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Bir güvenlik belirteci hizmeti oluşturma adımları açıklanmaktadır.  
  
 [Güvenlik Onaylama İşlemi İşaretleme Dili (SAML) Belirteçleri ve Talepleri](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Genişletilebilir güvenlik onaylar biçimlendirme dili (SAML) belirteçleri ve zengin oluşturmanızı talep türleri etkinleştir açıklar.  
  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Güvenlik belirteçlerinin yerel yayımlayan oluşturmayı açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Güvenli oturumlar devre dışı bırakmanız açıklar bir `WSFederationHttpBinding`. Her istemci için bir oturum gerektiren bir Web grubu oluşturulurken güvenli oturumlar devre dışı bırakılması gereklidir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [Özel Belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
