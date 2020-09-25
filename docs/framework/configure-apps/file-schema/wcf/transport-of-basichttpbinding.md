---
title: <transport> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: d575b7e282775e2e2c498ac94bb54a563b8d125e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201401"
---
# <a name="transport-of-basichttpbinding"></a>\<transport> / \<basicHttpBinding>

HTTP taşıması için kimlik doğrulama parametrelerini denetleyen özellikleri tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientCredentialType|-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir.  Varsayılan değer: `None`. Bu öznitelik türü <xref:System.ServiceModel.HttpClientCredentialType> .|  
|proxyCredentialType|-HTTP üzerinden proxy kullanan bir etki alanı içinden istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Bu öznitelik yalnızca `mode` üst öğenin özniteliği veya olduğunda geçerlidir `security` `Transport` `TransportCredentialsOnly` . Bu öznitelik türü <xref:System.ServiceModel.HttpProxyCredentialType> .|  
|bölgesindeki|Özet veya temel kimlik doğrulaması için HTTP kimlik doğrulama düzeni tarafından kullanılan bölgeyi belirten bir dize. Varsayılan değer boş bir dizedir.|  
|policyEnforcement|Bu numaralandırma, ne zaman <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> uygulanacağını belirtir.<br /><br /> 1. hiçbir süre – ilke hiçbir şekilde zorlanmaz (genişletilmiş koruma devre dışı bırakılır).<br />2. WhenSupported – ilke yalnızca istemci genişletilmiş korumayı destekliyorsa zorlanır.<br />3. her zaman – ilke her zaman zorlanır. Genişletilmiş korumayı desteklemeyen istemciler kimlik doğrulaması yapamaz.|  
|protectionScenario|Bu numaralandırma, ilke tarafından zorlanan koruma senaryosunu belirtir.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok|Aktarım sırasında iletiler güvenli değildir.|  
|Temel|Temel kimlik doğrulamasını belirtir.|  
|Bilgisi|Özet kimlik doğrulamasını belirtir.|  
|NT|Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.|  
|Windows|Windows tümleşik kimlik doğrulamasını belirtir.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok|-İletiler aktarım sırasında güvenli değildir.|  
|Temel|RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan temel kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.|  
|Bilgisi|RFC 2617 – HTTP kimlik doğrulaması ile tanımlanan Özet kimlik doğrulamasını belirtir: temel ve Özet kimlik doğrulaması.|  
|NT|Mümkünse NTLM kimlik doğrulamasını belirtir ve Windows kimlik doğrulaması başarısız olursa.|  
|Windows|Windows tümleşik kimlik doğrulamasını belirtir.|  
|Sertifika|Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir. Bu seçenek yalnızca `Mode` üst `security` öğenin özniteliği Transport olarak ayarlandıysa ve yalnızca transportcredentialolarak ayarlandıysa işe yarar.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|İçin güvenlik yeteneklerini tanımlar [\<basicHttpBinding>](basichttpbinding.md) .|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, temel bağlama ile SSL Aktarım güvenliği kullanımını gösterir. Varsayılan olarak, temel bağlama HTTP iletişimini destekler.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
