---
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 0ad44d0ad1f0d67d84cc42f6b9938d096c245417
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834756"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
Bulma sırasında kullanılan dört ana yapılandırma ayarı grubu vardır. Bu konu, her birini kısaca betimleyen ve bunların nasıl yapılandırılacağını gösteren örnekler gösterecektir. Her bölüm için, her alanla ilgili daha ayrıntılı bir belge bağlantısı olacaktır.  
  
## <a name="behavior-configuration"></a>Davranış yapılandırması  
 Bulma hizmeti davranışlarını ve uç nokta davranışlarını kullanır. @No__t-0 davranışı, bir hizmetin tüm uç noktaları için bulmayı sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.  Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ' nın nasıl ekleneceğini ve bir duyuru uç noktasının nasıl yapılacağını gösterir.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
```  
  
 Davranışı belirttikten sonra, aşağıdaki örnekte gösterildiği gibi bir < `service` > öğesinden başvuru yapın.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </service>  
```  
  
 Bir hizmetin bulunabilir olması için, bir bulma uç noktası da eklemeniz gerekir, yukarıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası ekler.  
  
 Duyuru uç noktaları eklediğinizde, aşağıdaki örnekte gösterildiği gibi < `services` > öğesine bir duyuru dinleyicisi hizmeti de eklemeniz gerekir.  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
```  
  
 @No__t-0 davranışı belirli bir uç noktanın bulunmasını etkinleştirmek veya devre dışı bırakmak için kullanılır.  Aşağıdaki örnek, bir hizmeti bulma etkin ve diğeri de bulma devre dışı olan iki uygulama uç noktası ile yapılandırır. Her bitiş noktası için <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"   
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
```  
  
 @No__t-0 davranışı, hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 @No__t-0 davranışı, istemcilerin Hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir. Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 @No__t-0 ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> hakkında daha fazla bilgi için bkz. [WCF bulmaya genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Bağlama öğesi yapılandırması  
 Bağlama öğesi yapılandırması, istemci tarafında en ilginç bir öğedir. Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırma kullanabilirsiniz.  Aşağıdaki örnek <xref:System.ServiceModel.Discovery.DiscoveryClient> kanalına sahip özel bir bağlama oluşturur ve bir tür ve kapsam içeren bulma ölçütünü belirtir. Ayrıca, <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri için değerler belirtir.  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>              
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
        </binding>  
```  
  
 Bu özel bağlama yapılandırmasına bir istemci uç noktası tarafından başvurulmalıdır:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Bulma ölçütü hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz. [WCF bulgu genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standart uç nokta yapılandırması  
 Standart uç noktalar bir veya daha fazla Özellik (adres, bağlama veya sözleşme) veya değiştirebir veya daha fazla özellik değeri için varsayılan değerlere sahip önceden tanımlanmış uç noktalardır. .NET 4, 3 bulma ile ilgili standart uç noktaları ile birlikte gelir: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  @No__t-0, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç noktadır. @No__t-0, bir UDP bağlaması üzerinden duyuru iletileri gönderecek şekilde önceden yapılandırılmış standart bir uç noktadır. @No__t-0, çalışma zamanında dinamik olarak bulunan bir hizmetin uç nokta adresini bulmak için bulma kullanan standart bir uç noktadır.  Standart bağlamalar, eklenecek standart uç nokta türünü belirtilen tür özniteliğini içeren bir < `endpoint` > öğesiyle belirtilir. Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ' in nasıl ekleneceğini gösterir.  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 Standart uç noktalar < `standardEndpoints` > öğesinde yapılandırılır. Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ' in nasıl yapılandırılacağını gösterir.  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint   
            name="udpAnnouncementEndpointSettings"   
            multicastAddress="soap.udp://239.255.255.250:3703"    
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>  
```  
  
 Standart uç nokta yapılandırmasını ekledikten sonra, aşağıdaki örnekte gösterildiği gibi her bir uç nokta için < `endpoint` > öğesinde yapılandırmaya başvurun.  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->          
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 Bulma sırasında kullanılan diğer standart uç noktaların aksine, <xref:System.ServiceModel.Discovery.DynamicEndpoint> için bir bağlama ve sözleşme belirtirsiniz. Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DynamicEndpoint> ' ın nasıl ekleneceğini ve yapılandırılacağını gösterir.  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>   
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>          
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 Standart uç noktalar hakkında daha fazla bilgi için bkz. [standart uç noktalar](standard-endpoints.md).
