---
title: "Federasyon ve Verilen Belirteçler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05a110318bbe92f18d0bc6becb453a5d7851821c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="federation-and-issued-tokens"></a>Federasyon ve Verilen Belirteçler
İle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], WS-Federasyon ve WS-Trust belirtimleri uygulayan Hizmetleri ile güvenli bir şekilde iletişim kuran istemciler oluşturabilirsiniz. Belirtimleri, kimlik doğrulama ve yetkilendirme farklı güven bölgelerinde etkinleştirmek mekanizmalar için XML, SOAP ve Web Hizmetleri Açıklama Dili (WSDL) kullanın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 Federasyon genel bir bakış sağlar.  
  
 [Federasyon ve güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 Ne zaman oluşturma hizmetleri veya istemciler Federasyon in farkında olması için tasarım konuları listeler.  
  
 [Nasıl yapılır: federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 İle federe istemci oluşturma temelleri açıklanır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Nasıl yapılır: federe bir hizmette kimlik bilgilerini yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 Bir Federasyon Hizmeti oluşturma adımları açıklanmaktadır.  
  
 [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 İstemcileri yapılandırmak açıklar ve hizmetleri kullanan `WSFederationHttpBinding`.  
  
 [Nasıl yapılır: bir güvenlik belirteci hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 Bir güvenlik belirteci hizmeti oluşturma adımları açıklanmaktadır.  
  
 [Güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteçleri ve talepleri](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 Genişletilebilir güvenlik onaylar biçimlendirme dili (SAML) belirteçleri ve zengin oluşturmanızı talep türleri etkinleştir açıklar.  
  
 [Nasıl yapılır: yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 Güvenlik belirteçlerinin yerel yayımlayan oluşturmayı açıklar.  
  
 [Nasıl yapılır: Güvenli WSFederationHttpBinding gücenli oturumlarını devre dışı bırak](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
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
 [Özel belirteçler](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
