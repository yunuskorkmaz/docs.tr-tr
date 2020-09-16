---
title: Federasyon ve Verilen Belirteçler
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: dffba51c1bf1aaffbed8725aafc96fd747cb31c6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559258"
---
# <a name="federation-and-issued-tokens"></a>Federasyon ve Verilen Belirteçler
Windows Communication Foundation (WCF) ile, WS-Federation ve WS-Trust belirtimlerini uygulayan hizmetlerle güvenli bir şekilde iletişim kuran istemciler oluşturabilirsiniz. Belirtimler, farklı güven bölgelerinde kimlik doğrulaması ve yetkilendirmeyi etkinleştiren mekanizmalar sağlamak üzere XML, SOAP ve Web Hizmetleri Açıklama Dili (WSDL) kullanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Federasyon](federation.md)  
 Federasyona genel bakış sağlar.  
  
 [Federasyon ve Güven](federation-and-trust.md)  
 Federasyon Hizmetleri veya istemcileri oluştururken dikkat edilecek tasarım sorunlarını listeler.  
  
 [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)  
 WCF ile federe istemci oluşturma hakkında temel bilgileri açıklar.  
  
 [Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma](how-to-configure-credentials-on-a-federation-service.md)  
 Federasyon hizmeti oluşturma adımlarını açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](how-to-create-a-wsfederationhttpbinding.md)  
 Kullanan istemcilerin ve hizmetlerin nasıl yapılandırılacağını açıklar `WSFederationHttpBinding` .  
  
 [Nasıl yapılır: Güvenlik Belirteci Hizmeti Oluşturma](how-to-create-a-security-token-service.md)  
 Güvenlik belirteci hizmeti oluşturma adımlarını açıklar.  
  
 [Güvenlik Onaylama İşlemi İşaretleme Dili (SAML) Belirteçleri ve Talepleri](saml-tokens-and-claims.md)  
 Genişletilebilir olan ve zengin talep türleri oluşturmanızı sağlayan güvenlik onayları biçimlendirme dili (SAML) belirteçlerini açıklar.  
  
 [Nasıl yapılır: Yerel Yayımlayan Yapılandırma](how-to-configure-a-local-issuer.md)  
 Güvenlik belirteçlerinin yerel olarak vereni oluşturmayı açıklar.  
  
 [Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Bir üzerinde güvenli oturumların nasıl devre dışı bırakılacağını açıklar `WSFederationHttpBinding` . Her istemci için bir oturum gerektiren bir Web grubu oluşturulurken güvenli oturumların devre dışı bırakılması gerekir.  
  
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

- [Yetkilendirme](authorization-in-wcf.md)
- [Özel Belirteçler](../extending/custom-tokens.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
