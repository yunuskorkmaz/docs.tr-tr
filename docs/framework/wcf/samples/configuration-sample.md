---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 5ac72db1fce0862381cd614499b5db4b9d95b2d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183910"
---
# <a name="configuration-sample"></a>Yapılandırma Örneği
Bu örnek, bir hizmeti keşfedilebilir hale getirmek için bir yapılandırma dosyasının kullanımını gösterir.  
  
> [!NOTE]
> Bu örnek yapılandırmada bulma uygular. Kodda bulma uygulayan bir örnek için [Temel'e](../../../../docs/framework/wcf/samples/basic-sample.md)bakın.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Hizmet Yapılandırması  
 Bu örnekteki yapılandırma dosyası iki özellik gösterir:  
  
- Hizmetin standart <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>üzerinden keşfedilebilir hale getirilmesi.  
  
- Hizmetin uygulama bitiş noktası için keşifle ilgili bilgileri ayarlama ve standart bitiş noktasında keşifle ilgili ayarların bazılarını ayarlama.  
  
 Keşfi etkinleştirmek için, hizmetin uygulama yapılandırma dosyasında birkaç değişiklik yapılması gerekir:  
  
- `<service>` Öğeye bir bulma bitiş noktası eklenmelidir. Bu standart <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> bir bitiş noktasıdır. Bu, çalışma zamanının bulma hizmetiyle ilişkilendirdiyi gösteren bir sistem bitiş noktasıdır. Bulma hizmeti bu uç noktadaki iletileri dinler.  
  
- `<serviceBehaviors>` Bölüme bir `<serviceDiscovery>` davranış eklenir. Bu, hizmetin çalışma zamanında bulunmasını sağlar ve keşif `Probe` ve `Resolve` iletileri dinlemek için daha önce bahsedilen keşif bitiş noktasını kullanır. Bu iki eklemeyle, hizmet belirtilen bulma bitiş noktasında keşfedilebilir.  
  
 Aşağıdaki config snippet, uygulama bitiş noktası ve bir bulma bitiş noktası tanımlanan bir hizmeti gösterir:  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"
                    kind="udpDiscoveryEndpoint"
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 Duyurulardan yararlanmak için bir duyuru bitiş noktası eklemeniz gerekir. Bunu yapmak için, yapılandırma dosyasını aşağıdaki kodda gösterildiği şekilde değiştirin.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Bulma hizmeti davranışına bir duyuru bitiş noktası eklemek, hizmet için varsayılan bir duyuru istemcisi oluşturur. Bu, hizmet sırasıyla açılıp kapandığında hizmetin çevrimiçi ve çevrimdışı bir duyuru göndereceğini garanti eder.  
  
 Bu yapılandırma dosyası, ek davranışları değiştirerek bu basit adımların ötesine geçer. Belirli uç noktaları kullanarak keşifle ilgili bilgileri denetlemek mümkündür. Diğer bir nokta, bir uç noktanın bulunup bulunamayacağını denetleyebilir ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> kullanıcı da bu bitiş noktasını ve özel XML meta verilerini işaretleyebilir. Bunu yapmak için, kullanıcı `behaviorConfiguration` uygulama bitiş noktasına bir özellik eklemeniz gerekir. Bu durumda, uygulama bitiş noktasına aşağıdaki özellik eklenir.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Şimdi, davranış yapılandırma öğesi aracılığıyla, keşifle ilgili öznitelikleri denetleyebilirsiniz. Bu durumda, uygulama bitiş noktasına iki kapsam eklenir.  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
```  
  
 Kapsamlar hakkında daha fazla bilgi [için, Bulma Ve Bulma Ölçütleri'ne](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)bakın.  
  
 Ayrıca, bulma bitiş noktasının belirli ayrıntılarını da denetleyebilirsiniz. Bu yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. Bu örnekte, kullanılan protokolün sürümü, aşağıdaki kod `maxResponseDelay` örneğinde gösterildiği gibi bir öznitelik eklemenin yanı sıra değiştirilir.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Bu örnekte kullanılan yapılandırma dosyasının tamamı aşağıda verilmiştir:  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a>İstemci Yapılandırması  
 İstemci için uygulama yapılandırma `standardEndpoint` dosyasında, aşağıdaki config snippet'te gösterildiği gibi keşfi kullanmak için bir tür `dynamicEndpoint` kullanılır.  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 İstemci bir `dynamicEndpoint`, çalışma zamanı otomatik olarak keşif gerçekleştirir kullanır. Keşif sırasında, kullanılacak keşif bitiş noktasının `discoveryClientSettings` türünü belirten bölümde tanımlananlar gibi çeşitli ayarlar kullanılır:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Hizmetleri aramak için kullanılan bul ölçütleri:  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 Bu örnek bu özelliği genişletir <xref:System.ServiceModel.Discovery.FindCriteria> ve istemci tarafından kullanılan yanı sıra keşif `updDiscoveryEndpoint` için kullanılan standardın bazı özelliklerini değiştirir. Bir <xref:System.ServiceModel.Discovery.FindCriteria> kapsam ve belirli `scopeMatchBy` bir algoritmanın yanı sıra özel sonlandırma ölçütlerini kullanmak üzere değiştirilir. Ayrıca, örnek, iletileri kullanarak `Probe` istemcinin XML öğelerini nasıl gönderebileceğini de gösterir. Son olarak, aşağıdaki yapılandırma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>dosyasında gösterildiği gibi kullanılan protokolün sürümü ve UDP'ye özgü ayarlar gibi bazı değişiklikler yapılır.  
  
```xml  
<udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
```  
  
 Aşağıda örnekte kullanılan tam istemci yapılandırmasıdır.  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Bu örnek, HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ALA'ları eklenmelidir. Daha fazla bilgi için [http ve HTTPS yapılandırma](../feature-details/configuring-http-and-https.md)bölümüne bakın. Aşağıdaki komutu yükseltilmiş bir ayrıcalıkta yürütmek uygun ALA'ları eklemelidir. Komut olduğu gibi çalışmıyorsa, Etki Alanı nızı ve Kullanıcı Adınızı aşağıdaki bağımsız değişkenler için değiştirmek isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Çözümü derleyin.  
  
3. Yapı dizininden çalıştırılabilen hizmeti çalıştırın.  
  
4. İstemciyi çalıştırılabilir çalıştırın. İstemcinin hizmeti bulabilmesi gerektiğini unutmayın.  
