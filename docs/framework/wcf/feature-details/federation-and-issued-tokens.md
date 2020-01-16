---
title: Federasyon ve Verilen Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: d566388279f9210f70ebdb5c42512aea0425a47e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964587"
---
# <a name="federation-and-issued-tokens"></a>Federasyon ve Verilen Belirteçler
Windows Communication Foundation (WCF) ile, WS-Federation ve WS-Trust belirtimlerini uygulayan hizmetlerle güvenli bir şekilde iletişim kuran istemciler oluşturabilirsiniz. Belirtimler, farklı güven bölgelerinde kimlik doğrulaması ve yetkilendirmeyi etkinleştiren mekanizmalar sağlamak üzere XML, SOAP ve Web Hizmetleri Açıklama Dili (WSDL) kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 Federasyona genel bakış sağlar.  
  
 [Federasyon ve Güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Federasyon Hizmetleri veya istemcileri oluştururken dikkat edilecek tasarım sorunlarını listeler.  
  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 WCF ile federe istemci oluşturma hakkında temel bilgileri açıklar.  
  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Federasyon hizmeti oluşturma adımlarını açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 `WSFederationHttpBinding`kullanan istemcilerin ve hizmetlerin nasıl yapılandırılacağını açıklar.  
  
 [Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Güvenlik belirteci hizmeti oluşturma adımlarını açıklar.  
  
 [Güvenlik Onaylama İşlemi İşaretleme Dili (SAML) Belirteçleri ve Talepleri](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Genişletilebilir olan ve zengin talep türleri oluşturmanızı sağlayan güvenlik onayları biçimlendirme dili (SAML) belirteçlerini açıklar.  
  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Güvenlik belirteçlerinin yerel olarak vereni oluşturmayı açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 `WSFederationHttpBinding`için güvenli oturumların nasıl devre dışı bırakılacağını açıklar. Her istemci için bir oturum gerektiren bir Web grubu oluşturulurken güvenli oturumların devre dışı bırakılması gerekir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yetkilendirme](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)
- [Özel Belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
