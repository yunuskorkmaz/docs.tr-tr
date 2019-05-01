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
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="af2bf-102">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="af2bf-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="af2bf-103">Dört büyük Grup bulma içinde kullanılan yapılandırma ayarları vardır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="af2bf-104">Bu konu, kısaca açıklanmaktadır ve nasıl yapılandırılacakları örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="af2bf-105">Aşağıdaki her bölümde, her alan hakkında daha fazla ayrıntılı belgeler için bir bağlantı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="af2bf-106">Davranışını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="af2bf-106">Behavior Configuration</span></span>  
 <span data-ttu-id="af2bf-107">Hizmet davranışları ve uç nokta davranışları bulma kullanır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="af2bf-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Davranış tüm bir hizmet uç noktaları için bulma olanağı sağlar ve duyuru uç noktaları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="af2bf-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="af2bf-109">Aşağıdaki örnek nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç noktasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="af2bf-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-110">Davranış belirttiğinizde, ondan başvuran bir <`service`> Aşağıdaki örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="af2bf-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-111">Yukarıdaki örnekte bir bulma uç noktası eklemeniz de bulunabilir olması için bir hizmet için sırada ekler bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="af2bf-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="af2bf-112">Duyuru uç noktaları eklerken bir duyuru dinleyici hizmetine de eklemeniz gerekir <`services`> Aşağıdaki örnekte gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="af2bf-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı etkinleştirmek veya belirli bir uç noktaya bulunmasını devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="af2bf-114">Aşağıdaki örnek, iki uygulama uç noktası ile bir hizmeti, etkin bulma ile diğeri devre dışı keşif ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="af2bf-115">Her uç nokta için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı da özel meta verileri, hizmet tarafından döndürülen meta veri uç noktası eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="af2bf-117">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı da kapsamları ve istemcilerin aramak için hizmetler için kullandığınız türleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="af2bf-119">Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-120">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="af2bf-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="af2bf-121">Bağlama öğesi yapılandırması</span><span class="sxs-lookup"><span data-stu-id="af2bf-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="af2bf-122">Bağlama öğesi yapılandırması istemci tarafında en ilginç.</span><span class="sxs-lookup"><span data-stu-id="af2bf-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="af2bf-123">Yapılandırma, bir WCF istemci uygulama hizmetlerini keşfetmek için bulma ölçütlerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af2bf-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="af2bf-124">Aşağıdaki örnek, özel bir bağlama ile oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> kanal ve türüne ve kapsamına içeren Bulma ölçütü belirtir.</span><span class="sxs-lookup"><span data-stu-id="af2bf-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="af2bf-125">Buna ek olarak, için değerler belirten <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="af2bf-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-126">Bu özel bağlama yapılandırma, bir istemci uç noktası tarafından başvurulması gerekir:</span><span class="sxs-lookup"><span data-stu-id="af2bf-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 <span data-ttu-id="af2bf-127">Bulma ölçütleri hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="af2bf-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="af2bf-128">Bulma ve bağlama öğeleri bkz hakkında daha fazla bilgi için [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="af2bf-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="af2bf-129">Standart uç nokta yapılandırması</span><span class="sxs-lookup"><span data-stu-id="af2bf-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="af2bf-130">Standart uç noktaları, bir veya daha fazla özellikler (adresi, bağlama veya sözleşme) ve değiştirilemez bir veya daha fazla özellik değerleri için varsayılan değerlere sahip önceden tanımlı uç noktalardır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="af2bf-131">.NET 4, 3 ile birlikte gelen bulma ilgili standart uç noktaları: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="af2bf-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="af2bf-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Olduğu için bulma işlemlerini bir UDP çok noktaya yayın önceden yapılandırılmış bir standart uç nokta bağlama.</span><span class="sxs-lookup"><span data-stu-id="af2bf-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="af2bf-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> UDP bağlama üzerinden Duyurunun ileti göndermek için önceden yapılandırılmış bir standart uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="af2bf-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma, bulunan bir Hizmeti uç nokta adresini çalışma zamanında dinamik olarak bulmak için kullandığı standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="af2bf-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="af2bf-135">Standart bağlamaları ile belirtilen bir <`endpoint`> eklemek için standart uç nokta türü belirtilen tür öznitelik içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="af2bf-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="af2bf-136">Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="af2bf-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-137">Standart uç noktaları yapılandırılmış bir <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="af2bf-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="af2bf-138">Aşağıdaki örnek nasıl yapılandırılacağı gösterilmektedir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="af2bf-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-139">Standart uç nokta yapılandırması ekledikten sonra yapılandırmayı başvuru <`endpoint`> Aşağıdaki örnekte gösterildiği gibi her uç nokta için öğesi.</span><span class="sxs-lookup"><span data-stu-id="af2bf-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-140">Bulma içinde kullanılan diğer standart uç noktaları, farklı bir bağlama belirtin ve için sözleşme <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="af2bf-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="af2bf-141">Aşağıdaki örnek, ekleme ve yapılandırma işlemi gösterilmektedir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="af2bf-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="af2bf-142">Standart uç noktaları hakkında daha fazla bilgi için bkz: [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="af2bf-142">For more information about standard endpoints see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span></span>
