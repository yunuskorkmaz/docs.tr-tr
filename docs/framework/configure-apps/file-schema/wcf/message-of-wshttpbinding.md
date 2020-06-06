---
title: <message> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 5a4d7bb41a57ca25397f585a2d5684ca6abdfa33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738974"
---
# <a name="message-of-wshttpbinding"></a>\<message> / \<wsHttpBinding>
İleti düzeyi güvenliği için ayarları tanımlar [\<wsHttpBinding>](wshttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
         establishSecurityContext="Boolean"
         negotiateServiceCredential="Boolean" />
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> . Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Varsayılan değer: `Basic256`.|  
|clientCredentialType|İsteğe bağlı. Güvenlik modunu kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir `Message` `TransportWithMessageCredentials` . Aşağıdaki numaralandırma değerlerine bakın. Varsayılan değer: `Windows`.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .|  
|establishSecurityContext|Güvenlik kanalının güvenli bir oturum kurup kurmadığını belirleyen bir Boole değeri. Güvenli bir oturum, uygulama iletilerini değiş tokuş etmeden önce bir güvenlik bağlamı belirteci (SCT) oluşturur. SCT oluşturulduğunda güvenlik kanalı, <xref:System.ServiceModel.Channels.ISession> üst kanallara yönelik bir arabirim sunar. Güvenli oturumları kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli oturum oluşturma](../../../wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Varsayılan değer: `true`.|  
|negotiateServiceCredential|İsteğe bağlı. Hizmet kimlik bilgisinin istemci bant dışı olarak sağlanıp sağlanmadığını veya hizmetten istemciye bir anlaşma sürecinde elde edilip edilmeyeceğini belirten bir Boole değeri. Bu tür bir anlaşma, olağan ileti alışverişi için bir precurslı ' dır.<br /><br /> `clientCredentialType`Öznitelik None, username veya Certificate değerine eşitse, bu özniteliği ayarlamak `false` hizmet sertifikasının bant dışı ve istemcinin [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) hizmet davranışındaki hizmet sertifikasını (kullanarak) belirtmesi gerektiğini gösterir [\<serviceCredentials>](servicecredentials.md) . Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> `ClientCredentialType`Özniteliği olarak ayarlandıysa `Windows` , bu özniteliği `false` Kerberos tabanlı kimlik doğrulamasını belirtir. Bu, istemci ve hizmetin aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod, Kerberos belirteç profilini (OASSıS WSS TC ' de tanımlandığı gibi) ve WS-Trust ve WS-SecureConversation ' i uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik olduğunda `true` , SOAP iletileri üzerinde SPNEGO Exchange tünelini sağlayan bir .NET SOAP anlaşmasına neden olur.<br /><br /> Varsayılan değer: `true`.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|Anahtar kaydırması için Basic128 şifrelemesi, ileti özeti için SHA1 ve rsa-oaep-mgf1p kullanın.|  
|Basic192|Anahtar kaydırması için Basic192 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256|Anahtar kaydırması için Basic256 şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic256Rsa15|İleti şifreleme için Basic256, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Rsa15|İleti şifreleme için Basic192, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDes|Anahtar kaydırması için, TripleDes şifrelemesi, ileti özeti için SHA1, rsa-oaep-mgf1p kullanın.|  
|Basic128Rsa15|İleti şifreleme için Basic128, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesRsa15|TripleDes şifrelemesi, ileti özeti için SHA1 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic128Sha256|İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic192Sha256|İleti için Basic192, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|Basic256Sha256|İleti için Basic256, ileti özeti için SHA256, anahtar kaydırması için rsa-oaep-mgf1p kullanın.|  
|TripleDesSha256|İleti şifreleme için TripleDes, SHA256 for Message Digest ve rsa-oaep-mgf1p için anahtar kaydırması kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme için Basic128, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme için Basic192, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme için Basic256, ileti özeti için SHA256 ve anahtar kaydırması için Rsa15 kullanın.|  
|TripleDesSha256Rsa15|İleti şifreleme için TripleDes, SHA256 for Message Digest ve Rsa15 anahtar kaydırması için kullanın.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok|Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Hizmet tarafında bu, hizmetin hiçbir istemci kimlik bilgisi gerektirmediğini belirtir. İstemcide Bu, istemcinin hiçbir istemci kimlik bilgisi sunmadığını gösterir.|  
|Sertifika|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği olarak ayarlandıysa `false` , istemcinin hizmet sertifikasıyla sağlanması gerekir.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti tarafından verilen özel bir belirteci belirtir.|  
|UserName|Hizmetin, istemcinin bir Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını gerektirmesini sağlar. WCF parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorunlu kılar. Bu kimlik bilgisi modu, özelliği temel alan, birlikte çalışabilen bir Exchange veya birlikte çalışabilen bir anlaşma ile sonuçlanır `negotiateServiceCredential` .|  
|Windows|SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. `negotiateServiceCredential`Özniteliği olarak ayarlandıysa `true` , bu ya bir SSPI anlaşması veya Kerberos (birlikte çalışabilen bir standart) gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-wshttpbinding.md)|Bir için güvenlik ayarlarını tanımlar [\<wsHttpBinding>](wshttpbinding.md) .|  
  
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
