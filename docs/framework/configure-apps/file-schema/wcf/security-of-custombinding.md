---
title: <security> / <customBinding>
ms.date: 03/30/2017
ms.assetid: 243a5148-bbd1-447f-a8a5-6e7792c0a3f1
ms.openlocfilehash: 454113f66007ddd69f8455bb532e9cbd12fcefb7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738704"
---
# <a name="security-of-custombinding"></a>\<security> / \<customBinding>
Özel bağlama için güvenlik seçeneklerini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security allowSerializedSigningTokenOnReply="Boolean"
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
          securityHeaderLayout="Strict/Lax/LaxTimestampFirst/LaxTimestampLast">
   <issuedTokenParameters />
   <localClientSettings />
   <localServiceSettings />
   <secureConversationBootstrap />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|allowSerializedSigningTokenOnReply|İsteğe bağlı. Seri hale getirilmiş bir belirtecin yanıt olarak kullanılabileceğini belirten bir Boole değeri. Varsayılan değer: `false`. İkili bağlama kullanılırken, varsayılan ayar olarak olarak `true` değişir ve yapılan ayar yok sayılır.|  
|authenticationMode|İsteğe bağlı. Başlatıcı ve Yanıtlayıcı arasında kullanılan kimlik doğrulama modunu belirtir. Tüm değerler için aşağıya bakın.<br /><br /> Varsayılan değer: `sspiNegotiated`.|  
|defaultAlgorithmSuite|İsteğe bağlı. İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> . Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Olası değerler aşağıda gösterilmiştir. Varsayılan değer: `Basic256`.<br /><br /> Bu öznitelik, varsayılandan farklı bir algoritma kümesi için çalışan farklı bir platformda çalışırken kullanılır. Bu ayarda değişiklik yaparken ilgili algoritmaların güçlerinin ve zayıflığının farkında olmanız gerekir. Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .|  
|IncludeTimestamp|Her iletiye zaman damgalarının dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.|  
|keyEntropyMode|Güvenli iletiler için anahtarların hesaplanma şeklini belirtir. Anahtarlar yalnızca hizmet anahtarı malzemeden veya her ikisinin bir birleşimi olan istemci anahtar malzemesini temel alabilir. Geçerli değerler şunlardır<br /><br /> -   `ClientEntropy`: Oturum anahtarı, istemci tarafından sağlanmış olan anahtar verileri temel alır.<br />-   `ServerEntropy`: Oturum anahtarı, sunucu tarafından sağlanmış olan anahtar verileri temel alır.<br />-   `CombinedEntropy`: Oturum anahtarı, istemci ve hizmet tarafından sunulan anahtar verileri temel alır.<br /><br /> Varsayılan değer: `CombinedEntropy`.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .|  
|messageProtectionOrder|İletiye ileti düzeyi güvenlik algoritmalarının uygulanma sırasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -   `SignBeforeEncrypt`: Önce imzala, sonra şifreleyin.<br />-   `SignBeforeEncryptAndEncryptSignature`: Önce imzalayın, sonra imzayı şifreleyin.<br />-   `EncryptBeforeSign`: Önce şifreleyin, ardından imzalayın.<br /><br /> Varsayılan değer, kullanılmakta olan WS-Security sürümüne bağlıdır. Varsayılan değer `SignBeforeEncryptAndEncryptSignature` WS-Security 1,1 ' i kullanmaktır. Varsayılan değer `SignBeforeEncrypt` WS-Security 1,0 ' i kullanmaktır.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.Security.MessageProtectionOrder> .|  
|messageSecurityVersion|İsteğe bağlı. Kullanılan WS-güvenlik sürümünü ayarlar. Geçerli değerler şunlardır:<br /><br /> - WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11<br />- WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br />- WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10<br /><br /> Varsayılan değer WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11 ' dir ve XML 'de yalnızca olarak ifade edilebilir `Default` . Bu öznitelik türü <xref:System.ServiceModel.MessageSecurityVersion> .|  
|requireDerivedKeys|Anahtarların orijinal kanıt anahtarlarından türetilip türetilemeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.|  
|requireSecurityContextCancellation|İsteğe bağlı. Artık gerekli olmadığında güvenlik bağlamının iptal edilip edilmemesi gerektiğini belirten bir Boolean değer. Varsayılan değer: `true`.|  
|requireSignatureConfirmation|İsteğe bağlı. WS-güvenlik imza doğrulamasının etkin olup olmadığını belirten bir Boolean değer. Olarak ayarlandığında `true` ileti imzaları Yanıtlayıcı tarafından onaylanır.  Özel bağlama karşılıklı sertifikalara yapılandırıldığında veya verilen belirteçleri (WSS 1,1 bağlamaları) kullanmak üzere yapılandırıldığında, bu özniteliğin varsayılan değeri olarak ayarlanır `true` . Aksi takdirde, varsayılan olur `false` .<br /><br /> İmza onayı, hizmetin bir isteğin tam olarak farkında olarak yanıt verdiğini doğrulamak için kullanılır.|  
|securityHeaderLayout|İsteğe bağlı. Güvenlik üst bilgisindeki öğelerin sıralamasını belirtir. Geçerli değerler şunlardır<br /><br /> -   `Strict`: Öğeler, "kullanmadan önce bildir" genel ilkesine göre güvenlik üstbilgisine eklenir.<br />-   `Lax`: Öğeler güvenlik başlığına, WSS: SOAP Ileti güvenliği olduğunu doğrulayan herhangi bir sırada eklenir.<br />-   `LaxWithTimestampFirst`: Güvenlik üst bilgisindeki ilk öğe bir WSO: Timestamp öğesi olması dışında, öğeler güvenlik başlığına, WSS: SOAP Ileti güvenliği ' ni doğrulayan herhangi bir sırada eklenir.<br />-   `LaxWithTimestampLast`: Öğeler güvenlik başlığına, güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp öğesi olması dışında, WSS: SOAP Iletisi güvenliği olan herhangi bir sıraya eklenir.<br /><br /> Varsayılan değer: `Strict`.<br /><br /> Bu öğe türündedir <xref:System.ServiceModel.Channels.SecurityHeaderLayout> .|  
  
## <a name="authenticationmode-attribute"></a>authenticationMode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Dize|`AnonymousForCertificate`<br /><br /> `AnonymousForSslNegotiated`<br /><br /> `CertificateOverTransport`<br /><br /> `IssuedToken`<br /><br /> `IssuedTokenForCertificate`<br /><br /> `IssuedTokenForSslNegotiated`<br /><br /> `IssuedTokenOverTransport`<br /><br /> `Kerberos`<br /><br /> `KerberosOverTransport`<br /><br /> `MutualCertificate`<br /><br /> `MutualCertificateDuplex`<br /><br /> `MutualSslNegotiated`<br /><br /> `SecureConversation`<br /><br /> `SspiNegotiated`<br /><br /> `UserNameForCertificate`<br /><br /> `UserNameForSslNegotiated`<br /><br /> `UserNameOverTransport`<br /><br /> `SspiNegotiatedOverTransport`|  
  
## <a name="defaultalgorithm-attribute"></a>Defaultalgorithd özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|Anahtar kaydırması için AES128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.|  
|Basic192|Anahtar kaydırması için Aes192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256|Anahtar kaydırması için AES256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256Rsa15|İleti şifreleme için AES256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Rsa15|İleti şifreleme için Aes192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDes|Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic128Rsa15|İleti şifreleme için AES128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesRsa15|TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic128Sha256|İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic192Sha256|İleti için Aes192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic256Sha256|İleti için AES256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|TripleDesSha256|İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme için AES128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme için Aes192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme için AES256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesSha256Rsa15|İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|Geçerli bir verilen belirteç belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement> .|  
|[\<localClientSettings>](localclientsettings-element.md)|Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement> .|  
|[\<localServiceSettings>](localservicesettings-element.md)|Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement> .|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğeyi kullanma hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](../../../wcf/feature-details/securitybindingelement-authentication-modes.md) ve [nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel bağlama kullanılarak güvenliğin nasıl yapılandırılacağını gösterir. Güvenli bir aktarımla ileti düzeyi güvenliği etkinleştirmek için özel bağlamayı nasıl kullanacağınızı gösterir. Bu, iletileri istemci ve hizmet arasında iletmek için güvenli bir aktarım gerektiğinde ve iletilerin ileti düzeyinde güvenli olması gerektiği durumlarda yararlıdır. Bu yapılandırma sistem tarafından belirtilen bağlamalar tarafından desteklenmiyor.  
  
 Hizmet yapılandırması, TLS/SSL protokolü ve Windows ileti güvenliği kullanılarak korunan TCP iletişimini destekleyen özel bir bağlama tanımlar. Özel bağlama, Aktarım düzeyinde hizmetin kimliğini doğrulamak ve istemci ile hizmet arasında iletim sırasında iletileri korumak için bir hizmet sertifikası kullanır. Bu, [\<sslStreamSecurity>](sslstreamsecurity.md) Binding öğesi tarafından gerçekleştirilir. Hizmetin sertifikası bir hizmet davranışı kullanılarak yapılandırılır.  
  
 Ayrıca, özel bağlama Windows kimlik bilgisi türü ile ileti güvenliği kullanır-bu, varsayılan kimlik bilgisi türüdür. Bu, [güvenlik](security-of-custombinding.md) bağlama öğesi tarafından gerçekleştirilir. Kerberos kimlik doğrulama mekanizması kullanılabilirse, istemci ve hizmetin her ikisi de ileti düzeyi güvenlik kullanılarak doğrulanır. Kerberos kimlik doğrulama mekanizması kullanılamıyorsa, NTLM kimlik doğrulaması kullanılır. NTLM, istemcinin hizmet kimliğini doğrular, ancak istemciye hizmetin kimliğini doğrulamaz. [Güvenlik](security-of-custombinding.md) bağlama öğesi, `SecureConversation` hem istemcide hem de hizmette bir güvenlik oturumu oluşturulmasına neden olan AuthenticationType kullanmak üzere yapılandırılmıştır. Bu, hizmetin çift yönlü sözleşmesinin çalışmasını sağlamak için gereklidir. Bu örneği çalıştırma hakkında daha fazla bilgi için bkz. [özel bağlama güvenliği](../../../wcf/samples/custom-binding-security.md).  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <sslStreamSecurity requireClientCertificate="false" />
          <tcpTransport />
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
            <serviceCertificate findValue="localhost"
                                storeLocation="LocalMachine"
                                storeName="My"
                                x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.SecurityElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
