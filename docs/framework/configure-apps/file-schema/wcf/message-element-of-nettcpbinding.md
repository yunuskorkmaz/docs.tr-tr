---
title: "&lt;netTcpBinding&gt; &lt;ileti&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d71edd9-c085-4c2e-b6d3-980c313366f9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae44c80f99b2753b4914ff0844fd9538f3ac3f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltnettcpbindinggt"></a>&lt;netTcpBinding&gt; &lt;ileti&gt; öğesi
İleti düzeyi güvenlik gereksinimleri ile yapılandırılmış bir uç nokta türünü tanımlar [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netTcpBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message   
      algorithmSuite=System.Servicemodel.Security.SecurityAlgorithmsuite  
    clientCredentialType="None/Windows/UserName/Certificate/IssuedToken"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`algorithmSuite`|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.<br /><br /> Olası değerler aşağıdaki tabloda gösterilmiştir. Varsayılan değer `Basic256` şeklindedir.<br /><br /> Hizmet bağlama belirtiyorsa bir `algorithmSuite` varsayılan ve sizin için eşit olmayan değer üretmek Svcutil.exe, kullanarak yapılandırma dosyasını sonra doğru oluşturulmaz ve bu özniteliği ayarlamak için yapılandırma dosyasını el ile düzenlemeniz gerekir İstenen değeri.|  
|`clientCredentialType`|İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir. Olası değerler aşağıdaki tabloda gösterilmiştir. Varsayılan değer `UserName` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
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
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|Bu hizmetin anonim istemcilerle etkileşime girmesine izin verir. Hizmette bu hizmeti istemci kimlik gerektirmez gösterir. İstemcide, bu istemciyi istemci kimlik sağlamaz gösterir.|  
|Windows|SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar.|  
|UserName|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]bir parola Özet gönderirken ya da parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak anahtarları türetme desteklemez. Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar. Bu kimlik bilgisi modu birlikte çalışabilir exchange veya temel çalışabilen olmayan bir anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|Sertifika|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası sağlanmalıdır.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteç belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|Güvenlik özellikleri için tanımlar <xref:System.ServiceModel.Configuration.NetTcpBindingElement>.|  
  
## <a name="remarks"></a>Açıklamalar  
 İleti bütünlüğü ve gizliliği SOAP iletisi ve karşılıklı kimlik doğrulama iletişimi eş için ileti düzeyi güvenlik kullanır. Bağlamada bu güvenlik modunu seçtiyseniz, kanal yığını ile ileti güvenliği bağlama öğeleri yapılandırılır ve SOAP iletilerine uyumlu WS güvenliği sağlanan-güvenlik * standartları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.MessageSecurityOverTcp>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
