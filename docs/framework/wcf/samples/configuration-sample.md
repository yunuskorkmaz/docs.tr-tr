---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 6d84085d06da117ebf13fa4bb714513aacc3abd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594731"
---
# <a name="configuration-sample"></a>Yapılandırma Örneği
Bu örnek, bir hizmetin bulunabilir olması için bir yapılandırma dosyası kullanımını gösterir.  
  
> [!NOTE]
> Bu örnek, yapılandırmada bulma işlemini uygular. Kodda bulmayı uygulayan bir örnek için bkz. [temel](basic-sample.md).  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Hizmet yapılandırması  
 Bu örnekteki yapılandırma dosyası iki özelliği göstermektedir:  
  
- Hizmetin bir standart üzerinde bulunabilir hale getirilmesi <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .  
  
- Hizmetin uygulama uç noktası için bulma ile ilgili bilgileri ayarlama ve standart uç noktada bazı bulma ile ilgili ayarları ayarlama.  
  
 Bulmayı etkinleştirmek için, hizmet için uygulama yapılandırma dosyasında birkaç değişiklik yapılmalıdır:  
  
- Bir bulma uç noktasının öğeye eklenmesi gerekir `<service>` . Bu, standart bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktasıdır. Bu, çalışma zamanının bulma hizmetiyle ilişkilendiğini belirten bir sistem uç noktasıdır. Bulma hizmeti bu uç noktada iletileri dinler.  
  
- `<serviceDiscovery>`Bölüme bir davranış eklenir `<serviceBehaviors>` . Bu, hizmetin çalışma zamanında keşfedilmesini sağlar ve daha önce bulma ve iletileri dinlemek için bahsedilen bulma uç noktasını `Probe` kullanır `Resolve` . Bu iki eklemele, hizmet belirtilen bulma uç noktasında bulunabilir.  
  
 Aşağıdaki yapılandırma kod parçacığında, bir uygulama uç noktasına ve tanımlı bulma uç noktasına sahip bir hizmet gösterilmektedir:  
  
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
  
 Duyuruların avantajlarından yararlanmak için bir duyuru uç noktası eklemeniz gerekir. Bunu yapmak için, yapılandırma dosyasını aşağıdaki kodda gösterildiği gibi değiştirin.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Bulma hizmeti davranışına bir duyuru uç noktası eklemek, hizmet için varsayılan bir duyuru istemcisi oluşturur. Bu, hizmetin sırasıyla açık ve kapalı olduğu durumlarda hizmetin çevrimiçi ve çevrimdışı duyuru göndermesini güvence altına alır.  
  
 Bu yapılandırma dosyası, ek davranışları değiştirerek yalnızca bu basit adımların ötesine geçer. Belirli uç noktaları kullanarak bulma ile ilgili bilgileri denetlemek mümkündür. Diğer bir deyişle, bir Kullanıcı bir uç noktanın keşfedilip edilmeyeceğini denetleyebilir ve Kullanıcı bu uç noktayı <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verilerini de işaretleyebilir. Bunu yapmak için, kullanıcının `behaviorConfiguration` uygulama uç noktasına bir özellik eklemesi gerekir. Bu durumda, aşağıdaki özellik uygulama uç noktasına eklenir.  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 Şimdi, davranış yapılandırma öğesi sayesinde, bulma ile ilgili öznitelikleri denetleyebilirsiniz. Bu durumda, uygulama uç noktasına iki kapsam eklenir.  
  
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
  
 Kapsamlar hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../feature-details/discovery-find-and-findcriteria.md).  
  
 Bulma uç noktasının belirli ayrıntılarını da denetleyebilirsiniz. Bu, aracılığıyla yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection> . Bu örnekte, kullanılan protokolün sürümü değiştirilmiştir ve `maxResponseDelay` Aşağıdaki kod örneğinde gösterildiği gibi bir özniteliği ekler.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Aşağıda, bu örnekte kullanılan tüm yapılandırma dosyası verilmiştir:  
  
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
 İstemcinin uygulama yapılandırma dosyasında, bir `standardEndpoint` türü `dynamicEndpoint` aşağıdaki yapılandırma parçacığında gösterildiği gibi bulmayı kullanmak için kullanılır.  
  
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
  
 Bir istemci bir kullanırken `dynamicEndpoint` , çalışma zamanı bulmayı otomatik olarak gerçekleştirir. Bulma sırasında, `discoveryClientSettings` kullanılacak bulma uç noktasının türünü belirten, bölümünde tanımlananlar gibi çeşitli ayarlar kullanılır:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Hizmetleri aramak için kullanılan bulma ölçütü:  
  
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
  
 Bu örnek, bu özelliği genişletir ve <xref:System.ServiceModel.Discovery.FindCriteria> istemcinin, bulma için kullanılan bazı özellikler özelliklerinin yanı sıra istemci tarafından kullanılan özellikleri değiştirir `updDiscoveryEndpoint` . , <xref:System.ServiceModel.Discovery.FindCriteria> Bir kapsamı ve belirli bir `scopeMatchBy` algoritmayı ve özel sonlandırma ölçütlerini kullanacak şekilde değiştirilir. Ayrıca, örnek ayrıca, bir istemcinin iletileri kullanarak nasıl XML öğeleri gönderebilirim gösterilmektedir `Probe` . Son olarak, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki yapılandırma dosyasında gösterildiği gibi, kullanılan protokol sürümü ve UDP 'ye özgü ayarlar gibi bazı değişiklikler yapılmıştır.  
  
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
  
 Örnekte kullanılan tüm istemci yapılandırması aşağıda verilmiştir.  
  
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
</configuration>
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md). Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. Çözümü derleyin.  
  
3. Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.  
  
4. İstemci yürütülebilir dosyasını çalıştırın. İstemcinin hizmeti bulabileceğini unutmayın.  
