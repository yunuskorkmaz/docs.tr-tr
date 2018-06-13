---
title: 'Nasıl Yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: d4c2e34b3e123e6fa9d8dc8e544f621b39861592
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806188"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>Nasıl Yapılır: İmzalama ve Şifreleme için Ayrı X.509 Sertifikaları Kullanma
Bu konu, Windows Communication Foundation (WCF) ileti imzalama ve şifreleme hem istemci hem de hizmet için farklı sertifikalar kullanmak üzere yapılandırma gösterilmektedir.  
  
 WCF birden çok istemci veya hizmet sertifikaları ayarlamak için bir API sağlamadığından imzalama ve şifreleme için kullanılacak ayrı sertifikaların etkinleştirmek için özel bir istemci veya hizmet kimlik bilgilerini (veya her ikisi de) oluşturulması gerekir. Ayrıca, birden çok sertifika bilgileri kullanmasına ve bir uygun güvenlik belirteci sağlayıcısı oluşturmak için anahtar kullanım ve ileti yönünü belirtilen belirteci yöneticisi sağlanmalıdır güvenlik.  
  
 Aşağıdaki diyagramda kullanılan ana sınıflarını gösterir, sınıfları bunlar (bir yukarı ok tarafından gösterilen), devralınan ve dönüş türleri belirli yöntemleri ve özellikleri.  
  
-   `MyClientCredentials` özel bir uygulamasıdır <xref:System.ServiceModel.Description.ClientCredentials>.  
  
    -   Tüm dönüş örneklerini diyagramda gösterildiği özelliklerini <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>.  
  
    -   Kendi yöntemi <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> örneğini döndürür `MyClientCredentialsSecurityTokenManager`.  
  
-   `MyClientCredentialsSecurityTokenManager` özel bir uygulamasıdır <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>.  
  
    -   Kendi yöntemi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> örneğini döndürür <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider>.  
  
 ![İstemci kimlik bilgilerini nasıl kullanıldığını gösteren grafik](../../../../docs/framework/wcf/extending/media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")  
  
 Özel kimlik bilgileri hakkında daha fazla bilgi için bkz: [izlenecek yol: özel istemci oluşturma ve hizmet kimlik bilgilerini](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
 Ayrıca, bir özel kimlik doğrulayıcı oluşturma ve özel bağlama güvenliği bağlama öğesinde bağlantı gerekir. Ayrıca yerine varsayılan kimlik bilgilerini özel kimlik bilgileri kullanmanız gerekir.  
  
 Aşağıdaki diyagramda sınıfları söz konusu özel bağlama ve özel kimlik doğrulayıcı nasıl bağlı olduğu gösterilmektedir. Bunların tümü devral birkaç bağlama öğe söz konusu, <xref:System.ServiceModel.Channels.BindingElement>. <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> Sahip <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> örneğini döndürür özelliği <xref:System.ServiceModel.Security.IdentityVerifier>, içinden `MyIdentityVerifier` özelleştirilir.  
  
 ![Özel bağlama öğesi gösteren grafik](../../../../docs/framework/wcf/extending/media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")  
  
 Özel kimlik doğrulayıcı oluşturma hakkında daha fazla bilgi için bkz: nasıl yapılır: [nasıl yapılır: özel bir istemci Kimliği Doğrulayıcı oluşturma](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md).  
  
### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>İmzalama ve şifreleme için ayrı sertifikalarını kullanmak için  
  
1.  Öğesinden devralınan yeni bir istemci kimlik bilgileri sınıf tanımlama <xref:System.ServiceModel.Description.ClientCredentials> sınıfı. Birden çok sertifika belirtimine izin vermek için dört yeni özellikleri uygulamak: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, ve `ServiceEncryptingCertificate`. Ayrıca geçersiz <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> özelleştirilmiş bir örneğini döndürmek için yöntemin <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sonraki adımda tanımlanan sınıfı.  
  
     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]  
  
2.  Öğesinden devralınan yeni istemci güvenlik belirteci yöneticisi tanımlamak <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı. Geçersiz kılma <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> uygun güvenlik belirteci sağlayıcısı oluşturmak için yöntemi. `requirement` Parametre (bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) ileti yönü ve anahtar kullanım sağlar.  
  
     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]  
  
3.  Öğesinden devralınan yeni bir hizmet kimlik bilgilerini sınıf tanımlama <xref:System.ServiceModel.Description.ServiceCredentials> sınıfı. Birden çok sertifika belirtimine izin vermek için dört yeni özellikleri uygulamak: `ClientSigningCertificate`, `ClientEncryptingCertificate`, `ServiceSigningCertificate`, ve `ServiceEncryptingCertificate`. Ayrıca geçersiz <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> özelleştirilmiş bir örneğini döndürmek için yöntemin <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sonraki adımda tanımlanan sınıfı.  
  
     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]  
  
4.  Öğesinden devralınan yeni hizmet güvenlik belirteci yöneticisi tanımlamak <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı. Geçersiz kılma <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> geçilen ileti yönü ve anahtar kullanım verilen bir uygun güvenlik belirteci sağlayıcısı oluşturmak için yöntemi.  
  
     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]  
  
### <a name="to-use-multiple-certificates-on-the-client"></a>İstemci üzerinde birden çok sertifika kullanmak için  
  
1.  Özel bağlama oluşturma. Güvenlik bağlama öğesi, farklı bir güvenlik belirteci sağlayıcıları isteklerini ve yanıtlarını bulunması izin vermek için çift yönlü modda çalışmalıdır. Yapmanın bir yolu çift yönlü özellikli bir taşıma kullanın veya kullanmak için budur <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> aşağıdaki kodda gösterildiği gibi. Özelleştirilmiş bağlantı <xref:System.ServiceModel.Security.IdentityVerifier> güvenlik bağlama öğesi için bir sonraki adımda tanımlanan. Varsayılan istemci kimlik bilgileri, daha önce oluşturduğunuz özelleştirilmiş istemci kimlik bilgileri ile değiştirin.  
  
     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]  
  
2.  Özel tanımlama <xref:System.ServiceModel.Security.IdentityVerifier>. Farklı sertifikaları istek şifrelemek ve yanıt imzalamak için kullanıldığından hizmet birden çok kimliği vardır.  
  
    > [!NOTE]
    >  Aşağıdaki örnekte, sağlanan özel kimlik doğrulayıcı Tanıtım amaçlı denetimi uç nokta kimlikleri gerçekleştirmez. Bu yöntem üretim kodu için önerilmez.  
  
     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]  
  
### <a name="to-use-multiple-certificates-on-the-service"></a>Birden çok sertifika hizmetini kullanmak için  
  
1.  Özel bağlama oluşturma. Güvenlik bağlama öğesi, farklı bir güvenlik belirteci sağlayıcıları isteklerini ve yanıtlarını bulunması izin vermek için bir çift yönlü modda çalışmalıdır. İstemci ile çift yönlü özellikli bir taşıma veya kullanın gibi <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> aşağıdaki kodda gösterildiği gibi. Varsayılan hizmet kimlik bilgilerini daha önce oluşturduğunuz özelleştirilmiş hizmeti kimlik bilgileri ile değiştirin.  
  
     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>  
 <xref:System.ServiceModel.Security.IdentityVerifier>  
 [İzlenecek Yol: Özel İstemci ve Hizmet Kimlik Bilgileri Oluşturma](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
