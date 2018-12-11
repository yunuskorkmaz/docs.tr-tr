---
title: '&lt;customBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: eb8cd4172a83d618f3fd83519a8d9d2f4c864067
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128965"
---
# <a name="ltsecuritygt-of-ltcustombindinggt"></a>&lt;customBinding&gt; &lt;güvenliği&gt;
Özel bağlama için güvenlik seçeneklerini belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security   
   allowSerializedSigningTokenOnReply="Boolean"  
   authenticationMode="AuthenticationMode"  
      defaultAlgorithmSuite="SecurityAlgorithmSuite"  
   includeTimestamp="Boolean"  
      requireDerivedKeys="Boolean"  
   keyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"   
messageProtectionOrder="SignBeforeEncrypt/SignBeforeEncryptAndEncryptSignature/EncryptBeforeSign"  
      messageSecurityVersion="WSSecurityJan2004/WSSecurityXXX2005"  
   requireDerivedKeys="Boolean"  
   requireSecurityContextCancellation="Boolean"  
   requireSignatureConfirmation="Boolean"  
      securityHeaderLayout=  
              "Strict/Lax/LaxTimestampFirst/LaxTimestampLast">  
   <issuedTokenParameters />  
   <localClientSettings />  
   <localServiceSettings />  
   <secureConversationBootstrap />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|İsteğe bağlı. Seri hale getirilmiş bir belirteç üzerinde cevap kullanılıp kullanılmayacağını belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. Bir çift bağlamayı kullanarak ayarı için varsayılan olarak `true` ve yapılan herhangi bir ayarı yok sayılacak.|  
|authenticationMode|İsteğe bağlı. Başlarıcı ve Yanıtlayıcı arasında kullanılan kimlik doğrulama modunu belirtir. Aşağıda tüm değerler için bkz.<br /><br /> Varsayılan, `sspiNegotiated` değeridir.|  
|defaultAlgorithmSuite|İsteğe bağlı. İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.<br /><br /> Olası değerler, aşağıda gösterilmiştir. Varsayılan değer `Basic256` şeklindedir.<br /><br /> Bu öznitelik, bir dizi varsayılandan farklı algoritmalar için kabul eder, farklı bir platform ile çalışırken kullanılır. Bu ayarda yapılan değişiklikler yaparken, güçlü ve zayıf ilgili algoritmaları farkında olmalıdır. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|includeTimestamp|Her iletiye zaman damgalarının dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|keyEntropyMode|Güvenliğini sağlanmış iletiler için anahtarların hesaplanma yolunu belirtir. Anahtarları istemci anahtar malzemesi üzerinde yalnızca, yalnızca hizmet anahtar malzemesi veya her ikisinin bir birleşiminde temel alabilir. Geçerli değerler:<br /><br /> -   `ClientEntropy`: Oturum anahtarı istemci tarafından sağlanan anahtar verileri temel alır.<br />-   `ServerEntropy`: Oturum anahtarı sunucu tarafından sağlanan anahtar verileri temel alır.<br />-   `CombinedEntropy`: Oturum anahtarı istemci ve hizmet tarafından sağlanan anahtar verileri temel alır.<br /><br /> Varsayılan, `CombinedEntropy` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|messageProtectionOrder|Sıranın içinde hangi ileti düzeyi güvenlik algoritmasının uygulanacağı ayarlar. Geçerli değerler şunlardır:<br /><br /> -   `SignBeforeEncrypt`: Önce imzalamak ve şifrelemek.<br />-   `SignBeforeEncryptAndEncryptSignature`: İlk kez oturum, şifreleme ve imza şifreleme.<br />-   `EncryptBeforeSign`: İlk olarak, oturum şifreleyin.<br /><br /> Varsayılan değer kullanılan WS-güvenlik sürümüne bağlıdır. Varsayılan değer `SignBeforeEncryptAndEncryptSignature` WS-güvenlik 1.1 kullanırken. Varsayılan değer `SignBeforeEncrypt` WS-güvenlik 1.0 kullanırken.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|messageSecurityVersion|İsteğe bağlı. Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> -WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Varsayılan WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 olduğu ve XML olarak ifade edilebilir `Default`. Bu öznitelik türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Anahtarları kanıt anahtarlarından türetilip varsa belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|requireSecurityContextCancellation|İsteğe bağlı. Güvenlik bağlamı verilecek iptal edildi ve artık gerekli olmadığında sonlandırıldı, belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|requireSignatureConfirmation|İsteğe bağlı. WS-güvenlik imza doğrulamasının etkin olup olmadığını belirten bir Boole değeri. Ayarlandığında `true`, ileti imzaları Yanıtlayıcı tarafından onaylanır.  Ne zaman özel bağlama için karşılıklı sertifikalar yapılandırılmamış veya kullanım verilen belirteçleri (WSS 1.1 bağlamaları) Bu öznitelik varsayılan olarak yapılandırılmış `true`. Aksi takdirde, varsayılan değer `false`.<br /><br /> İmza onayı isteği tam tanıma hizmet yanıt verdiğini doğrulamak için kullanılır.|  
|securityHeaderLayout|İsteğe bağlı. Güvenlik üst bilgisindeki öğelerin sıralamasını belirtir. Geçerli değerler:<br /><br /> -   `Strict`: Öğeleri güvenlik başlığına göre "kullanılmadan önce bildirme" Genel İlkesi eklenir.<br />-   `Lax`: Öğeler için WSS onaylar herhangi bir sırada güvenlik üstbilgisinde eklenir: SOAP ileti güvenliği.<br />-   `LaxWithTimestampFirst`: Öğeler için WSS onaylar herhangi bir sırada güvenlik üstbilgisinde eklenir: İleti güvenliği güvenlik üst bilgisi içindeki ilk öğeyi wsse:Timestamp öğesi olmalıdır dışında SOAP.<br />-   `LaxWithTimestampLast`: Öğeler için WSS onaylar herhangi bir sırada güvenlik üstbilgisinde eklenir: İleti güvenliği güvenlik üst bilgisi içindeki son öğeden bir wsse:Timestamp öğesi olmalıdır dışında SOAP.<br /><br /> Varsayılan, `Strict` değeridir.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes192 şifrelemesi kullanın.|  
|Basic256|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes256 şifrelemesi kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|TripleDes|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.|  
|Basic128Rsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|TripleDesRsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|TripleDesSha256|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.|  
|Basic128Sha256Rsa15|İleti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Geçerli bir verilen belirtecin belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe kullanma hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) ve [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, özel bağlama kullanma güvenliğinin nasıl yapılandırılacağı gösterilmektedir. Bu, özel bağlama güvenli aktarım birlikte ileti düzeyi güvenliği etkinleştirmek için nasıl kullanılacağını gösterir. Bu hizmet ve istemci arasında ileti aktarmaya güvenli aktarım gereklidir ve iletileri ileti düzeyi üzerinde aynı anda güvenli olmalıdır yararlı olur. Bu yapılandırma, sistem tarafından sağlanan bağlamalar tarafından desteklenmiyor.  
  
 Hizmet yapılandırması, TLS/SSL protokolü ve ileti güvenliği Windows korunan TCP iletişimi destekleyen özel bir bağlama tanımlar. Özel bağlama taşıma düzeyinde hizmet kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında mesajlarını korumak için bir hizmet sertifikası kullanır. Bu tarafından gerçekleştirilir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) bağlama öğesi. Hizmet sertifikası, bir hizmet davranışını kullanarak yapılandırılır.  
  
 Ayrıca, özel bağlamanın Windows kimlik bilgisi türü ile ileti güvenliği kullanır - bu varsayılan kimlik bilgisi türüdür. Bu tarafından gerçekleştirilir [güvenlik](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi. Hizmet ve istemci, Kerberos kimlik doğrulama mekanizması varsa, ileti düzeyi güvenliği kullanılarak doğrulanır. Kerberos kimlik doğrulama mekanizması kullanılabilir durumda değilse, NTLM kimlik doğrulaması kullanılır. NTLM bir hizmete istemcinin kimliğini doğrular, ancak istemciye hizmet kimlik doğrulaması yapmaz. [Güvenlik](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi kullanacak şekilde yapılandırıldığını `SecureConversation` AuthenticationType değerine bir güvenlik oturumu hem istemci hem de hizmet oluşturulması ile sonuçlanır. Bu, hizmetin çalışması çift yönlü sözleşme etkinleştirmek için gereklidir. Bu örnek çalıştırma hakkında daha fazla bilgi için bkz. [özel bağlama güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- use following base address -->  
            <add baseAddress="net.tcp://localhost:8000/ServiceModelSamples/Service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                    binding="customBinding"  
                    bindingConfiguration="Binding1"   
                    contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
        <!-- the mex endpoint is exposed at net.tcp://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <sslStreamSecurity requireClientCertificate="false"/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.SecurityElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl Yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
