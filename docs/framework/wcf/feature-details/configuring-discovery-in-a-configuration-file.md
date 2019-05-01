---
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: c282767e686ac8a6382268aee8b45eb2d1297f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857525"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
Dört büyük Grup bulma içinde kullanılan yapılandırma ayarları vardır. Bu konu, kısaca açıklanmaktadır ve nasıl yapılandırılacakları örnekleri gösterir. Aşağıdaki her bölümde, her alan hakkında daha fazla ayrıntılı belgeler için bir bağlantı olacaktır.  
  
## <a name="behavior-configuration"></a>Davranışını yapılandırma  
 Hizmet davranışları ve uç nokta davranışları bulma kullanır. <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Davranış tüm bir hizmet uç noktaları için bulma olanağı sağlar ve duyuru uç noktaları belirtmenizi sağlar.  Aşağıdaki örnek nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç noktasını belirtin.  
  
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
  
 Davranış belirttiğinizde, ondan başvuran bir <`service`> Aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 Yukarıdaki örnekte bir bulma uç noktası eklemeniz de bulunabilir olması için bir hizmet için sırada ekler bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası.  
  
 Duyuru uç noktaları eklerken bir duyuru dinleyici hizmetine de eklemeniz gerekir <`services`> Aşağıdaki örnekte gösterildiği gibi bir öğe.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı etkinleştirmek veya belirli bir uç noktaya bulunmasını devre dışı bırakmak için kullanılır.  Aşağıdaki örnek, iki uygulama uç noktası ile bir hizmeti, etkin bulma ile diğeri devre dışı keşif ile yapılandırır. Her uç nokta için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı da özel meta verileri, hizmet tarafından döndürülen meta veri uç noktası eklemek için kullanılabilir. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı da kapsamları ve istemcilerin aramak için hizmetler için kullandığınız türleri eklemek için kullanılabilir. Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.  
  
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
  
 Hakkında daha fazla bilgi için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).  
  
## <a name="binding-element-configuration"></a>Bağlama öğesi yapılandırması  
 Bağlama öğesi yapılandırması istemci tarafında en ilginç. Yapılandırma, bir WCF istemci uygulama hizmetlerini keşfetmek için bulma ölçütlerini belirtmek için kullanabilirsiniz.  Aşağıdaki örnek, özel bir bağlama ile oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> kanal ve türüne ve kapsamına içeren Bulma ölçütü belirtir. Buna ek olarak, için değerler belirten <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri.  
  
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
  
 Bu özel bağlama yapılandırma, bir istemci uç noktası tarafından başvurulması gerekir:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 Bulma ölçütleri hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md). Bulma ve bağlama öğeleri bkz hakkında daha fazla bilgi için [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standart uç nokta yapılandırması  
 Standart uç noktaları, bir veya daha fazla özellikler (adresi, bağlama veya sözleşme) ve değiştirilemez bir veya daha fazla özellik değerleri için varsayılan değerlere sahip önceden tanımlı uç noktalardır. .NET 4, 3 ile birlikte gelen bulma ilgili standart uç noktaları: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Olduğu için bulma işlemlerini bir UDP çok noktaya yayın önceden yapılandırılmış bir standart uç nokta bağlama. <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> UDP bağlama üzerinden Duyurunun ileti göndermek için önceden yapılandırılmış bir standart uç noktadır. <xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma, bulunan bir Hizmeti uç nokta adresini çalışma zamanında dinamik olarak bulmak için kullandığı standart bir uç noktadır.  Standart bağlamaları ile belirtilen bir <`endpoint`> eklemek için standart uç nokta türü belirtilen tür öznitelik içeren öğe. Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standart uç noktaları yapılandırılmış bir <`standardEndpoints`> öğesi. Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standart uç nokta yapılandırması ekledikten sonra yapılandırmayı başvuru <`endpoint`> Aşağıdaki örnekte gösterildiği gibi her uç nokta için öğesi.  
  
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
  
 Bulma içinde kullanılan diğer standart uç noktaları, farklı bir bağlama belirtin ve için sözleşme <xref:System.ServiceModel.Discovery.DynamicEndpoint>. Aşağıdaki örnek, ekleme ve yapılandırma işlemi gösterilmektedir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Standart uç noktaları hakkında daha fazla bilgi için bkz: [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
