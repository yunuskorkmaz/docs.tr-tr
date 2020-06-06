---
title: <message> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: 3396f74f76d790759f4c32de2907607486701b1a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738953"
---
# <a name="message-of-ws2007httpbinding"></a>\<message> / \<ws2007HttpBinding>
Öğenin ileti düzeyi güvenliği için ayarları tanımlar [\<ws2007HttpBinding>](ws2007httpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
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
|`algorithmSuite`|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> . Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Varsayılan değer Basic256 ' dir.|  
|`clientCredentialType`|İsteğe bağlı. Güvenlik modunu kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir `Message` `TransportWithMessageCredentials` . Aşağıdaki tablodaki numaralandırma değerlerine bakın. Varsayılan olarak Windows.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .|  
|`establishSecurityContext`|Güvenlik kanalının güvenli bir oturum kurup kurmadığını belirleyen bir değer. Güvenli bir oturum, uygulama iletilerini değiş tokuş etmeden önce bir güvenlik bağlamı belirteci (SCT) oluşturur. SCT oluşturulduğunda güvenlik kanalı, <xref:System.ServiceModel.Channels.ISession> üst kanallara yönelik bir arabirim sunar. Güvenli oturumları kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli oturum oluşturma](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Varsayılan değer: `true`.|  
|`negotiateServiceCredential`|İsteğe bağlı. Hizmet kimlik bilgisinin istemcide bant dışı olarak sağlandığını veya bir anlaşma sürecinde hizmetten istemciye elde edilip edilmeyeceğini belirten bir değer. Bu tür bir anlaşma, olağan ileti alışverişi için bir precurslı ' dır.<br /><br /> `clientCredentialType`Öznitelik None, username veya Certificate değerine eşitse, bu özniteliği, `false` hizmet sertifikasının bant dışı olarak ayarlanması ve istemcinin hizmet davranışındaki hizmet sertifikasını (kullanarak) belirtmesi gerektiğini gösterir [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) [\<serviceCredentials>](servicecredentials.md) . Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> `ClientCredentialType`Özniteliği olarak ayarlandıysa `Windows` , bu özniteliği `false` Kerberos tabanlı kimlik doğrulamasını belirtir. Bu, istemci ve hizmetin aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod, Kerberos belirteç profilini (OASSıS WSS TC ' de tanımlandığı şekilde) ve WS-Trust ve WS-SecureConversation ' i uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik olduğunda `true` , <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> SOAP iletileri üzerinden Exchange 'i tünelle BIR .NET SOAP anlaşmasına neden olur.<br /><br /> Varsayılan değer: `true`.|  
  
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
|`Certificate`|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. `message`Güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği olarak ayarlandıysa `false` , istemci hizmet sertifikası ile sağlanmalıdır.|  
|`IssuedToken`|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteci belirtir.|  
|`UserName`|Hizmetin kimlik bilgileri kullanılarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar `UserName` . WCF parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, kimlik bilgileri kullanılırken taşımanın güvenli hale getirilme işlemi uygular `UserName` . Bu kimlik bilgisi modu, özelliği temel alan, birlikte çalışabilen bir Exchange veya birlikte çalışabilen bir anlaşma ile sonuçlanır `negotiateServiceCredential` .|  
|`Windows`|SOAP değişimlerinin kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar `Windows` . `negotiateServiceCredential`Özniteliği olarak ayarlandıysa `true` , bu ya bir SSPI anlaşması veya Kerberos (birlikte çalışabilen bir standart) gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|Bir için güvenlik ayarlarını tanımlar [\<ws2007HttpBinding>](ws2007httpbinding.md) .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
