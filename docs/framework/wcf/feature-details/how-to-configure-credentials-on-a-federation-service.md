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
ms.openlocfilehash: 792d2f1b113c0743bd91ccf2f7ff894d7f7d319f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912192"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma
Windows Communication Foundation (WCF) ' de, Federasyon hizmeti oluşturmak aşağıdaki ana yordamlardan oluşur:  
  
1. Veya benzer <xref:System.ServiceModel.WSFederationHttpBinding> bir özel bağlamayı yapılandırma. Uygun bağlama oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)oluşturun.  
  
2. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> Hizmet için sunulan verilen belirteçlerin nasıl doğrulandığını denetleyen öğesini yapılandırma.  
  
 Bu konu, İkinci adımla ilgili ayrıntıları sağlar. Federe bir hizmetin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md).  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>Koddaki IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> Bir <xref:System.ServiceModel.Description.ServiceCredentials> örneğe başvurudöndürmekiçinsınıfınınözelliğinikullanın.<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> Özelliğine, <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> <xref:System.ServiceModel.ServiceHostBase> sınıfının özelliğinden erişilir.  
  
2. , <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> CardSpace kartları gibi `true` kendi kendine verilen belirteçlerin kimlik doğrulamasından geçirilme özelliğini olarak ayarlayın. Varsayılan, `false` değeridir.  
  
3. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> Özelliği tarafından döndürülen koleksiyonu <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfının örnekleriyle doldurun. Her örnek, hizmetin, belirteçlerin kimliğini doğrulayabileceği bir veren temsil eder.  
  
    > [!NOTE]
    > <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> Özelliği tarafından döndürülen istemci tarafı koleksiyonun aksine, bilinen sertifikalar koleksiyonu bir anahtarlı koleksiyon değildir. Hizmet, verilen belirteci içeren iletiyi gönderen istemcinin adresine bakılmaksızın belirtilen sertifikaların (Bu konunun ilerleyen kısımlarında açıklanan diğer kısıtlamalara bağlı olarak) ilgili belirteçleri kabul eder.  
  
4. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Özelliğini <xref:System.ServiceModel.Security.X509CertificateValidationMode> sabit listesi değerlerinden birine ayarlayın. Bu, yalnızca kodda yapılabilir. Varsayılan, <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A> değeridir.  
  
5. Özelliği olarak <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>ayarlandıysa, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> özelliğine özel <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfın bir örneğini atayın. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A>  
  
6. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> Veya <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> olarak ayarlandıysa, özelliği <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Numaralandırmadaki uygun bir değere ayarlayın. `ChainTrust` `PeerOrChainTrust` İptal modunun `PeerTrust` veya `Custom` doğrulama modlarında kullanılmadığını unutmayın.  
  
7. Gerekirse, <xref:System.IdentityModel.Tokens.SamlSerializer> <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> özelliğe özel bir sınıfın bir örneğini atayın. Özel bir güvenlik onaylama işlemi biçimlendirme dili (SAML) seri hale getirici, örneğin özel SAML onayları ayrıştırılırken gereklidir.  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>Yapılandırmada IssuedTokenServiceCredential özelliklerini ayarlamak için  
  
1. Bir < `<issuedTokenAuthentication>` `serviceCredentials`> öğesinin alt öğesi olarak bir öğe oluşturun.  
  
2. Bir CardSpace kartı gibi bir `<issuedTokenAuthentication>` otomatik olarak `true` verilen belirtecin kimliği doğrulanmışsa, öğesinin özniteliğiniolarakayarlayın.`allowUntrustedRsaIssuers`  
  
3. Öğesinin alt `<knownCertificates>` `<issuedTokenAuthentication>` öğesi olarak bir öğe oluşturun.  
  
4. `<add>` `findValue` `x509FindType` `storeName` `storeLocation`Öğesinin alt öğesi olarak sıfır veya daha fazla öğe oluşturun ve,,, ve özniteliklerini kullanarak sertifikayı bulmayı belirtin. `<knownCertificates>`  
  
5. Gerekirse, <`issuedTokenAuthentication`> öğesinin `samlSerializer` özniteliğini özel <xref:System.IdentityModel.Tokens.SamlSerializer> sınıfın tür adı olarak ayarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> içinde kodunun özelliklerini ayarlar.  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 Bir Federasyon hizmetinin bir istemcinin kimliğini doğrulayabilmesi için, verilen belirteç ile ilgili olarak aşağıdakilerin doğru olması gerekir:  
  
- Verilen belirtecin dijital imzası bir RSA güvenlik anahtarı tanımlayıcısı kullandığında, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> özelliği olmalıdır. `true`  
  
- Verilen belirtecin imzası bir x. 509.952 Issuer seri numarası, x. 509.952 konu anahtarı tanımlayıcısı veya x. 509.440 parmak izi güvenlik tanımlayıcısı kullandığında, verilen belirtecin, öğesinin <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliği tarafından döndürülen koleksiyonda bir sertifika tarafından imzalanması gerekir. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>sınıf.  
  
- Verilen belirteç bir X. 509.440 sertifikası kullanılarak imzalandığında, sertifikanın bağlı olan tarafa bir <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> <xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> veya alınmış olarak gönderilip gönderilmediğini bağımsız olarak, sertifikanın özelliğin değeriyle belirtilen semantiğe göre doğrulanması gerekir <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> özelliğinden. X. 509.440 sertifika doğrulaması hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Örneğin, öğesini <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> olarak <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> ayarlamak, `TrustedPeople` imza sertifikası sertifika deposunda olan verilen belirtecin kimliğini doğrular. Bu durumda, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> özelliğini ya <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine>da <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> olarak ayarlayın. Dahil olmak üzere <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>diğer modları seçebilirsiniz. Seçildiğinde, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> özelliğine <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfının bir örneğini atamanız gerekir. `Custom` Özel Doğrulayıcı, beğendiğini herhangi bir ölçüt kullanarak sertifikaları doğrulayabilir. Daha fazla bilgi için [nasıl yapılır: Özel bir sertifika Doğrulayıcı](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)kullanan bir hizmet oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Federasyon](../../../../docs/framework/wcf/feature-details/federation.md)
- [Federasyon ve Güven](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [Federasyon Örneği](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Nasıl yapılır: Bir WSFederationHttpBinding üzerindeki güvenli oturumları devre dışı bırakma](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: WSFederationHttpBinding oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [SecurityBindingElement Kimlik Doğrulama Modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
