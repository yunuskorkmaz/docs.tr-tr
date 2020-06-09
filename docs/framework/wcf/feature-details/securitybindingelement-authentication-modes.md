---
title: SecurityBindingElement Kimlik Doğrulama Modları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: 163645c16097b5371369618f2bd5f333feb75747
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595160"
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement Kimlik Doğrulama Modları
Windows Communication Foundation (WCF), istemcilerin ve hizmetlerin bir diğeri üzerinde kimlik doğrulaması yaptığı çeşitli modlar sağlar. Sınıfında veya yapılandırma aracılığıyla statik yöntemler kullanarak bu kimlik doğrulama modları için güvenlik bağlama öğeleri oluşturabilirsiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> . Bu konu, 18 kimlik doğrulama modlarını kısaca açıklamaktadır.  
  
 Öğesinin kimlik doğrulama modlarından biri için kullanımına ilişkin bir örnek için, bkz. [nasıl yapılır: belirtilen bir kimlik doğrulama modu Için SecurityBindingElement oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Temel yapılandırma programlama  
 Aşağıdaki yordamda, bir yapılandırma dosyasında kimlik doğrulama modunun nasıl ayarlanacağı açıklanmaktadır.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Yapılandırmada kimlik doğrulama modunu ayarlamak için  
  
1. [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md)Öğesine bir ekleyin [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .  
  
2. Bir alt öğe olarak, öğesine bir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin `<customBinding>` .  
  
3. Öğeye bir `<security>` öğe ekleyin `<binding>` .  
  
4. `authenticationMode`Özniteliğini aşağıda açıklanan değerlerden birine ayarlayın. Örneğin, aşağıdaki kod modu olarak ayarlar `AnonymousForCertificate` .  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Modu program aracılığıyla ayarlamak için  
  
1. Dönüş türünü belirleme, aşağıdakilerden biri olabilir: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> , <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.SecurityBindingElement> .  
  
2. Sınıfının uygun statik yöntemini çağırın <xref:System.ServiceModel.Channels.SecurityBindingElement> . Örneğin, aşağıdaki kod <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> yöntemini çağırır.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. Özel bağlama oluşturmak için bağlama öğesini kullanın. Daha fazla bilgi için bkz. [Özel Bağlamalar](../extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Mod açıklamaları  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Bu kimlik doğrulama moduyla, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> . Alternatif olarak, `authenticationMode` <`security`> öğesinin özniteliğini olarak ayarlayın `AnonymousForCertificate` .  
  
### <a name="anonymousforsslnegotiated"></a>Anonymousforsslanlaşmalı  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmetin kimliği, çalışma zamanında anlaşılan bir X. 509.440 sertifikası kullanılarak doğrulanır. <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> İlk parametre için bir değer geçirildiğinde, yöntemi tarafından döndürülen güvenlik bağlama öğesi `false` . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `AnonymousForSslNegotiated` .  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında bir onaylama destekleme belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `CertificateOverTransport` .  
  
### <a name="issuedtoken"></a>IssuedToken  
 Bu kimlik doğrulama moduyla, istemci hizmette kimlik doğrulaması yapmaz; Örneğin, Bunun yerine, istemci bir güvenlik belirteci hizmetinin kimliğini doğrular ve bir SAML belirteci alır. Bu, daha sonra paylaşılan bir anahtarın bilgisini kanıtlamak için sunucuya sunulur. Hizmetin kimliği istemci tarafından doğrulanmadığı için, ancak güvenlik belirteci hizmeti verilen belirtecin bir parçası olarak paylaşılan anahtarı şifreler; böylece yalnızca hizmet, anahtarın şifresini çözebilir. Güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `IssuedToken` .  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Bu kimlik doğrulama moduyla, istemci hizmette kimlik doğrulaması yapmaz; Örneğin, Bunun yerine, istemci bir güvenlik belirteci hizmetinin kimliğini doğrular ve bir SAML belirteci alır. Bu, daha sonra paylaşılan bir anahtarın bilgisini kanıtlamak için sunucuya sunulur. Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak görünür; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `IssuedTokenForCertificate` .  
  
### <a name="issuedtokenforsslnegotiated"></a>Issuedtokenforsslanlaşmalı  
 Bu kimlik doğrulama moduyla, istemci hizmette kimlik doğrulaması yapmaz; Örneğin, Bunun yerine, istemci bir güvenlik belirteci hizmetinin kimliğini doğrular ve bir SAML belirteci alır. Bu, daha sonra paylaşılan bir anahtarın bilgisini kanıtlamak için sunucuya sunulur. Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak görünür; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `IssuedTokenForSslnegotiated` .  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Bu kimlik doğrulama moduyla, istemci hizmette kimlik doğrulaması yapmaz; Örneğin, Bunun yerine, istemci bir güvenlik belirteci hizmetinin kimliğini doğrular ve bir SAML belirteci alır. Bu, daha sonra paylaşılan bir anahtarın bilgisini kanıtlamak için sunucuya sunulur. Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak görünür; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, `TransportSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `IssuedTokenOverTransport` .  
  
### <a name="kerberos"></a>Kerberos  
 Bu kimlik doğrulama moduyla istemci, Kerberos bileti kullanarak hizmetin kimliğini doğrular. Aynı bilet aynı zamanda sunucu kimlik doğrulaması da sağlar. Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `Kerberos` .  
  
> [!NOTE]
> Bu kimlik doğrulama modunu kullanabilmeniz için hizmet hesabının bir hizmet asıl adı (SPN) ile ilişkilendirilmesi gerekir. Bunu yapmak için, hizmeti ağ HIZMETI hesabı veya yerel SISTEM hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak üzere SetSpn. exe aracını kullanın. Her iki durumda da, istemcinin öğesinde doğru SPN kullanması [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) veya oluşturucuyu kullanması gerekir <xref:System.ServiceModel.EndpointAddress> . Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).  
  
> [!NOTE]
> `Kerberos`Kimlik doğrulama modu kullanıldığında, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> kimliğe bürünme düzeyleri desteklenmez.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Bu kimlik doğrulama moduyla istemci, Kerberos bileti kullanarak hizmetin kimliğini doğrular. Kerberos belirteci, SOAP katmanında bir onaylama destekleme belirteci olarak görünür; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, `TransportSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `KerberosOverTransport` .  
  
> [!NOTE]
> Bu kimlik doğrulama modunu kullanabilmeniz için hizmet hesabının bir SPN ile ilişkilendirilmesi gerekir. Bunu yapmak için, hizmeti ağ HIZMETI hesabı veya yerel SISTEM hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak üzere SetSpn. exe aracını kullanın. Her iki durumda da, istemcinin öğesinde doğru SPN kullanması [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md) veya oluşturucuyu kullanması gerekir <xref:System.ServiceModel.EndpointAddress> . Daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>Çoklu sertifika  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında bir onaylama destekleme belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `MutualCertificate` .  
  
### <a name="mutualcertificateduplex"></a>Değişken Uıalcertificateduplex  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında bir onaylama destekleme belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır. Bağlama `AsymmetricSecurityBindingElement` yöntemi tarafından döndürülür <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `MutualCertificateDuplex` .  
  
### <a name="mutualsslnegotiated"></a>Değişken anlaşmalı  
 Bu kimlik doğrulama moduyla, istemci ve hizmet X. 509.440 sertifikalarını kullanarak kimlik doğrular. `SymmetricSecurityBindingElement` <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> İlk parametre için bir değer geçirildiğinde, yöntemi tarafından döndürülen güvenlik bağlama öğesi `true` . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `MutualSslNegotiated` .  
  
### <a name="secureconversation"></a>SecureConversation  
 Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> . Bu yöntem <xref:System.ServiceModel.Channels.SecurityBindingElement> , başlatma sırasında güvenli oturum oluşturmak için kullanılan parametresi olarak bir parametresini alır. Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `SecureConversation` .  
  
 Önyükleme bağlaması belirtilmemişse, `SspiNegotiated` önyükleme için kimlik doğrulama modu kullanılır.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Bu kimlik doğrulama moduyla, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır. Mümkünse Kerberos kullanılır; Aksi halde, NT LanMan (NTLM) kullanılır. Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `SspiNegotiated` .  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Bu kimlik doğrulama moduyla, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır. Mümkünse Kerberos protokolü kullanılır; Aksi halde, NTLM kullanılır. Elde edilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür; diğer bir deyişle, ileti imzasını imzalayan bir belirteç. Ayrıca hizmet, aktarım katmanında bir X. 509.440 sertifikası tarafından da doğrulanır. Güvenlik bağlama öğesi, `TransportSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `SspiNegotiatedOverTransport` .  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Bu kimlik doğrulama moduyla istemci, SOAP katmanında imzalanmış destekleyici belirteç olarak görünen bir Kullanıcı adı belirtecini kullanarak hizmeti doğrular; diğer bir deyişle, ileti imzası tarafından imzalanan bir belirteç. Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `UserNameForCertificate` .  
  
 `UserNameForCertificate`Kimlik doğrulama modu için hem istemci hem de HIZMET WS-Security 1,1 kullanıyor olmalıdır.  
  
### <a name="usernameforsslnegotiated"></a>Usernameforsslanlaşmalı  
 Bu kimlik doğrulama moduyla istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimlik doğrular; diğer bir deyişle, ileti imzası tarafından imzalanan bir belirteç. Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, `SymmetricSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `UserNameForSslNegotiated` .  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Bu kimlik doğrulama moduyla istemci, SOAP katmanında imzalanmış destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimliğini doğrular; diğer bir deyişle, ileti imzası tarafından imzalanan bir belirteç. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Güvenlik bağlama öğesi, `TransportSecurityBindingElement` yöntemi tarafından döndürülen bir öğedir <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> . Alternatif olarak, `authenticationMode` özniteliğini olarak ayarlayın `UserNameOverTransport` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
