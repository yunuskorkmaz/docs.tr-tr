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
ms.openlocfilehash: e464aff46f311ede1cd629fb459ade9a6e627d59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796951"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Nasıl yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma

Bu konuda, hem istemci hem de hizmette ileti imzalama ve şifreleme için farklı sertifikaları kullanmak üzere Windows Communication Foundation (WCF) yapılandırma gösterilmektedir.

İmzalama ve şifreleme için ayrı sertifikaların kullanılmasını etkinleştirmek üzere, WCF birden çok istemci veya hizmet sertifikası ayarlamak için bir API sağlamadığı için özel bir istemci veya hizmet kimlik bilgileri (veya her ikisi de) oluşturulmalıdır. Ayrıca, birden çok sertifika bilgisinin kullanılması ve belirtilen anahtar kullanımı ve ileti yönü için uygun bir güvenlik belirteci sağlayıcısı oluşturmak için bir güvenlik belirteci Yöneticisi sağlanmalıdır.

Aşağıdaki diyagramda, kullanılan ana sınıflar, devraldığı sınıflar (yukarıyı gösteren bir oka göre gösterilir) ve belirli yöntemlerin ve özelliklerin dönüş türleri gösterilmektedir.

- `MyClientCredentials`, özel bir uygulamasıdır <xref:System.ServiceModel.Description.ClientCredentials>.

  - Diyagramda gösterilen özelliklerine ait <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>Özellikler döndürülen örnekleri.

  - Yöntemi <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> bir`MyClientCredentialsSecurityTokenManager`örneğini döndürür.

- `MyClientCredentialsSecurityTokenManager`, özel bir uygulamasıdır <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.

  - Yöntemi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> bir<xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>örneğini döndürür.

![İstemci kimlik bilgilerinin nasıl kullanıldığını gösteren grafik](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-A59F-4571-b36f-7e6b2f0d610f")

Özel kimlik bilgileri hakkında daha fazla bilgi için [bkz. İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri](walkthrough-creating-custom-client-and-service-credentials.md)oluşturuluyor.

Ayrıca, özel bir kimlik doğrulayıcı oluşturmanız ve bunu özel bir bağlamada Güvenlik bağlama öğesine bağlamanız gerekir. Varsayılan kimlik bilgileri yerine özel kimlik bilgilerini de kullanmalısınız.

Aşağıdaki diyagramda özel bağlamada yer alan sınıflar ve özel kimlik doğrulayıcı 'nın nasıl bağlandığı gösterilmektedir. ' Den <xref:System.ServiceModel.Channels.BindingElement>kalıtımla alan birkaç bağlama öğesi vardır. , ' Nin <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> özelleştirildiği ' `MyIdentityVerifier` öğesinin <xref:System.ServiceModel.Security.IdentityVerifier>bir örneğini döndüren özelliğine sahiptir.<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>

![Özel bağlama öğesini gösteren grafik](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")

Özel kimlik doğrulayıcı oluşturma hakkında daha fazla bilgi için bkz. nasıl yapılır: [Nasıl yapılır: Özel bir Istemci Kimliği Doğrulayıcısı](how-to-create-a-custom-client-identity-verifier.md)oluşturun.

### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>İmzalama ve şifreleme için ayrı sertifikalar kullanmak üzere

1. <xref:System.ServiceModel.Description.ClientCredentials> Sınıfından devralan yeni bir istemci kimlik bilgileri sınıfı tanımlayın. Birden çok sertifika belirtimine izin vermek için dört yeni özellik `ClientSigningCertificate`uygulayın `ClientEncryptingCertificate`: `ServiceSigningCertificate`,, `ServiceEncryptingCertificate`ve. Ayrıca, bir <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> sonraki adımda tanımlanan özelleştirilmiş <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfın bir örneğini döndürmek için yöntemini geçersiz kılın.

     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]

2. <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> Sınıfından devralan yeni bir istemci güvenlik belirteci Yöneticisi tanımlayın. Uygun bir güvenlik belirteci sağlayıcısı oluşturmak için yönteminigeçersizkılın.<xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> Parametresi (a <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) ileti yönünü ve anahtar kullanımını sağlar. `requirement`

     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]

3. <xref:System.ServiceModel.Description.ServiceCredentials> Sınıfından devralan yeni bir hizmet kimlik bilgileri sınıfı tanımlayın. Birden çok sertifika belirtimine izin vermek için dört yeni özellik `ClientSigningCertificate`uygulayın `ClientEncryptingCertificate`: `ServiceSigningCertificate`,, `ServiceEncryptingCertificate`ve. Ayrıca, bir <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> sonraki adımda tanımlanan özelleştirilmiş <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfın bir örneğini döndürmek için yöntemini geçersiz kılın.

     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]

4. <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> Sınıfından devralan yeni bir hizmet güvenlik belirteci Yöneticisi tanımlayın. Geçilen ileti yönü ve anahtar kullanımı verilen uygun bir güvenlik belirteci sağlayıcısı oluşturmak için yönteminigeçersizkılın.<xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A>

     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]

### <a name="to-use-multiple-certificates-on-the-client"></a>İstemcide birden çok sertifika kullanmak için

1. Özel bir bağlama oluşturun. Güvenlik bağlama öğesinin, istekler ve yanıtlar için farklı güvenlik belirteci sağlayıcılarının bulunmasına izin vermek üzere çift yönlü modda çalışması gerekir. Bunu yapmanın bir yolu, <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> çift yönlü bir aktarım kullanmaktır veya aşağıdaki kodda gösterildiği gibi öğesini kullanmaktır. Bir sonraki adımda <xref:System.ServiceModel.Security.IdentityVerifier> tanımlanan özelleştirilmiş ' i güvenlik bağlama öğesine bağlayın. Varsayılan istemci kimlik bilgilerini önceden oluşturulan özelleştirilmiş istemci kimlik bilgileriyle değiştirin.

     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]

2. Özel <xref:System.ServiceModel.Security.IdentityVerifier>bir tanımlama. Hizmetin birden çok kimliği vardır çünkü isteği şifrelemek ve yanıtı imzalamak için farklı sertifikalar kullanılır.

    > [!NOTE]
    > Aşağıdaki örnekte, belirtilen özel kimlik doğrulayıcı, tanıtım amacıyla herhangi bir uç nokta kimlik denetimi gerçekleştirmez. Bu, üretim kodu için önerilen bir uygulamadır.

     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]

### <a name="to-use-multiple-certificates-on-the-service"></a>Hizmette birden çok sertifika kullanmak için

1. Özel bir bağlama oluşturun. Güvenlik bağlama öğesinin, istekler ve yanıtlar için farklı güvenlik belirteci sağlayıcılarının mevcut olmasını sağlamak üzere çift yönlü modda çalışması gerekir. İstemcide olduğu gibi, çift yönlü bir aktarım kullanın veya aşağıdaki kodda gösterildiği <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> gibi kullanın. Varsayılan hizmet kimlik bilgilerini önceden oluşturulmuş özelleştirilmiş hizmet kimlik bilgileriyle değiştirin.

     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [İzlenecek yol: Özel Istemci ve hizmet kimlik bilgileri oluşturma](walkthrough-creating-custom-client-and-service-credentials.md)
