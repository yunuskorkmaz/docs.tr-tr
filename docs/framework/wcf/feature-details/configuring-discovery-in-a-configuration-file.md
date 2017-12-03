---
title: "Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42f86762bf40f5c8358b8772548c082844eae1ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
Dört ana gruplarını bulmayı kullanılan yapılandırma ayarlarını vardır. Bu konuda kısaca açıklanmaktadır ve bunların nasıl yapılandırılacağı örnekleri gösterilmektedir. Her bölüm aşağıdaki her bir alan hakkında daha fazla ayrıntılı belgeler için bir bağlantı olacaktır.  
  
## <a name="behavior-configuration"></a>Davranışını yapılandırma  
 Hizmet davranışları ve uç nokta davranışları bulma kullanır. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Davranışı bulma bir hizmetin bitiş noktalarının tümü için etkinleştirir ve duyuru uç noktaları belirtmenize olanak tanır.  Aşağıdaki örnekte nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç nokta belirtin.  
  
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
  
 Davranış belirttiğinizde, ondan başvuran bir <`service`> Aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
  
 Yukarıdaki örnekte bir bulma uç noktası da eklemelisiniz bulunabilir olması bir hizmet için sırayla ekler bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası.  
  
 Duyuru uç noktaları eklerken bir duyuru dinleme hizmeti de eklemeniz gerekir <`services`> Aşağıdaki örnekte gösterildiği gibi öğesi.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı etkinleştirmek veya belirli bir uç bulmayı devre dışı bırakmak için kullanılır.  Aşağıdaki örnekte, iki uygulama uç noktaları olan bir hizmeti, etkin bulma ile diğeri devre dışı bulma ile yapılandırır. Her uç noktası için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranış da hizmet tarafından döndürülen uç noktası meta verileri için özel meta verileri eklemek için kullanılabilir. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranış da kapsamlar ve Hizmetleri için aranacak istemcileri kullanmak türleri eklemek için kullanılabilir. Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunu gösterilmektedir.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Bağlama öğesi yapılandırma  
 Öğesi yapılandırma bağlama istemci tarafında en ilginç olacaktır. Yapılandırma Hizmetleri bir WCF istemci uygulamasından bulmak için kullanılan Bul ölçütlerini belirtmek için kullanabilirsiniz.  Aşağıdaki örnek ile özel bağlama oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> kanal ve türüne ve kapsamına içerir Bul ölçütlerini belirtir. Ayrıca için değerleri belirtir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri.  
  
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
  
 Bu özel bağlama yapılandırma istemci uç noktası tarafından başvurulan gerekir:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bul ölçütlerini görmek [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]bulma ve bağlama öğeleri bakın, [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standart uç nokta yapılandırması  
 Standart uç noktaları, bir veya daha fazla özellikleri (adresi, bağlama veya sözleşme) veya değiştiremezsiniz bir veya daha fazla özellik değerleri için varsayılan değerleri olan önceden tanımlanmış noktalarıdır. .NET 4, 3 ile birlikte gelen bulma ilgili standart uç noktaları: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Olduğu için bulma işlemlerini UDP çok noktaya yayın önceden yapılandırılmış standart bir uç nokta bağlama. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> UDP bağlama üzerinden duyuru iletileri göndermek üzere önceden yapılandırılmıştır standart bir uç noktası. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma bulunan hizmet uç noktası adresi çalışma zamanında dinamik olarak bulmak için kullandığı standart bir uç noktası.  Standart bağlamaları ile belirtilen bir <`endpoint`> öğesi eklemek için standart uç nokta türü belirtilen tür özniteliği içeriyor. Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standart uç noktaları olarak yapılandırılmış olan bir <`standardEndpoints`> öğesi. Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standart uç nokta yapılandırması ekledikten sonra yapılandırmada başvuru <`endpoint`> öğesi aşağıdaki örnekte gösterildiği gibi her bitiş noktasıyla ilgili.  
  
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
  
 Bulmayı kullanılan diğer standart uç noktaları, farklı bir bağlama belirtin ve için sözleşme <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Aşağıdaki örnek eklemek ve yapılandırmak nasıl gösterir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Standart uç noktaları görmek [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
