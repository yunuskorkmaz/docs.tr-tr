---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 6273b6b0f84887f031539581fbf664b9dbf50300
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579465"
---
# <a name="configuration-sample"></a>Yapılandırma Örneği
Bu örnek, bir hizmet bulunabilir hale getirmek için bir yapılandırma dosyası kullanımını gösterir.  
  
> [!NOTE]
>  Bu örnek yapılandırmada bulma uygular. Bulma uygulayan kodda bir örnek için bkz. [temel](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Hizmet yapılandırması  
 Bu örnek yapılandırma dosyasında iki özelliklerini gösterir:  
  
-   Hizmetin bir standart bulunabilir olmasını sağlama <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Bulma ile ilgili bilgi hizmetin uygulama uç noktası ve bazı standart uç noktasında bulma ile ilgili ayarlar ayarlama için ayarlanıyor.  
  
 Bulmayı etkinleştirmek için birkaç değişiklik hizmeti için uygulama yapılandırma dosyasında yapılması gerekir:  
  
-   Bulma uç noktası eklenmelidir `<service>` öğesi. Bu bir standarttır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası. Bu çalışma zamanı bulma hizmeti ile ilişkilendiren bir sistem uç noktadır. Bu uç nokta ileti bulma hizmeti dinler.  
  
-   A `<serviceDiscovery>` davranışı eklenir `<serviceBehaviors>` bölümü. Bu çalışma zamanında bulunacak hizmetini etkinleştirir ve bulma için dinlemek için daha önce bahsedilen bulma uç noktası kullanan `Probe` ve `Resolve` iletileri. Bu iki eklemeleriyle, hizmet belirtilen bulma uç noktada bulunabilir.  
  
 Yapılandırma aşağıdaki kod parçacığında, bir uygulama uç noktası ve tanımlanmış bir bulma uç noktası ile bir hizmeti gösterir:  
  
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
  
 Duyuruları yararlanmak için bir duyuru uç noktası eklemeniz gerekir. Bunu yapmak için aşağıdaki kodda gösterildiği gibi yapılandırma dosyasını değiştirme.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Bir duyuru uç nokta ekleme için bulma hizmet davranışı, hizmet için varsayılan bir duyuru istemcisi oluşturur. Bu hizmeti açık ve kapalı sırasıyla hizmet çevrimiçi ve çevrimdışı duyuru gönderir güvence altına alır.  
  
 Bu yapılandırma dosyası, yalnızca basit adımları ek davranışları değiştirerek gider. Özel uç noktaları kullanarak bulma ile ilgili bilgileri denetlemek mümkündür. Diğer bir deyişle, bir kullanıcı bir uç nokta bulunan ve kullanıcı uç noktasına da işaretleyebilirsiniz denetleyebilirsiniz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verileri. Bunu yapmak için kullanıcıyı eklemeniz gerekir bir `behaviorConfiguration` özelliğini uygulama uç noktası. Bu durumda, aşağıdaki özellik için uygulama uç noktası eklenir.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Şimdi, davranış yapılandırma öğesi bulma ile ilgili özniteliklere denetleyebilirsiniz. Bu durumda, iki kapsam için bir uygulama uç noktası eklenir.  
  
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
  
 Kapsamlar hakkında daha fazla bilgi için bkz: [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Belirli bir bulma uç noktası ayrıntılarını ayrıca denetleyebilirsiniz. Bu yoluyla yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. Bu örnekte, ekleme yanı sıra kullanılan protokol sürümünü değiştiren bir `maxResponseDelay` öznitelik aşağıdaki kod örneğinde gösterildiği gibi.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Bu örnekte kullanılan tam yapılandırma dosyası verilmiştir:  
  
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
 İstemci, uygulama yapılandırma dosyasında bir `standardEndpoint` türü `dynamicEndpoint` bulma aşağıdaki yapılandırma kod parçacığında gösterildiği gibi yararlanmak için kullanılır.  
  
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
  
 Bir istemci kullanarak ne zaman bir `dynamicEndpoint`, çalışma zamanı otomatik olarak bulma işlemini gerçekleştirir. İçinde tanımlanan gibi bulma sırasında kullanılan çeşitli ayarları `discoveryClientSettings` bölümünde, kullanmak için bulma uç noktası türünü belirtir:  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 Hizmetleri aramak için kullanılan Bulma ölçütü:  
  
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
  
 Bu örnek, bu özellik genişleten ve değiştiren <xref:System.ServiceModel.Discovery.FindCriteria> istemci yanı sıra tarafından standart bazı özellikler kullanılan `updDiscoveryEndpoint` bulma için kullanılır. <xref:System.ServiceModel.Discovery.FindCriteria> Kapsam ve belirli bir değişiklik `scopeMatchBy` özel sonlandırma ölçütünü yanı sıra algoritması. Ayrıca, örnek aynı zamanda bir istemci kullanarak XML öğeleri nasıl gönderebilir gösterir `Probe` iletileri. Son olarak, bazı değişiklikler yapılır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>kullanılan protokol sürümünü ve UDP özgü ayarları aşağıdaki yapılandırma dosyasında gösterildiği gibi.  
  
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
  
 Örnekte kullanılan tam istemci yapılandırması aşağıda verilmiştir.  
  
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
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir. Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Yürütülebilir hizmet oluşturma dizinden çalıştırın.  
  
4.  İstemci yürütülebilir çalıştırın. İstemci hizmetini bulun mümkün olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
