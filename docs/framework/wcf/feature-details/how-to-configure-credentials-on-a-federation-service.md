---
title: "Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 243dbd73d60577cbda2d8cf4fad1fd2e510d87ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma
İçinde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], Federasyon Hizmeti oluşturma, aşağıdaki ana yordamlardan oluşur:  
  
1.  Yapılandırma bir <xref:System.ServiceModel.WSFederationHttpBinding> ya da benzer özel bağlama. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]uygun bir bağlama bkz [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2.  Yapılandırma <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> hizmete sunulan nasıl verilen belirteçler denetimleri doğrulanır.  
  
 Bu konuda, ikinci adım hakkında ayrıntılar sağlar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Federasyon hizmetinin çalıştığı bkz [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Kodda IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1.  Kullanım <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> özelliği <xref:System.ServiceModel.Description.ServiceCredentials> bir başvuru döndürmek için sınıf bir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> örneği. Özellik Şeritteki <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği <xref:System.ServiceModel.ServiceHostBase> sınıfı.  
  
2.  Ayarlamak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> özelliğine `true` varsa gibi kendi kendine verilen belirteçler [!INCLUDE[infocard](../../../../includes/infocard-md.md)] kartlardır doğrulanamaz. Varsayılan, `false` değeridir.  
  
3.  Tarafından döndürülen koleksiyon doldurmak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> örneklerini özelliğiyle <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı. Her örneği hizmet belirteçleri kimliğini doğrulayacak bir veren temsil eder.  
  
    > [!NOTE]
    >  Tarafından döndürülen istemci-tarafı koleksiyonu aksine <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği, bilinen sertifikalar koleksiyonu anahtarlı koleksiyonu değil. Hizmet verilen belirteç (bağlı olarak bu konunun ilerleyen bölümlerinde açıklanan başka kısıtlamalar,) içeren iletiyi gönderen istemci adresi bakılmaksızın belirtilen sertifikaları belirteçleri kabul eder.  
  
4.  Ayarlama <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> özelliğini birine <xref:System.ServiceModel.Security.X509CertificateValidationMode> numaralandırma değerleri. Bu, yalnızca kodda yapılabilir. Varsayılan, <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A> değeridir.  
  
5.  Varsa <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> özelliği ayarlanmış <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, özel bir örneğini atamak <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfının <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> özelliği.  
  
6.  Varsa <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> ayarlanır `ChainTrust` veya `PeerOrChainTrust`ayarlayın <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> uygun bir değerden özelliğine <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> numaralandırması. İptal modu kullanılmaz Not `PeerTrust` veya `Custom` doğrulama modları.  
  
7.  Gerekirse, özel bir örneği atamak <xref:System.IdentityModel.Tokens.SamlSerializer> sınıfının <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> özelliği. Özel güvenlik onaylar biçimlendirme dili (SAML) seri hale getirici, örneğin, özel SAML onaylar ayrıştırmak için gereklidir.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Yapılandırmada IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1.  Oluşturma bir `<issuedTokenAuthentication>` öğesi bir alt öğesi olarak bir <`serviceCredentials`> öğesi.  
  
2.  Ayarlama `allowUntrustedRsaIssuers` özniteliği `<issuedTokenAuthentication>` öğesine `true` otomatik olarak verilen bir belirteç gibi kimlik doğrulaması, bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] kart.  
  
3.  Oluşturma bir `<knownCertificates>` öğesi bir alt öğesi olarak `<issuedTokenAuthentication>` öğesi.  
  
4.  Sıfır veya daha fazla oluşturmak `<add>` öğeleri alt öğeleri olarak `<knownCertificates>` öğesi ve sertifika kullanılarak bulmak nasıl belirtin `storeLocation`, `storeName`, `x509FindType`, ve `findValue` öznitelikleri.  
  
5.  Gerekirse, ayarlamak `samlSerializer` özniteliği <`issuedTokenAuthentication`> özel tür adını öğesine <xref:System.IdentityModel.Tokens.SamlSerializer> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özelliklerini ayarlar bir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> kod.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Bir istemci kimlik doğrulaması bir Federasyon Hizmeti için sırayla aşağıdakileri hakkında verilen belirteç doğru olması gerekir:  
  
-   Verilen belirtecin dijital imza bir RSA güvenlik anahtarı tanımlayıcısı kullandığında <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> olmalıdır `true`.  
  
-   Bir sertifika tarafından döndürülen koleksiyonundaki tarafından verilen belirtecinin imzası bir X.509 Verenin seri numarası, X.509 konu anahtarı tanımlayıcısı veya X.509 parmak izi güvenlik tanımlayıcısı kullandığında, verilen belirteç imzalanmalıdır <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliği<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>sınıfı.  
  
-   Verilen belirteç X.509 sertifikası kullanarak imzalandığında sertifika değeri tarafından belirtilen semantiği başına doğrulamalısınız <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> olup bağlı olan taraf sertifika gönderildiği bakılmaksızın özelliği, bir <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> veya alındı gelen <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliği. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]X.509 sertifikasının bkz [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Örneğin, ayarlama <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> için <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> herhangi verilen belirteç imzalama sertifikası konusu kimlik doğrulamasının `TrustedPeople` sertifika deposu. Bu durumda, ayarlamak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> ya da özellik <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> veya <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Dahil olmak üzere Diğer modları, seçebileceğiniz <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Zaman `Custom` olan seçili örneği atamalısınız <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfının <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> özelliği. Özel Doğrulayıcı sertifikaları, yöntemlerine herhangi bir ölçütü kullanarak doğrulayabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Federasyon ve Güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Nasıl yapılır: WSFederationHttpBinding Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [Nasıl yapılır: Federe İstemci Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [SecurityBindingElement Kimlik Doğrulama Modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
