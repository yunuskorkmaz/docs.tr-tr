---
title: 'Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 33df685b4d14130ae00d59012706b7637924c9be
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295438"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma
Windows Communication Foundation (WCF) Federasyon Hizmeti oluşturma ana aşağıdaki yordamlardan oluşur:  
  
1. Yapılandırma bir <xref:System.ServiceModel.WSFederationHttpBinding> ya da benzer özel bağlama. Uygun bir bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).  
  
2. Yapılandırma <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> hizmete sunulan nasıl verilen belirteçleri denetler doğrulanır.  
  
 Bu konuda, ikinci adım hakkında ayrıntılar sağlar. Federasyon hizmetinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Kodda IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. Kullanım <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> özelliği <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı bir başvuru döndürmek için bir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> örneği. Özellik erişilen <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> özelliği <xref:System.ServiceModel.ServiceHostBase> sınıfı.  
  
2. Ayarlama <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> özelliğini `true` varsa gibi Self verilen belirteçler [!INCLUDE[infocard](../../../../includes/infocard-md.md)] kartlardır doğrulanamaz. Varsayılan, `false` değeridir.  
  
3. Tarafından döndürülen bir koleksiyonda doldurmak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> örneklerini özelliğiyle <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı. Her örneği, hizmet belirteçleri kimliğini doğrulayacak bir veren temsil eder.  
  
    > [!NOTE]
    >  Tarafından döndürülen bir istemci-tarafı koleksiyonda aksine <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> özelliği, bilinen sertifika koleksiyonuna anahtarlanmış koleksiyon değil. Hizmet verilen belirtecin (tabidir, bu konunun ilerleyen bölümlerinde açıklanan daha fazla kısıtlama,) içeren ileti gönderen adresini bakılmaksızın belirtilen sertifikaları belirteçleri kabul eder.  
  
4. Ayarlama <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> özelliğini birine <xref:System.ServiceModel.Security.X509CertificateValidationMode> sabit listesi değerleri. Bu, yalnızca kod içinde yapılabilir. Varsayılan, <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A> değeridir.  
  
5. Varsa <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> özelliği <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, ardından özel bir örneği atamak <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfının <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> özelliği.  
  
6. Varsa <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> ayarlanır `ChainTrust` veya `PeerOrChainTrust`ayarlayın <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> özelliğini uygun bir değerden <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> sabit listesi. İptal modu kullanılmaz Not `PeerTrust` veya `Custom` doğrulama modları.  
  
7. Gerekirse, özel bir örneği atamak <xref:System.IdentityModel.Tokens.SamlSerializer> sınıfının <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> özelliği. Özel güvenlik onaylama işaretleme dili (SAML) seri hale getirici, örneğin, özel SAML onaylamalarını ayrıştırmak için gereklidir.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Yapılandırmada IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. Oluşturma bir `<issuedTokenAuthentication>` öğesi alt öğesi olarak bir <`serviceCredentials`> öğesi.  
  
2. Ayarlama `allowUntrustedRsaIssuers` özniteliği `<issuedTokenAuthentication>` öğesine `true` gibi Self verilen bir belirteç kimlik doğrulaması, bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] kart.  
  
3. Oluşturma bir `<knownCertificates>` öğesi alt öğesi olarak `<issuedTokenAuthentication>` öğesi.  
  
4. Sıfır veya daha fazla oluşturma `<add>` öğeleri alt öğeleri olarak `<knownCertificates>` öğesini kullanarak sertifikayı bulma belirtin `storeLocation`, `storeName`, `x509FindType`, ve `findValue` öznitelikleri.  
  
5. Gerekirse, ayarlayın `samlSerializer` özniteliği <`issuedTokenAuthentication`> özel tür adını öğesine <xref:System.IdentityModel.Tokens.SamlSerializer> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özelliklerini ayarlar bir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> kod.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Bir istemcinin kimliğini doğrulamak bir Federasyon Hizmeti için sırayla aşağıdakileri hakkında verilen belirtecin doğru olması gerekir:  
  
-   Dijital imza verilen belirtecin bir RSA güvenlik anahtarı tanımlayıcısı kullandığında <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> özelliği olmalıdır `true`.  
  
-   Tarafından döndürülen bir koleksiyonda, bir sertifika tarafından verilen belirtecinin imzası bir X.509 Verenin seri numarası, X.509 konu anahtarı tanımlayıcısı veya X.509 parmak izi güvenlik tanımlayıcısı kullandığında, verilen belirteç imzalanmalıdır <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliği<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>sınıfı.  
  
-   Verilen belirtecin bir X.509 sertifikası kullanılarak yeniden imzalandığında, başına değeri tarafından belirtilen semantiği sertifika doğrulamalıdır <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> olup sertifika bağlı olan tarafa gönderilen bağımsız olarak özelliği, bir <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> veya alınamadı gelen <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliği. X.509 Sertifika doğrulama hakkında daha fazla bilgi için bkz: [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Örneğin, ayarlamak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> için <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> herhangi verilen belirteç imzalama sertifikası konusu kimlik doğrulamasının `TrustedPeople` sertifika deposu. Bu durumda ayarlama <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> ya da özellik <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> veya <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>. Dahil olmak üzere Diğer modları, seçtiğiniz <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>. Zaman `Custom` olduğu belirlenirse, bir örneğini atamanız gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfının <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> özelliği. Özel Doğrulayıcı sağlayıcısı sertifikaları, beğeni herhangi bir ölçütü kullanarak doğrulayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federasyon ve Güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding güvenli oturumlarını devre dışı bırak](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [SecurityBindingElement Kimlik Doğrulama Modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
