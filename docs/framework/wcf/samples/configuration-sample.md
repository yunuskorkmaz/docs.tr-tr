---
title: "Yapılandırma Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3c73fd8501d5209a87564caa810997476357f3e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-sample"></a>Yapılandırma Örneği
Bu örnek, bir hizmet bulunabilir duruma getirmek için bir yapılandırma dosyası kullanımını göstermektedir.  
  
> [!NOTE]
>  Bu örnek bulma yapılandırmasını uygular. Kodda bulma uygulayan bir örnek için bkz: [temel](../../../../docs/framework/wcf/samples/basic-sample.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>Hizmet yapılandırması  
 Bu örnek yapılandırma dosyasında iki özellik gösterilmektedir:  
  
-   Hizmeti bir standart bulunabilir olmasını <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
-   Bulma ile ilgili bilgiler hizmetin uygulama uç noktası ve bazı standart uç bulma ile ilgili ayarları ayarlamak için ayarlama.  
  
 Bulmayı etkinleştirmek için birkaç değişiklik hizmeti için uygulama yapılandırma dosyasında yapılması gerekir:  
  
-   Bir bulma uç noktası eklenmelidir `<service>` öğesi. Bu bir standarttır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası. Bu çalışma zamanı bulma hizmetiyle ilişkilendirir bir sistem uç noktadır. Bu uç noktaya iletileri bulma hizmeti dinler.  
  
-   A `<serviceDiscovery>` davranışı eklenir `<serviceBehaviors>` bölümü. Bu çalışma zamanında bulunacak hizmetini etkinleştirir ve bulma için dinlemek için daha önce bahsedilen bulma uç nokta kullanır `Probe` ve `Resolve` iletileri. Bu iki eklemeleri ile belirtilen bulma uç noktada bulunabilirlik hizmetidir.  
  
 Aşağıdaki yapılandırma parçacığını olan bir hizmeti uygulama uç noktası ve tanımlı bir bulma uç noktası gösterilmektedir:  
  
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
  
 Duyurular yararlanmak için bir duyuru uç noktası eklemeniz gerekir. Bunu yapmak için aşağıdaki kodda gösterildiği gibi yapılandırma dosyasını değiştirin.  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 Bulma hizmet davranışı için bir duyuru uç noktası ekleniyor varsayılan duyuru İstemcisi hizmeti oluşturur. Bu hizmeti açılır ve sırasıyla kapalı hizmeti çevrimiçi ve çevrimdışı duyuru gönderir güvence altına alır.  
  
 Bu yapılandırma dosyası, yalnızca basit adımları ek davranışları değiştirerek gider. Özel uç noktaları kullanarak bulma ile ilgili bilgiler denetlemek mümkündür. Diğer bir deyişle, bir kullanıcı bir uç nokta bulunan ve kullanıcı da bu bitiş noktası ile işaretleyebilirsiniz olup olmadığını kontrol edebilirsiniz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verileri. Bunu yapmak için kullanıcının eklemelisiniz bir `behaviorConfiguration` uygulama uç özelliği. Bu durumda, aşağıdaki özellik uygulama uç noktasına eklenir.  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 Şimdi, davranışını yapılandırma öğesi bulma ile ilgili öznitelikleri kontrol edebilirsiniz. Bu durumda, iki kapsamları uygulama uç noktasına eklenir.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bkz: kapsamları, [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).  
  
 Ayrıca belirli bulma uç nokta ayrıntılarını kontrol edebilirsiniz. Bu yoluyla yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection>. Bu örnekte, ekleme yanı sıra kullanılan protokol sürümünü değiştiren bir `maxResponseDelay` özniteliği aşağıdaki kod örneğinde gösterildiği gibi.  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 Bu örnekte kullanılan tam yapılandırma dosyasını verilmiştir:  
  
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
 İstemci uygulama yapılandırma dosyasında bir `standardEndpoint` türü `dynamicEndpoint` aşağıdaki yapılandırma parçacığında gösterildiği gibi bulma faydalanmak için kullanılır.  
  
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
  
 Bir istemci kullanırken bir `dynamicEndpoint`, çalışma zamanı bulma otomatik olarak gerçekleştirir. İçinde tanımlanan gibi bulma sırasında kullanılan çeşitli ayarları `discoveryClientSettings` kullanmak için keşif arka uç noktası türünü belirtir. Bölüm:  
  
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
  
 Bu örnek, bu özellik genişletir ve değiştirir <xref:System.ServiceModel.Discovery.FindCriteria> istemci yanı sıra tarafından bazı standart özelliklerini kullanılan `updDiscoveryEndpoint` bulma için kullanılır. <xref:System.ServiceModel.Discovery.FindCriteria> Bir kapsam ve belirli bir değişiklik `scopeMatchBy` özel sonlandırma ölçütleri yanı sıra algoritması. Ayrıca, örnek aynı zamanda bir istemci XML öğeleri kullanılarak nasıl gönderebilir gösterir `Probe` iletileri. Son olarak, bazı değişiklikler yapılması <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>kullanılan protokol sürümünü ve aşağıdaki yapılandırma dosyasında gösterildiği gibi UDP özgü ayarları gibi.  
  
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
  
 Aşağıdaki örnekte kullanılan tam istemci yapılandırmadır.  
  
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
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir. Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Hizmeti yürütülebilir dosyası derleme dizininden çalıştırın.  
  
4.  İstemci yürütülebilir çalıştırın. İstemci hizmetini bulun mümkün olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
