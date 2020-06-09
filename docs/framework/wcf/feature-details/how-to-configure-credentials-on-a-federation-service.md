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
ms.openlocfilehash: 05f35bbb7dbb34cd4067c407578038cbb4eff70f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599151"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma
Windows Communication Foundation (WCF) ' de, Federasyon hizmeti oluşturmak aşağıdaki ana yordamlardan oluşur:  
  
1. <xref:System.ServiceModel.WSFederationHttpBinding>Veya benzer bir özel bağlamayı yapılandırma. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md).  
  
2. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>Hizmet için sunulan verilen belirteçlerin nasıl doğrulandığını denetleyen öğesini yapılandırma.  
  
 Bu konu, İkinci adımla ilgili ayrıntıları sağlar. Federe bir hizmetin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Koddaki IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> <xref:System.ServiceModel.Description.ServiceCredentials> Bir örneğe başvuru döndürmek için sınıfının özelliğini kullanın <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> . Özelliğine, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> sınıfının özelliğinden erişilir <xref:System.ServiceModel.ServiceHostBase> .  
  
2. , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> `true` CardSpace kartları gibi kendi kendine verilen belirteçlerin kimlik doğrulamasından geçirilme özelliğini olarak ayarlayın. Varsayılan değer: `false`.  
  
3. Özelliği tarafından döndürülen koleksiyonu <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> sınıfının örnekleriyle doldurun <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> . Her örnek, hizmetin, belirteçlerin kimliğini doğrulayabileceği bir veren temsil eder.  
  
    > [!NOTE]
    > Özelliği tarafından döndürülen istemci tarafı koleksiyonun aksine <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> , bilinen sertifikalar koleksiyonu bir anahtarlı koleksiyon değildir. Hizmet, verilen belirteci içeren iletiyi gönderen istemcinin adresine bakılmaksızın belirtilen sertifikaların (Bu konunun ilerleyen kısımlarında açıklanan diğer kısıtlamalara bağlı olarak) ilgili belirteçleri kabul eder.  
  
4. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>Özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode> sabit listesi değerlerinden birine ayarlayın. Bu, yalnızca kodda yapılabilir. Varsayılan değer: <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A>.  
  
5. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>Özelliği olarak ayarlandıysa <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> , özelliğine özel sınıfın bir örneğini atayın <xref:System.IdentityModel.Selectors.X509CertificateValidator> <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> .  
  
6. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>Veya olarak ayarlandıysa `ChainTrust` `PeerOrChainTrust` , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> özelliği Numaralandırmadaki uygun bir değere ayarlayın <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> . İptal modunun `PeerTrust` veya doğrulama modlarında kullanılmadığını unutmayın `Custom` .  
  
7. Gerekirse, özelliğe özel bir sınıfın bir örneğini atayın <xref:System.IdentityModel.Tokens.SamlSerializer> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> . Özel bir güvenlik onaylama işlemi biçimlendirme dili (SAML) seri hale getirici, örneğin özel SAML onayları ayrıştırılırken gereklidir.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Yapılandırmada IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. Bir `<issuedTokenAuthentication>` <> öğesinin alt öğesi olarak bir öğe oluşturun `serviceCredentials` .  
  
2. `allowUntrustedRsaIssuers` `<issuedTokenAuthentication>` `true` Bir CardSpace kartı gibi bir otomatik olarak verilen belirtecin kimliği doğrulanmışsa, öğesinin özniteliğini olarak ayarlayın.  
  
3. Öğesinin `<knownCertificates>` alt öğesi olarak bir öğe oluşturun `<issuedTokenAuthentication>` .  
  
4. `<add>`Öğesinin alt öğesi olarak sıfır veya daha fazla öğe oluşturun `<knownCertificates>` ve,,, `storeLocation` `storeName` `x509FindType` ve `findValue` özniteliklerini kullanarak sertifikayı bulmayı belirtin.  
  
5. Gerekirse, `samlSerializer` <`issuedTokenAuthentication`> öğesinin özniteliğini özel sınıfın tür adı olarak ayarlayın <xref:System.IdentityModel.Tokens.SamlSerializer> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir içinde kodunun özelliklerini ayarlar <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> .  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Bir Federasyon hizmetinin bir istemcinin kimliğini doğrulayabilmesi için, verilen belirteç ile ilgili olarak aşağıdakilerin doğru olması gerekir:  
  
- Verilen belirtecin dijital imzası bir RSA güvenlik anahtarı tanımlayıcısı kullandığında, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> özelliği olmalıdır `true` .  
  
- Verilen belirtecin imzası bir X. 509.952 Issuer seri numarası, X. 509.952 konu anahtarı tanımlayıcısı veya X. 509.952 parmak izi güvenlik tanımlayıcısı kullandığında, verilen belirtecin, sınıfının özelliği tarafından döndürülen koleksiyondaki bir sertifika tarafından imzalanması gerekir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> .  
  
- Verilen belirteç bir X. 509.952 sertifikası kullanılarak imzalanmışsa, sertifikanın <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> bağlı olan tarafa bir <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> veya özelliğinden alınmış olmasına bakılmaksızın, sertifikanın, özelliğin değeri ile belirtilen semantiğe göre doğrulanması gerekir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> . X. 509.440 sertifika doğrulaması hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).  
  
 Örneğin, öğesini olarak ayarlamak <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> , <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> imza sertifikası sertifika deposunda olan verilen belirtecin kimliğini doğrular `TrustedPeople` . Bu durumda, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> özelliğini ya da olarak ayarlayın <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine> . Dahil olmak üzere diğer modları seçebilirsiniz <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> . Seçildiğinde `Custom` , özelliğine sınıfının bir örneğini atamanız gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> . Özel Doğrulayıcı, beğendiğini herhangi bir ölçüt kullanarak sertifikaları doğrulayabilir. Daha fazla bilgi için bkz. [nasıl yapılır: özel bir sertifika Doğrulayıcı kullanan bir hizmet oluşturma](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](federation.md)
- [Federasyon ve Güven](federation-and-trust.md)
- [Federasyon Örneği](../samples/federation-sample.md)
- [Nasıl yapılır: WSFederationHttpBinding Güvenli Oturumlarını Devre Dışı Bırakma](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding Oluşturma](how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe İstemci Oluşturma](how-to-create-a-federated-client.md)
- [Sertifikalarla Çalışma](working-with-certificates.md)
- [SecurityBindingElement Kimlik Doğrulama Modları](securitybindingelement-authentication-modes.md)
