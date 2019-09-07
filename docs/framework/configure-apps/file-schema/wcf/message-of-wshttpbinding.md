---
title: <message> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 8cb8879d866eca3b1dafbd139de39373874dad14
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397802"
---
# <a name="message-of-wshttpbinding"></a>\<\<WSHttpBinding > ileti >
WSHttpBinding > ileti düzeyinde güvenliğe [ \<](wshttpbinding.md)yönelik ayarları tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**  
  
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
|algorithmSuite|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfına göre belirlenir. Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Varsayılan değer `Basic256` şeklindedir.|  
|clientCredentialType|İsteğe bağlı. Güvenlik modunu `Message` `TransportWithMessageCredentials`kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Aşağıdaki numaralandırma değerlerine bakın. Varsayılan, `Windows` değeridir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Güvenlik kanalının güvenli bir oturum kurup kurmadığını belirleyen bir Boole değeri. Güvenli bir oturum, uygulama iletilerini değiş tokuş etmeden önce bir güvenlik bağlamı belirteci (SCT) oluşturur. SCT oluşturulduğunda güvenlik kanalı, üst kanallara yönelik bir <xref:System.ServiceModel.Channels.ISession> arabirim sunar. Güvenli oturumları kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Güvenli bir oturum](../../../wcf/feature-details/how-to-create-a-secure-session.md)oluşturun.<br /><br /> Varsayılan değer `true` şeklindedir.|  
|negotiateServiceCredential|İsteğe bağlı. Hizmet kimlik bilgisinin istemci bant dışı olarak sağlanıp sağlanmadığını veya hizmetten istemciye bir anlaşma sürecinde elde edilip edilmeyeceğini belirten bir Boole değeri. Bu tür bir anlaşma, olağan ileti alışverişi için bir precurslı ' dır.<br /><br /> Öznitelik None, username veya Certificate değerine eşitse, bu `false` özniteliği ayarı hizmet sertifikasının bant dışı ve istemcinin hizmet sertifikasını belirtmesi gerektiği anlamına gelir ( `clientCredentialType` ServiceCertificate >), [ \<ServiceCredentials >](servicecredentials.md) hizmet davranışında. [ \<](servicecertificate-of-servicecredentials.md) Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Özniteliği olarak `Windows` ayarlandıysa`false` , bu özniteliği Kerberos tabanlı kimlik doğrulamasını belirtir. `ClientCredentialType` Bu, istemci ve hizmetin aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod, Kerberos belirteç profilini (OASSıS WSS TC ' de tanımlandığı gibi) ve WS-Trust ve WS-SecureConversation ' i uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik `true`olduğunda, SOAP iletileri üzerinde SPNEGO Exchange tünelini sağlayan bir .NET SOAP anlaşmasına neden olur.<br /><br /> Varsayılan, `true` değeridir.|  
  
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
|Yok.|Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Hizmet tarafında bu, hizmetin hiçbir istemci kimlik bilgisi gerektirmediğini belirtir. İstemcide Bu, istemcinin hiçbir istemci kimlik bilgisi sunmadığını gösterir.|  
|Sertifika|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği olarak `false`ayarlandıysa, istemcinin hizmet sertifikasıyla sağlanması gerekir.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti tarafından verilen özel bir belirteci belirtir.|  
|UserName|Hizmetin, istemcinin bir Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını gerektirmesini sağlar. WCF parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorunlu kılar. Bu kimlik bilgisi modu, özelliği temel alan, `negotiateServiceCredential` birlikte çalışabilen bir Exchange veya birlikte çalışabilen bir anlaşma ile sonuçlanır.|  
|Windows|SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. `negotiateServiceCredential` Özniteliği olarak`true`ayarlandıysa, bu ya bir SSPI anlaşması veya Kerberos (birlikte çalışabilen bir standart) gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-wshttpbinding.md)|[ Bir\<WSHttpBinding >](wshttpbinding.md)için güvenlik ayarlarını tanımlar.|  
  
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
