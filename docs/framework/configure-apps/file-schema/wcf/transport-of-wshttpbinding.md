---
title: <transport> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732744"
---
# <a name="transport-of-wshttpbinding"></a>\<transport> / \<wsHttpBinding>

HTTP taşıması için kimlik doğrulama ayarlarını tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a>Sözdizimi

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a>Tür

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`clientCredentialType`|Hizmetin istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .|
|`proxyCredentialType`|Bir etki alanı ara sunucusu için istemcinin kimliğini doğrulamak için kullanılan kimlik bilgisini belirtir. Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .|
|`realm`|Özet veya temel kimlik doğrulaması için kimlik doğrulama bölgesini belirten bir dize. Varsayılan değer boş bir dizedir.<br /><br /> Kimlik doğrulama bölgesi, kimlik doğrulamasını gerçekleştiren konağın en azından adını belirtir. Ayrıca, erişimi olan bir kullanıcı koleksiyonu da belirtebilir. Kullanıcı, birkaç olası Kullanıcı adı ve parolanın kullanılabileceğini belirlemek için kimlik doğrulama bölgesini sorgulayabilir.|
|`policyEnforcement`|Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.<br /><br /> 1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).<br />2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.<br />3. her zaman – ilke her zaman zorlanır. Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.|

## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`None`|Güvenlik devre dışı bırakıldı.|
|`Basic`|Temel kimlik doğrulamasını kullanır.|
|`Digest`|Özet kimlik doğrulaması kullanır.|
|`Ntlm`|Windows etki alanı ile geri dönüş olarak NTLM kimlik doğrulamasını kullanır.|
|`Windows`|Tümleşik Windows kimlik doğrulamasını kullanır.|
|`Certificate`|İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.|

## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|`None`|Güvenlik devre dışı bırakıldı.|
|`Basic`|Temel kimlik doğrulamasını kullanır.|
|`Digest`|Özet kimlik doğrulaması kullanır.|
|`Ntlm`|Windows etki alanı ile geri dönüş olarak NTLM kullanır.|
|`Windows`|Tümleşik Windows kimlik doğrulamasını kullanır.|
|`Certificate`|İstemcinin kimliğini doğrulamak için X. 509.440 sertifikalarını kullanır.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|Öğesinin güvenlik yeteneklerini temsil eder [\<wsHttpBinding>](wshttpbinding.md) .|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
