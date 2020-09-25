---
title: <message> öğesi <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
ms.openlocfilehash: ab767a5a1179de81bf9a8adc61799ede2d915ac1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204911"
---
# <a name="message-element-of-nettcpbinding"></a>\<message> öğesi \<netTcpBinding>

İle yapılandırılmış bir uç nokta için ileti düzeyi güvenlik gereksinimlerinin türünü tanımlar [\<netTcpBinding>](nettcpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<message algorithmSuite="System.Servicemodel.Security.SecurityAlgorithmsuite"
         clientCredentialType="None/Windows/UserName/Certificate/IssuedToken" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`algorithmSuite`|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Algoritmalar ve anahtar boyutları sınıfına göre belirlenir <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> . Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Olası değerler aşağıdaki tabloda gösterilmiştir. Varsayılan değer: `Basic256`.<br /><br /> Hizmet bağlaması `algorithmSuite` varsayılan değere eşit olmayan bir değer belirtiyorsa ve Svcutil.exe kullanarak yapılandırma dosyasını oluşturursanız, doğru şekilde oluşturulmaz ve bu özniteliği istenen değere ayarlamak için yapılandırma dosyasını el ile düzenlemeniz gerekir.|  
|`clientCredentialType`|Ileti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Olası değerler aşağıdaki tabloda gösterilmiştir. Varsayılan değer: `UserName`. Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .|  
  
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
|Yok|Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Hizmette, bu hizmetin hiçbir istemci kimlik bilgisi gerektirmediğini belirtir. İstemcide Bu, istemcinin hiçbir istemci kimlik bilgisi sunmadığını gösterir.|  
|Windows|SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar.|  
|UserName|Hizmetin, istemcinin bir Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını gerektirmesini sağlar. WCF parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorunlu kılar. Bu kimlik bilgisi modu, özelliği temel alan, birlikte çalışabilen bir Exchange veya birlikte çalışabilen bir anlaşma ile sonuçlanır `negotiateServiceCredential` .|  
|Sertifika|Hizmetin, bir sertifika kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği olarak ayarlandıysa `false` , istemci hizmet sertifikası ile sağlanmalıdır.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteci belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|İçin güvenlik yeteneklerini tanımlar <xref:System.ServiceModel.Configuration.NetTcpBindingElement> .|  
  
## <a name="remarks"></a>Açıklamalar  

 İleti, SOAP iletisinin bütünlüğü ve gizliliği için ve iletişim eşlerinin karşılıklı kimlik doğrulaması için ileti düzeyi güvenliği kullanır. Bu güvenlik modu bir bağlamada seçilirse, kanal yığını ileti güvenliği bağlama öğeleriyle yapılandırılır ve SOAP iletileri WS-Security * standartları ile uyumlu olarak korunur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.MessageSecurityOverTcp>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
