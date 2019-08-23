---
title: <message> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 59449ec5f8f048e27313d088be0ca951915ef5e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931499"
---
# <a name="message-of-ws2007httpbinding"></a>\<\<WS2007HttpBinding > ileti >
WS2007HttpBinding > öğesinin ileti düzeyi güvenliğine [ \<](ws2007httpbinding.md) yönelik ayarları tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<ws2007HttpBinding>  
\<bağlama >  
\<Güvenlik >  
\<ileti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007HttpBinding>
  <binding>
    <security>
      <message clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"
               establishSecurityContext="Boolean"
               negotiateServiceCredential="Boolean"
               algorithmSuite="Enumeration. See algorithmSuite Attribute below."
               defaultProtectionLevel="None/Sign/EncryptionAndSign" />
    </security>
  </binding>
</ws2007HttpBinding>
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`algorithmSuite`|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfına göre belirlenir. Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Varsayılan değer Basic256 ' dir.|  
|`clientCredentialType`|İsteğe bağlı. Güvenlik modunu `Message` `TransportWithMessageCredentials`kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Aşağıdaki tablodaki numaralandırma değerlerine bakın. Varsayılan olarak Windows.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Güvenlik kanalının güvenli bir oturum kurup kurmadığını belirleyen bir değer. Güvenli bir oturum, uygulama iletilerini değiş tokuş etmeden önce bir güvenlik bağlamı belirteci (SCT) oluşturur. SCT oluşturulduğunda güvenlik kanalı, üst kanallara yönelik bir <xref:System.ServiceModel.Channels.ISession> arabirim sunar. Güvenli oturumları kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Güvenli bir oturum](../../../wcf/feature-details/how-to-create-a-secure-session.md)oluşturun.<br /><br /> Varsayılan değer `true` şeklindedir.|  
|`negotiateServiceCredential`|İsteğe bağlı. Hizmet kimlik bilgisinin istemcide bant dışı olarak sağlandığını veya bir anlaşma sürecinde hizmetten istemciye elde edilip edilmeyeceğini belirten bir değer. Bu tür bir anlaşma, olağan ileti alışverişi için bir precurslı ' dır.<br /><br /> Öznitelik None, username veya Certificate değerine eşitse, bu `false` özniteliğin ayarlanması hizmet sertifikasının bant dışı ve istemcinin hizmet sertifikasını belirtmesi gerektiğini belirtir ( `clientCredentialType` [ ServiceCertificate\<>](servicecertificate-of-servicecredentials.md)) ServiceCredentials > hizmet davranışında. [ \<](servicecredentials.md) Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Özniteliği olarak `Windows` ayarlandıysa`false` , bu özniteliği Kerberos tabanlı kimlik doğrulamasını belirtir. `ClientCredentialType` Bu, istemci ve hizmetin aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod, Kerberos belirteç profilini (OASSıS WSS TC ' de tanımlandığı şekilde) ve WS-Trust ve WS-SecureConversation ' i uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik `true`olduğunda, SOAP iletileri üzerinden Exchange 'i tünelle <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> bir .NET SOAP anlaşmasına neden olur.<br /><br /> Varsayılan, `true` değeridir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
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
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Hizmette, bu hizmetin hiçbir istemci kimlik bilgisi gerektirmediğini belirtir. İstemcide Bu, istemcinin hiçbir istemci kimlik bilgisi sunmadığını gösterir.|  
|`Certificate`|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. Güvenlik modu kullanılıyorsa `negotiateServiceCredential` ve özniteliği olarak `false`ayarlandıysa, istemci hizmet sertifikası ile sağlanmalıdır. `message`|  
|`IssuedToken`|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteci belirtir.|  
|`UserName`|Hizmetin `UserName` kimlik bilgileri kullanılarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. WCF parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, kimlik bilgileri kullanılırken `UserName` taşımanın güvenli hale getirilme işlemi uygular. Bu kimlik bilgisi modu, özelliği temel alan, `negotiateServiceCredential` birlikte çalışabilen bir Exchange veya birlikte çalışabilen bir anlaşma ile sonuçlanır.|  
|`Windows`|SOAP değişimlerinin `Windows` kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. `negotiateServiceCredential` Özniteliği olarak`true`ayarlandıysa, bu ya bir SSPI anlaşması veya Kerberos (birlikte çalışabilen bir standart) gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-ws2007httpbinding.md)|[ Bir\<WS2007HttpBinding >](ws2007httpbinding.md)için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
