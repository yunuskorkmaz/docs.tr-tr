---
title: '&lt;customBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 148cd9e11c326ce499cf1ff1fa7c490bea3c05bb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752240"
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
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|İsteğe bağlı. Serileştirilmiş belirteci üzerinde cevap kullandıysanız belirten bir Boole değeri. Varsayılan değer `false` şeklindedir. Bir çift bağlama kullanırken, ayarı varsayılan olarak `true` ve yapılan herhangi bir ayar yoksayılır.|  
|authenticationMode|İsteğe bağlı. Başlatıcı hem Yanıtlayıcı arasında kullanılan kimlik doğrulama modunu belirtir. Aşağıda tüm değerler için bakın.<br /><br /> Varsayılan, `sspiNegotiated` değeridir.|  
|DefaultAlgorithmSuite|İsteğe bağlı. İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.<br /><br /> Olası değerler aşağıda verilmiştir. Varsayılan değer `Basic256` şeklindedir.<br /><br /> Bu öznitelik, bir dizi varsayılandan farklı algoritmalar için çevrilir farklı bir platform ile çalışırken kullanılır. Bu ayardaki değişiklikler yaparken gücü ve ilgili algoritmalarının zayıf farkında olmalıdır. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|IncludeTimestamp|Zaman damgaları yer alan her ileti dahil olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|KeyEntropyMode|İletileri güvenli hale getirme için anahtar hesaplanır yolunu belirtir. Anahtarları istemci anahtar malzemesi üzerinde yalnızca, hizmet anahtar malzemesi yalnızca veya her ikisinin birleşimini temel alabilir. Geçerli değerler:<br /><br /> -   `ClientEntropy`: Oturum anahtarı istemci tarafından sağlanan anahtar verileri temel alır.<br />-   `ServerEntropy`: Oturum anahtarı sunucu tarafından sağlanan anahtar verileri temel alır.<br />-   `CombinedEntropy`: Oturum anahtarı istemci ve hizmet tarafından sağlanan anahtar verileri temel alır.<br /><br /> Varsayılan, `CombinedEntropy` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.|  
|MessageProtectionOrder|Hangi iletisinde düzeyi güvenlik algoritmaları iletiye uygulanma sırası ayarlar. Geçerli değerler şunlardır:<br /><br /> -   `SignBeforeEncrypt`: İlk kez oturum sonra şifreleyin.<br />-   `SignBeforeEncryptAndEncryptSignature`: İlk kez oturum, şifreleme ve imza şifrelemek.<br />-   `EncryptBeforeSign`: İlk olarak, oturum şifreleyin.<br /><br /> Varsayılan değer kullanılan WS-Security sürüm bağlıdır. Varsayılan değer `SignBeforeEncryptAndEncryptSignature` WS-güvenlik 1.1 kullanırken. Varsayılan değer `SignBeforeEncrypt` WS güvenliği 1.0 kullanırken.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.Security.MessageProtectionOrder>.|  
|MessageSecurityVersion|İsteğe bağlı. Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> -WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />-WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />-WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Varsayılan WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 olduğu ve XML'de olarak ifade edilen `Default`. Bu öznitelik türünde <xref:System.ServiceModel.MessageSecurityVersion>.|  
|requireDerivedKeys|Özgün kanıtını anahtarları türetilebilir anahtarları belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|requireSecurityContextCancellation|İsteğe bağlı. Güvenlik bağlamı iptal edildi ve artık gerekmediğinde sonlandırıldı oluşturulmayacağını belirten bir Boole değeri. Varsayılan, `true` değeridir.|  
|RequireSignatureConfirmation|İsteğe bağlı. WS güvenliği imza onayı etkin olup olmadığını belirten bir Boole değeri. Ayarlandığında `true`, ileti imzalarını Yanıtlayıcı tarafından onaylanır.  Ne zaman özel bağlama karşılıklı sertifikalar için yapılandırılmışsa veya varsayılan olarak bu öznitelik kullanım verilen belirteçleri (WSS 1.1 bağlamaları) için yapılandırılmış `true`. Aksi takdirde, varsayılan değer `false`.<br /><br /> İmza onayı hizmet isteği tam tanıma yanıt verdiğini doğrulamak için kullanılır.|  
|SecurityHeaderLayout|İsteğe bağlı. Güvenlik üstbilgi öğeleri sıralama belirtir. Geçerli değerler:<br /><br /> -   `Strict`: Öğeler "kullanılmadan önce bildirmek" Genel İlkesi göre güvenlik üstbilgisi eklenir.<br />-   `Lax`: Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik.<br />-   `LaxWithTimestampFirst`: Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik dışında güvenlik üstbilgisi ilk öğe wsse:Timestamp öğesi olması gerekir.<br />-   `LaxWithTimestampLast`: Öğeleri için WSS onaylar herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP iletisi güvenlik dışında güvenlik üstbilgisi son öğesi wsse:Timestamp öğesi olması gerekir.<br /><br /> Varsayılan, `Strict` değeridir.<br /><br /> Bu öğe türünde <xref:System.ServiceModel.Channels.SecurityHeaderLayout>.|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>defaultAlgorithm özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256|Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|TripleDes|TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic128Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.|  
|TripleDesRsa15|TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.|  
|TripleDesSha256|TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<İssuermetadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|Geçerli bir verilen belirteç belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>.|  
|[\<localClientSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)|Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>.|  
|[\<localServiceSettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md)|Bu bağlama için yerel bir hizmet güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe kullanma hakkında daha fazla bilgi için bkz: [SecurityBindingElement kimlik doğrulama modları](../../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) ve [nasıl yapılır: SecurityBindingElement oluşturma bağlama kullanarak bir özel](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek özel bağlama kullanma güvenliğinin nasıl yapılandırılacağı gösterilmektedir. Özel bağlama güvenli bir taşıma birlikte ileti düzeyi güvenliği etkinleştirmek için nasıl kullanılacağını gösterir. Bu, güvenli bir taşıma hizmet ve istemci arasındaki iletileri iletmek için gerekli ve iletileri ileti düzeyi üzerinde aynı anda güvenli olmalıdır durumunda faydalı olur. Bu yapılandırma, sistem tarafından sağlanan bağlamalar tarafından desteklenmiyor.  
  
 TLS/SSL protokolü ve Windows ileti güvenliği kullanılarak korunan TCP iletişimi destekleyen özel bağlama hizmet yapılandırmasını tanımlar. Özel bağlama taşıma düzeyi hizmette kimlik doğrulaması ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır. Bu tarafından gerçekleştirilir [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) bağlama öğesi. Hizmetin sertifikası, bir hizmet davranışı kullanılarak yapılandırılır.  
  
 Ayrıca, Windows kimlik bilgisi türü ile ileti güvenliği özel bağlama kullanır - varsayılan kimlik bilgisi türü budur. Bu tarafından gerçekleştirilir [güvenlik](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi. Hem istemci hem de hizmet Kerberos kimlik doğrulama mekanizması varsa ileti düzeyi güvenlik kullanılarak doğrulanır. Kerberos kimlik doğrulama mekanizması kullanılabilir durumda değilse, NTLM kimlik doğrulaması kullanılır. NTLM istemci hizmeti için kimlik doğrulaması yapar ancak istemci hizmete kimlik doğrulamasını yapmaz. [Güvenlik](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi kullanacak şekilde yapılandırılmış `SecureConversation` güvenlik oturumu hem istemci hem de hizmet oluşturulması ile sonuçlanır authenticationType. Bu hizmetin çalışmak çift yönlü sözleşme etkinleştirmek için gereklidir. Bu örnek çalıştırma hakkında daha fazla bilgi için bkz: [özel bağlama güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md).  
  
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
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
