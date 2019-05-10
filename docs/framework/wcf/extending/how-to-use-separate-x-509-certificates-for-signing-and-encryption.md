---
title: 'Nasıl yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: fc5b40bec7c53c9884379658ddce6d036032f160
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617593"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Nasıl yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma
Bu konuda, Windows Communication Foundation (WCF) ileti imzalama ve şifreleme hem istemci hem de hizmet için farklı sertifikalar kullanmak üzere yapılandırma gösterilmektedir.  
  
 WCF istemci veya hizmet birden çok sertifika ayarlamak için bir API sağlanmadığı için imzalama ve şifreleme için kullanılacak ayrı sertifikalar etkinleştirmek için özel bir istemci veya hizmet kimlik bilgilerini (veya her ikisi de) oluşturulması gerekir. Ayrıca, birden çok sertifika bilgileri kullanmasına ve bir uygun güvenlik belirteci sağlayıcısı oluşturmak için anahtar kullanımı ve ileti yönü belirtilen belirteci yöneticisi sağlanmalıdır güvenlik.  
  
 Aşağıdaki diyagram, kullanılan ana sınıflarını göstermektedir, sınıfları (yukarıyı gösteren bir ok ile gösterilen) devralındığı ve dönüş türleri belirli yöntemleri ve özellikleri.  
  
- `MyClientCredentials` özel bir uygulamasıdır <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    - Aşağıdaki diyagramda gösterilen tüm dönüş örneklerini özelliklerini <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    - Kendi yöntemi <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> örneğini döndürür `MyClientCredentialsSecurityTokenManager`.  
  
- `MyClientCredentialsSecurityTokenManager` özel bir uygulamasıdır <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    - Kendi yöntemi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> örneğini döndürür <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![İstemci kimlik bilgileri nasıl kullanıldığını gösteren grafik](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 Özel kimlik bilgileri hakkında daha fazla bilgi için bkz: [izlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Ayrıca, bir özel kimlik doğrulayıcı oluşturma ve bir güvenlik bağlama öğesinin özel bir bağlama için bağlamanız gerekir. Varsayılan kimlik bilgileri yerine özel kimlik bilgilerini de kullanmanız gerekir.  
  
 Aşağıdaki diyagramda sınıfları ilgili özel bağlama ve özel bir kimlik doğrulayıcı nasıl bağlı olduğu gösterilmektedir. Her biri devral çeşitli bağlama öğesi karmaşık <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Sahip <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> örneğini döndüren özellik <xref:System.ServiceModel.Security.IdentityVerifier>, içinden `MyIdentityVerifier` özelleştirilir.  
  
 ![Özel bağlama öğesini gösteren grafik](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 Özel bir kimlik doğrulayıcı oluşturma hakkında daha fazla bilgi için bkz: nasıl yapılır: [Nasıl yapılır: Özel İstemci Kimliği Doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>İmzalama ve şifreleme için ayrı sertifikalar kullanmak için  
  
1. Devralan yeni bir istemci kimlik bilgileri sınıfı tanımlayın <xref:System.ServiceModel.Description.ClientCredentials> sınıfı. Birden çok sertifika belirtimine izin vermek için dört yeni özellikler uygular: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, ve `ServiceEncryptingCertificate`. Ayrıca geçersiz <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> özelleştirilmiş bir örneğini döndürülecek yöntemi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sonraki adımda tanımlanan sınıfı.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2. Devralan yeni bir istemci güvenlik belirteci yöneticisi tanımlamak <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı. Geçersiz kılma <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> uygun güvenlik belirteci sağlayıcı oluşturma için yöntemi. `requirement` Parametre (bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) ileti yönü ve anahtar kullanım sağlar.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3. Devralan yeni bir hizmet kimlik bilgilerini sınıfı tanımlayın <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı. Birden çok sertifika belirtimine izin vermek için dört yeni özellikler uygular: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, ve `ServiceEncryptingCertificate`. Ayrıca geçersiz <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> özelleştirilmiş bir örneğini döndürülecek yöntemi <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sonraki adımda tanımlanan sınıfı.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4. Devralan yeni bir hizmet güvenlik belirteci yöneticisi tanımlamak <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı. Geçersiz kılma <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> gönderilen ileti yönü ve anahtar kullanım verilen uygun güvenlik belirteci sağlayıcı oluşturma için yöntemi.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>İstemci üzerinde birden çok sertifika kullanmak için  
  
1. Özel bir bağlama oluşturun. Güvenlik bağlama öğesinin farklı güvenlik belirteci sağlayıcıları istekleri ve yanıtları için mevcut olması izin vermek için çift yönlü modda çalışmalıdır. Yapmanın bir yolu çift yönlü özellikli bir aktarım kullanın veya kullanmak için budur <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> aşağıdaki kodda gösterildiği gibi. Özelleştirilmiş bağlantı <xref:System.ServiceModel.Security.IdentityVerifier> sonraki adımda güvenlik bağlama öğesi için tanımlanmış. Varsayılan istemci kimlik bilgileri, daha önce oluşturduğunuz özelleştirilmiş istemci kimlik bilgileri ile değiştirin.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2. Özel tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>. Hizmet birden çok kimlik sahip farklı bir sertifika isteği şifrelemek ve yanıt imzalamak için kullanılır.  
  
    > [!NOTE]
    >  Aşağıdaki örnekte, tanıtım amacıyla denetimi herhangi bir uç noktası kimliği sağlanan özel bir kimlik doğrulayıcı gerçekleştirmez. Bu yöntem üretim kodu için önerilmez.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Hizmeti için kullanabileceğiniz birden fazla sertifika  
  
1. Özel bir bağlama oluşturun. Güvenlik bağlama öğesinin farklı güvenlik belirteci sağlayıcıları istekleri ve yanıtları için mevcut olması izin vermek için bir çift yönlü modda çalışmalıdır. İstemci ile çift yönlü özellikli bir aktarım kullanın veya kullanmak <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> aşağıdaki kodda gösterildiği gibi. Varsayılan hizmet kimlik bilgilerini, daha önce oluşturduğunuz özelleştirilmiş hizmet kimlik bilgileri ile değiştirin.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [İzlenecek yol: Özel istemci ve hizmet kimlik bilgilerini oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
