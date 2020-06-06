---
title: <security> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736485"
---
# <a name="security-of-nethttpbinding"></a>\<security> / \<netHttpBinding>

Uygulamasının güvenlik yeteneklerini tanımlar [\<netHttpBinding>](nethttpbinding.md) .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

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
|mod|İsteğe bağlı. Kullanılan güvenlik türünü belirtir. Varsayılan değer: `None`. Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode> .|

## <a name="mode-attribute"></a>mode özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|Yok|-İletiler aktarım sırasında güvenli değildir.|
|Aktarım|Güvenlik, HTTPS taşıması kullanılarak sağlanır. SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır. Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır. İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır.|
|İleti|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, gövde şifrelenir ve imzalanır. Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir. `ClientCredentialType`Bu bağlama için geçerli tek geçerlidir `Certificate` .|
|TransportWithMessageCredential|Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır. İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır. Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.|
|Yalnızca transportcredential|Bu mod ileti bütünlüğü ve gizliliği sağlamaz. HTTP tabanlı istemci kimlik doğrulaması sağlar. Bu mod dikkatli kullanılmalıdır. Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar. Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.HttpTransportSecurity> .|
|[\<message>](message-of-nethttpbinding.md)|Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar. Bu öğe öğesine karşılık gelir <xref:System.ServiceModel.BasicHttpMessageSecurity> .|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|bağlama|Öğesinin bağlama öğesi [\<basicHttpBinding>](basichttpbinding.md) .|

## <a name="remarks"></a>Açıklamalar

 Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz. Bu öğe, öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar `netHttpBinding` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
