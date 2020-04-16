---
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 934b04b51b9954cf943f57f33250951048e5671b
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464212"
---
# <a name="configuring-discovery-in-a-configuration-file"></a>Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
Keşifte kullanılan dört ana yapılandırma ayarı grubu vardır. Bu konu, her birini kısaca açıklar ve bunları nasıl yapılandıracağınıza ait örnekler gösterir. Her bölümü takip her alan hakkında daha derinlemesine belgeler için bir bağlantı olacaktır.  
  
## <a name="behavior-configuration"></a>Davranış Yapılandırması  
 Bulma, hizmet davranışları ve uç nokta davranışları kullanır. Davranış, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir hizmetin tüm uç noktalarının bulunmasını sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.  Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru bitiş noktasının nasıl ekleyeceğinive belirtin.  
  
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
  
 Davranışı belirttikten sonra, aşağıdaki örnekte gösterildiği gibi <`service`> öğesinden başvurun.  
  
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
  
 Bir hizmetin bulunabilmesi için, bir keşif bitiş noktası da eklemeniz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> gerekir, yukarıdaki örnek standart bir bitiş noktası ekler.  
  
 Duyuru bitiş noktaları eklediğinizde, aşağıdaki örnekte gösterildiği gibi `services` <> öğesine bir duyuru dinleyici hizmeti de eklemeniz gerekir.  
  
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
  
 Davranış, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> belirli bir bitiş noktasının keşfini etkinleştirmek veya devre dışı etmek için kullanılır.  Aşağıdaki örnek, biri bulma etkinleştirilmiş, diğeri de bulma devre dışı bırakılmış iki uygulama uç noktası olan bir hizmeti yapılandırır. Her bitiş noktası <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için bir davranış eklenir.  
  
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
  
 Davranış, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir. Aşağıdaki örnekte, bunun nasıl yapılacağını gösterilmektedir.  
  
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
  
 Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış, istemcilerin hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir. Aşağıdaki örnek, istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.  
  
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
  
 Hakkında <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> daha fazla <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bilgi için ve [WCF Discovery Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)bakın.  
  
## <a name="binding-element-configuration"></a>Bağlama Öğesi Yapılandırması  
 Bağlama öğesi yapılandırması istemci tarafında en ilginç. Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırmayı kullanabilirsiniz.  Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DiscoveryClient> kanalla özel bir bağlama oluşturur ve bir tür ve kapsam içeren bul ölçütlerini belirtir. Buna ek olarak, özellikleri <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> değerleri belirtir.  
  
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
  
 Bu özel bağlama yapılandırması istemci bitiş noktası ile başvurulmalıdır:  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 Bulma ölçütleri hakkında daha fazla bilgi için [Bkz. Bulma Ve Bulma Kriterleri.](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md) Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz: [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
  
## <a name="standard-endpoint-configuration"></a>Standart Bitiş Noktası Yapılandırması  
 Standart uç noktaları, bir veya daha fazla özellik (adres, bağlama veya sözleşme) veya değiştirilemeyen bir veya daha fazla özellik değerleri için varsayılan değerlere sahip önceden tanımlanmış uç noktalarıdır. .NET 4 gemi ile 3 keşif <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>ilgili <xref:System.ServiceModel.Discovery.DynamicEndpoint>standart uç noktaları: , , ve .  UdP <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> çok noktaya yayın bağlama üzerinde bulma işlemleri için önceden yapılandırılan standart bir uç noktadır. UdP <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> bağlama üzerinden duyuru iletileri göndermek için önceden yapılandırılan standart bir bitiş noktasıdır. Keşfedilen <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir hizmetin bitiş noktası adresini çalışma zamanında dinamik olarak bulmak için keşfedilmeyi kullanan standart bir uç noktadır.  Standart bağlamalar, eklenecek `endpoint` standart bitiş noktası türünü belirten tür özniteliği içeren <bir> öğesiyle belirtilir. Aşağıdaki örnekte, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>a' nın nasıl eklendirilir  
  
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
  
 Standart uç noktalar <`standardEndpoints`> öğesi olarak yapılandırılır. Aşağıdaki örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> "ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.  
  
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
  
 Standart bitiş noktası yapılandırmasını ekledikten sonra, aşağıdaki `endpoint` örnekte gösterildiği gibi, her bitiş noktası için <> öğesindeki yapılandırmaya başvurun.  
  
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
  
 Keşifte kullanılan diğer standart uç noktaların aksine, <xref:System.ServiceModel.Discovery.DynamicEndpoint>bir bağlama ve sözleşme belirtirsiniz. Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.  
  
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
  
 Standart uç noktaları hakkında daha fazla bilgi için [Bkz. Standart Uç Noktaları.](standard-endpoints.md)
