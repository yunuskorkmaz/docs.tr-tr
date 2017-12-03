---
title: "&lt;basicHttpBinding&gt; &lt;taşıma&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c08e4c8b1008fa6e2625cdb9cd22672daf691a4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a>&lt;basicHttpBinding&gt; &lt;taşıma&gt;
HTTP taşıma için kimlik doğrulama parametrelerini denetleyen özellikler tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<basicHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
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
|clientCredentialType|-HTTP kimlik doğrulaması kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir.  Varsayılan, `None` değeridir. Bu öznitelik türünde <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-İstemci kimlik doğrulamasını bir proxy sunucu HTTP üzerinden kullanarak bir etki alanı içinde gerçekleştirirken kullanılacak kimlik bilgileri türünü belirtir. Bu öznitelik yalnızca uygun olduğunda olan `mode` üst öznitelik `security` öğesi `Transport` veya `TransportCredentialsOnly`. Bu öznitelik türünde <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|Bölge|HTTP kimlik doğrulama şeması tarafından Özet veya temel kimlik doğrulaması için kullanılan bölge belirten bir dize. Varsayılan boş bir dizedir.|  
|policyEnforcement|Bu numaralandırma ne zaman belirtir <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> zorunlu tutulmalıdır.<br /><br /> 1.  Hiçbir zaman – ilke hiçbir zaman zorlanır (genişletilmiş koruma devre dışı).<br />2.  Yalnızca istemci genişletilmiş koruma destekliyorsa WhenSupported – ilke uygulanır.<br />3.  Her zaman – ilke her zaman zorlanır. Genişletilmiş Koruma desteklemeyen istemcilerin kimliğini doğrulamak başarısız olur.|  
|protectionScenario|Bu numaralandırma ilke tarafından zorlanan koruma senaryosu belirtir.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|İleti aktarımı sırasında sağlanmaz.|  
|Temel|Temel kimlik doğrulaması belirtir.|  
|Özet|Özet kimlik doğrulaması belirtir.|  
|NTLM|NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.|  
|Windows|Windows tümleşik kimlik doğrulaması belirtir.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|-Aktarım sırasında iletileri güvenli değil.|  
|Temel|Temel kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.|  
|Özet|Özet kimlik doğrulaması RFC 2617 – HTTP kimlik doğrulaması tarafından tanımlandığı şekilde belirtir: temel ve Özet kimlik doğrulaması.|  
|NTLM|NTLM kimlik doğrulaması, mümkün olduğunda ve Windows kimlik doğrulaması başarısız olursa belirtir.|  
|Windows|Windows tümleşik kimlik doğrulaması belirtir.|  
|Sertifika|Bir sertifika kullanarak istemci kimlik doğrulaması gerçekleştirir. Bu seçenek yalnızca çalışır `Mode` üst öznitelik `security` öğesi taşıma için ayarlanır ve TransportCredentialOnly için ayarlarsanız çalışmaz.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Güvenlik özellikleri için tanımlar [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, temel bağlama ile SSL taşıma güvenliği kullanımını göstermektedir. Varsayılan olarak, temel bağlama HTTP iletişimi destekler.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
