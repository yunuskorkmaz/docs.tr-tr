---
title: SecurityBindingElement Kimlik Doğrulama Modları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: b09b50d2db277d6aec325fb9305890f8e5be581c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658906"
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement Kimlik Doğrulama Modları
Windows Communication Foundation (WCF) tarafından istemcileri ve Hizmetleri birbirine kimlik doğrulaması birkaç modu sağlar. Güvenlik bağlama öğeleri bu kimlik doğrulama modları için statik yöntemler kullanarak oluşturabileceğiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı veya yapılandırma yoluyla. Bu konuda, 18 kimlik doğrulama modları kısaca açıklanmaktadır.  
  
 Öğe kimlik doğrulama modlarından birini kullanarak bir örnek için bkz. [nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Temel yapılandırma programlama  
 Aşağıdaki yordam, kimlik doğrulama modunu bir yapılandırma dosyasında ayarlama işlemi açıklanmaktadır.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Kimlik doğrulama modu yapılandırmada ayarlamak için  
  
1.  İçin [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğe, Ekle bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Bir alt öğesi ekleyin bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesine `<customBinding>` öğesi.  
  
3.  Ekleme bir `<security>` öğesine `<binding>` öğesi.  
  
4.  Ayarlama `authenticationMode` aşağıda açıklanan değerlerden biri olarak özniteliği. Örneğin, aşağıdaki kod modu ayarlar `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Modu program üzerinden ayarlamak için  
  
1.  Aşağıdakilerden biri olabilir dönüş türü belirlenemiyor: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, veya <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Uygun statik yöntemini çağırabilirsiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. Örneğin, aşağıdaki çağrıları kod <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> yöntemi.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Bağlama öğesi, özel bağlamayı oluşturmak için kullanın. Daha fazla bilgi için [özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Modu açıklamaları  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Bu kimlik doğrulama modu ile istemci anonimdir ve bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliği <`security`> öğesine `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci anonimdir ve çalışma zamanında anlaşılan bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> yöntemi değeri olduğunda `false` için ilk parametre olarak geçirilir. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Bu kimlik doğrulama modu ile görüntülenen bir X.509 sertifikası SOAP katmanında bir onaylama destekleme belirteci kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Bu kimlik doğrulama modu ile hizmet için bu nedenle istemci kimliğini doğrulamaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bir paylaşılan anahtar bildiğini kanıtlamak için sunucuya sunan bir SAML belirteci alır. İstemcisini, bu nedenle, hizmet kimliği ancak güvenlik belirteci hizmeti yalnızca hizmet anahtarının şifresini verilen belirtecin bir parçası olarak paylaşılan anahtarı şifreler. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Bu kimlik doğrulama modu ile hizmet için bu nedenle istemci kimliğini doğrulamaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bir paylaşılan anahtar bildiğini kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci veya bir taşıyıcı belirteç olarak verilen belirteç görüntülenir; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Bu kimlik doğrulama modu ile hizmet için bu nedenle istemci kimliğini doğrulamaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bir paylaşılan anahtar bildiğini kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci veya bir taşıyıcı belirteç olarak verilen belirteç görüntülenir; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Bu kimlik doğrulama modu ile hizmet için bu nedenle istemci kimliğini doğrulamaz; Bunun yerine, istemci bir güvenlik belirteci hizmeti kimliğini doğrular ve ardından bir paylaşılan anahtar bildiğini kanıtlamak için sunucuya sunan bir SAML belirteci alır. SOAP katmanında bir onaylama destekleme belirteci veya bir taşıyıcı belirteç olarak verilen belirteç görüntülenir; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Bu kimlik doğrulama modu, bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular. Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `Kerberos`.  
  
> [!NOTE]
>  Bu kimlik doğrulama modu kullanmak için hizmet hesabı bir hizmet asıl adı (SPN) ile ilişkilendirilmiş olması gerekir. Bunu yapmak için hizmetin ağ hizmeti hesabı veya yerel sistem hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak üzere SetSpn.exe Aracı'nı kullanın. Her iki durumda da, istemci uygulamasında doğru SPN kullanmalısınız [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesini kullanarak veya <xref:System.ServiceModel.EndpointAddress> Oluşturucusu. Daha fazla bilgi için [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Zaman `Kerberos` kimlik doğrulama modu kullanılan <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> ve <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> kimliğe bürünme düzeyi desteklenmiyor.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Bu kimlik doğrulama modu, bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular. Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `KerberosOverTransport`.  
  
> [!NOTE]
>  Bu kimlik doğrulama modu kullanmak için hizmet hesabı SPN ile ilişkilendirilmiş olması gerekir. Bunu yapmak için hizmetin ağ hizmeti hesabı veya yerel sistem hesabı altında çalıştırın. Alternatif olarak, hizmet hesabı için bir SPN oluşturmak üzere SetSpn.exe Aracı'nı kullanın. Her iki durumda da, istemci uygulamasında doğru SPN kullanmalısınız [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesini kullanarak veya <xref:System.ServiceModel.EndpointAddress> Oluşturucusu. Daha fazla bilgi için [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Bu kimlik doğrulama modu ile görüntülenen bir X.509 sertifikası SOAP katmanında bir onaylama destekleme belirteci kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Bu kimlik doğrulama modu ile görüntülenen bir X.509 sertifikası SOAP katmanında bir onaylama destekleme belirteci kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Bağlamanın bir `AsymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 Bu kimlik doğrulama modu ile hizmet ve istemci X.509 sertifikaları kullanarak kimlik doğrulaması. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> yöntemi değeri olduğunda `true` için ilk parametre olarak geçirilir. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> yöntemi. Bu yöntem bir <xref:System.ServiceModel.Channels.SecurityBindingElement> parametre olarak, güvenli oturum oluşturmak için başlatma sırasında kullanılır. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SecureConversation`.  
  
 Önyükleme hiçbir bağlama belirtilirse, ardından `SspiNegotiated` kimlik doğrulama modu, önyükleme için kullanılır.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır. Kerberos mümkün olduğunda kullanılır. Aksi takdirde, NT LanMan (NTLM) kullanılır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır. Mümkünse, Kerberos protokolü kullanılır; Aksi takdirde, NTLM kullanılır. Elde edilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür; diğer bir deyişle, ileti imzası oturum açtığında bir belirteç. Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Bu kimlik doğrulama modu ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak hizmete istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameForCertificate`.  
  
 İçin `UserNameForCertificate` kimlik doğrulama modu, hem istemci hem de hizmet WS-güvenlik 1.1 kullanmanız gerekir.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Bu kimlik doğrulama modu ile istemcidir görüntülenen bir kullanıcı adı belirteci imzalı destekleyici belirteç olarak; SOAP katmanında kullanarak kimliğini doğrular diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `SymmetricSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Bu kimlik doğrulama modu ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak istemcinin kimliğini doğrular; diğer bir deyişle, ileti imzası tarafından imzalı bir belirteç. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Güvenlik bağlama öğesi bir `TransportSecurityBindingElement` tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> yöntemi. Alternatif olarak, kümesinin `authenticationMode` özniteliğini `UserNameOverTransport`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Nasıl yapılır: Belirtilen kimlik doğrulama modu için SecurityBindingElement oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
