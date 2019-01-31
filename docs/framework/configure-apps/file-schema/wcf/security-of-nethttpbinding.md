---
title: <security> , <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: f2750036aa4d3fbe41062ad041e50ff3a4be32b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283978"
---
# <a name="security-of-nethttpbinding"></a>\<Güvenlik >, \<netHttpBinding >

Güvenlik yeteneklerini tanımlar [ \<basicHttpBinding >](basichttpbinding.md).

\<sistemi. ServiceModel > \
\<bağlamaları > \
\<netHttpBinding > \
\<bağlama > \
\<Güvenlik >

## <a name="syntax"></a>Sözdizimi

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|mod|İsteğe bağlı. Kullanılan güvenlik türünü belirtir. Varsayılan, `None` değeridir. Bu öznitelik türünde <xref:System.ServiceModel.BasicHttpSecurityMode>.|

## <a name="mode-attribute"></a>mod özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|Hiçbiri|-Sıradaki iletiler, aktarım sırasında sağlanmaz.|
|Taşıma|HTTPS aktarımı kullanarak güvenliği sağlanır. SOAP iletilerini HTTPS kullanılarak güvenli hale getirilir. Hizmet, hizmetin X.509 sertifikası kullanarak istemci kimlik doğrulaması yapılır. İstemci tarafından sağlanan ClientCredentialType kullanarak kimlik doğrulaması yapılır.|
|İleti|SOAP ileti güveliği kullanarak güvenliği sağlanır. Varsayılan olarak, gövde imzalı ve şifrelenir. Bu bağlama için sistem sunucu sertifikası istemciyi bant dışından sağlanmasını gerektirir. Yalnızca geçerli `ClientCredentialType` Bu bağlama için `Certificate`.|
|TransportWithMessageCredential|Bütünlüğü, gizliliği ve sunucu kimlik doğrulaması ile Aktarım güvenliği sağlanır. İstemci kimlik doğrulaması yoluyla SOAP ileti güvenliği sağlanır. Bu mod, kullanıcının kullanıcı adı/parola kullanarak kimlik doğrulaması ve ileti aktarım güvenliğini sağlamak için var olan bir HTTP dağıtım olduğunda geçerlidir.|
|TransportCredentialOnly|Bu mod, ileti bütünlüğü ve gizliliği sağlamaz. Bu, http tabanlı istemci kimlik doğrulaması sağlar. Bu mod, dikkatli kullanılmalıdır. Burada aktarım güvenliği (IPSec gibi) diğer yollarla sağlanmaktadır ve yalnızca istemci kimlik doğrulaması WCF altyapısı tarafından sağlanan ortamlarda kullanılmalıdır.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<taşıma >](transport-of-nethttpbinding.md)|Temel HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.HttpTransportSecurity>.|
|[\<İleti >](message-of-nethttpbinding.md)|Temel HTTP hizmeti için ileti güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.BasicHttpMessageSecurity>.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|bağlama|Bağlama öğesi [ \<basicHttpBinding >](basichttpbinding.md).|

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, SOAP ileti güvenli olmadığından ve istemci kimliği doğrulanmamış. Bu öğe için ek güvenlik ayarları yapılandırmanızı sağlar `netHttpBinding` öğesi.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
