---
title: SecurityBindingElement Kimlik Doğrulama Modları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 715c813015fdb4b52444efca0bdcfc99acc92c21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement Kimlik Doğrulama Modları
Windows Communication Foundation (WCF) birkaç modu olarak istemciler ve hizmetler birbirine kimlik doğrulaması sağlar. Güvenlik bağlama öğeleri bu kimlik doğrulama modları için statik yöntemler kullanarak oluşturabileceğiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı veya yapılandırma yoluyla. Bu konuda 18 kimlik doğrulama modları kısaca açıklanmaktadır.  
  
 Tek bir kimlik doğrulama modu öğesini kullanarak bir örnek için bkz: [nasıl yapılır: belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Temel yapılandırma programlama  
 Aşağıdaki yordam, kimlik doğrulama modunu bir yapılandırma dosyasında ayarlanan açıklar.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Kimlik doğrulama modunu yapılandırmak için  
  
1.  İçin [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi ekleme bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Bir alt öğesi Ekle bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesine `<customBinding>` öğesi.  
  
3.  Ekleme bir `<security>` öğesine `<binding>` öğesi.  
  
4.  Ayarlama `authenticationMode` özniteliği için aşağıda açıklanan değerlerden biri. Örneğin, aşağıdaki kodu modunu ayarlar `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Mod programlı olarak ayarlamak için  
  
1.  Şunlardan biri olabilir dönüş türü belirlenemiyor: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, veya <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Uygun statik yöntemini çağırın <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Örneğin, aşağıdaki çağrıları kod <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> yöntemi.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Özel bağlama oluşturma için bağlama öğesini kullanın. Daha fazla bilgi için bkz: [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Mod açıklamaları  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliği <`security`> öğesine `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmet çalışma zamanında anlaşılan bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> yöntemi değerini zaman `false` için ilk parametre geçirildi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Bu kimlik doğrulama modu ile bir onaylama destekleme belirteci SOAP katmanında görünür bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle kimlik doğrulama kullanmaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bildiğini paylaşılan anahtar kanıtlamak için sunucuya sunan bir SAML belirteci alır. Hizmet istemcisi için bu nedenle, kimlik doğrulaması yapılamıyor, ancak yalnızca hizmet anahtarı şifresini çözebilir böylece güvenlik belirteci hizmeti paylaşılan anahtar verilen belirteç bir parçası olarak şifreler. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle kimlik doğrulama kullanmaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bildiğini paylaşılan anahtar kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak verilen belirteç görünür; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle kimlik doğrulama kullanmaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bildiğini paylaşılan anahtar kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak verilen belirteç görünür; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle kimlik doğrulama kullanmaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bildiğini paylaşılan anahtar kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci ya da bir taşıyıcı belirteci olarak verilen belirteç görünür; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `Kerberos`.  
  
> [!NOTE]
>  Bu kimlik doğrulama modu kullanmak için hizmet hesabı bir hizmet asıl adı (SPN) ile ilişkilendirilmiş olması gerekir. Bunu yapmak için hizmetin ağ hizmeti hesabı veya yerel sistem hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak istiyorsanız SetSpn.exe aracını kullanın. Her iki durumda da, istemci doğru SPN kullanmalısınız [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesini kullanarak veya <xref:System.ServiceModel.EndpointAddress> Oluşturucusu. Daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Zaman `Kerberos` kimlik doğrulama modu kullanılır, <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> kimliğe bürünme düzeyi desteklenmiyor.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görüntülenir; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `KerberosOverTransport`.  
  
> [!NOTE]
>  Bu kimlik doğrulama modu kullanmak için hizmet hesabı SPN ile ilişkilendirilmiş olması gerekir. Bunu yapmak için hizmetin ağ hizmeti hesabı veya yerel sistem hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak istiyorsanız SetSpn.exe aracını kullanın. Her iki durumda da, istemci doğru SPN kullanmalısınız [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesini kullanarak veya <xref:System.ServiceModel.EndpointAddress> Oluşturucusu. Daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Bu kimlik doğrulama modu ile bir onaylama destekleme belirteci SOAP katmanında görünür bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Bu kimlik doğrulama modu ile bir onaylama destekleme belirteci SOAP katmanında görünür bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Bağlamanın bir `AsymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualCertificateDuplex`.  
  
### <a name="mutalsslnegotiation"></a>MutalSslNegotiation  
 Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> yöntemi değerini zaman `true` için ilk parametre geçirildi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> yöntemi. Bu yöntem alır bir <xref:System.ServiceModel.Channels.SecurityBindingElement> bir parametre olarak başlatma sırasında güvenli oturum oluşturmak için kullanılan. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SecureConversation`.  
  
 Önyükleme hiçbir bağlama belirtilirse, sonra `SspiNegotiated` kimlik doğrulama modu, önyükleme için kullanılır.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos mümkünse kullanılır; Aksi halde, NT LanMan (NTLM) kullanılır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos protokolü mümkünse kullanılır; Aksi halde, NTLM kullanılır. Elde edilen belirteç SOAP katmanında bir onaylama destekleme belirteci görüntülenir; diğer bir deyişle, ileti imzası imzalar bir belirteç. Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Bu kimlik doğrulama modu ile istemci hizmeti görünür bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanarak kimliğini doğrular; diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameForCertificate`.  
  
 İçin `UserNameForCertificate` WS-güvenlik 1.1 kimlik doğrulama modu, hem istemci hem de hizmet kullanma.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Bu kimlik doğrulama modu ile istemcidir görünen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak; kullanarak kimliğini doğrular diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Bu kimlik doğrulama modu ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameOverTransport`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 [Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
