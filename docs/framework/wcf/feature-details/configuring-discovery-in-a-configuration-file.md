---
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 59eaecb7e34b9105bc694f444d98c13c036d552f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597559"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
Bulma sırasında kullanılan dört ana yapılandırma ayarı grubu vardır. Bu konu, her birini kısaca betimleyen ve bunların nasıl yapılandırılacağını gösteren örnekler gösterecektir. Her bölüm için, her alanla ilgili daha ayrıntılı bir belge bağlantısı olacaktır.  
  
## <a name="behavior-configuration"></a>Davranış yapılandırması  
 Bulma hizmeti davranışlarını ve uç nokta davranışlarını kullanır. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Davranış, bir hizmetin tüm uç noktaları için bulmayı sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.  Aşağıdaki örnek, ' nin nasıl ekleneceğini <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç noktasının nasıl ekleneceğini gösterir.  
  
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
</behaviors>  
```  
  
 Davranışı belirttikten sonra, `service` Aşağıdaki örnekte gösterildiği gibi bir <> öğesinden başvuru yapın.  
  
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
    </services>  
</system.serviceModel>  
```  
  
 Bir hizmetin bulunabilir olması için, bir bulma uç noktası da eklemeniz gerekir, yukarıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Standart bir uç nokta ekler.  
  
 Duyuru uç noktaları eklediğinizde, `services` Aşağıdaki örnekte gösterildiği gibi <> öğesine bir duyuru dinleyicisi hizmeti de eklemeniz gerekir.  
  
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
</services>
```  
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Davranış, belirli bir uç noktanın bulunmasını etkinleştirmek veya devre dışı bırakmak için kullanılır.  Aşağıdaki örnek, bir hizmeti bulma etkin ve diğeri de bulma devre dışı olan iki uygulama uç noktası ile yapılandırır. Her bitiş noktası için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış eklenir.  
  
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
</system.serviceModel>  
```  
  
 Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış, hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Bu davranış, istemcilerin Hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir. Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.  
  
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
  
 Hakkında daha fazla bilgi <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> için <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz. [WCF bulmaya genel bakış](wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Bağlama öğesi yapılandırması  
 Bağlama öğesi yapılandırması, istemci tarafında en ilginç bir öğedir. Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırma kullanabilirsiniz.  Aşağıdaki örnek, kanalla birlikte özel bir bağlama oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> ve bir tür ve kapsam içeren bulma ölçütünü belirtir. Ayrıca, ve özellikleri için değerleri belirtir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> .  
  
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
   </customBinding>
</bindings>  
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
  
 Bulma ölçütü hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](discovery-find-and-findcriteria.md). Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz. [WCF bulgu genel bakış](wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standart uç nokta yapılandırması  
 Standart uç noktalar bir veya daha fazla Özellik (adres, bağlama veya sözleşme) veya değiştirebir veya daha fazla özellik değeri için varsayılan değerlere sahip önceden tanımlanmış uç noktalardır. .NET 4, 3 bulma ile ilgili standart uç noktaları ile birlikte gelir: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> , ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> .  , <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> BIR UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç noktasıdır. , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> BIR UDP bağlaması üzerinden duyuru iletileri gönderecek şekilde önceden yapılandırılmış standart bir uç noktasıdır. , <xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma kullanan standart bir uç noktadır ve bulunan bir hizmetin uç nokta adresini çalışma zamanında dinamik olarak bulur.  Standart bağlamalar, `endpoint` eklenecek standart uç nokta türünü belirtilen tür özniteliğini içeren bir <> öğesiyle belirtilir. Aşağıdaki örnek, ve ' nin nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .  
  
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
  
 Standart uç noktalar bir <`standardEndpoints`> öğesinde yapılandırılır. Aşağıdaki örnek, ve ' nin nasıl yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .  
  
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
</standardEndpoints>
```  
  
 Standart uç nokta yapılandırmasını ekledikten sonra, `endpoint` Aşağıdaki örnekte gösterildiği gibi her bir uç nokta için <> öğesindeki yapılandırmaya başvurun.  
  
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
  
 Bulma sırasında kullanılan diğer standart uç noktaların aksine, için bir bağlama ve sözleşme belirtirsiniz <xref:System.ServiceModel.Discovery.DynamicEndpoint> . Aşağıdaki örnek, ' nin nasıl ekleneceğini ve yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.DynamicEndpoint> .  
  
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
