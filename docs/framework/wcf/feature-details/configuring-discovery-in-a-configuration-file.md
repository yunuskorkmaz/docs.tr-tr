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
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="ee919-102">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ee919-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="ee919-103">Bulma sırasında kullanılan dört ana yapılandırma ayarı grubu vardır.</span><span class="sxs-lookup"><span data-stu-id="ee919-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="ee919-104">Bu konu, her birini kısaca betimleyen ve bunların nasıl yapılandırılacağını gösteren örnekler gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="ee919-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="ee919-105">Her bölüm için, her alanla ilgili daha ayrıntılı bir belge bağlantısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ee919-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="ee919-106">Davranış yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ee919-106">Behavior Configuration</span></span>  
 <span data-ttu-id="ee919-107">Bulma hizmeti davranışlarını ve uç nokta davranışlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ee919-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="ee919-108">@No__t-0 davranışı, bir hizmetin tüm uç noktaları için bulmayı sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ee919-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="ee919-109">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ' nın nasıl ekleneceğini ve bir duyuru uç noktasının nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee919-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="ee919-110">Davranışı belirttikten sonra, aşağıdaki örnekte gösterildiği gibi bir < `service` > öğesinden başvuru yapın.</span><span class="sxs-lookup"><span data-stu-id="ee919-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="ee919-111">Bir hizmetin bulunabilir olması için, bir bulma uç noktası da eklemeniz gerekir, yukarıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="ee919-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="ee919-112">Duyuru uç noktaları eklediğinizde, aşağıdaki örnekte gösterildiği gibi < `services` > öğesine bir duyuru dinleyicisi hizmeti de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee919-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ee919-113">@No__t-0 davranışı belirli bir uç noktanın bulunmasını etkinleştirmek veya devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ee919-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="ee919-114">Aşağıdaki örnek, bir hizmeti bulma etkin ve diğeri de bulma devre dışı olan iki uygulama uç noktası ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ee919-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="ee919-115">Her bitiş noktası için <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.</span><span class="sxs-lookup"><span data-stu-id="ee919-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="ee919-116">@No__t-0 davranışı, hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee919-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="ee919-117">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ee919-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="ee919-118">@No__t-0 davranışı, istemcilerin Hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ee919-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="ee919-119">Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee919-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ee919-120">@No__t-0 ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> hakkında daha fazla bilgi için bkz. [WCF bulmaya genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee919-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="ee919-121">Bağlama öğesi yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ee919-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="ee919-122">Bağlama öğesi yapılandırması, istemci tarafında en ilginç bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="ee919-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="ee919-123">Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee919-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="ee919-124">Aşağıdaki örnek <xref:System.ServiceModel.Discovery.DiscoveryClient> kanalına sahip özel bir bağlama oluşturur ve bir tür ve kapsam içeren bulma ölçütünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee919-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="ee919-125">Ayrıca, <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri için değerler belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee919-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="ee919-126">Bu özel bağlama yapılandırmasına bir istemci uç noktası tarafından başvurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ee919-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 <span data-ttu-id="ee919-127">Bulma ölçütü hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="ee919-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="ee919-128">Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz. [WCF bulgu genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="ee919-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="ee919-129">Standart uç nokta yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ee919-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="ee919-130">Standart uç noktalar bir veya daha fazla Özellik (adres, bağlama veya sözleşme) veya değiştirebir veya daha fazla özellik değeri için varsayılan değerlere sahip önceden tanımlanmış uç noktalardır.</span><span class="sxs-lookup"><span data-stu-id="ee919-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="ee919-131">.NET 4, 3 bulma ile ilgili standart uç noktaları ile birlikte gelir: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="ee919-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="ee919-132">@No__t-0, bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="ee919-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="ee919-133">@No__t-0, bir UDP bağlaması üzerinden duyuru iletileri gönderecek şekilde önceden yapılandırılmış standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="ee919-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="ee919-134">@No__t-0, çalışma zamanında dinamik olarak bulunan bir hizmetin uç nokta adresini bulmak için bulma kullanan standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="ee919-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="ee919-135">Standart bağlamalar, eklenecek standart uç nokta türünü belirtilen tür özniteliğini içeren bir < `endpoint` > öğesiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ee919-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="ee919-136">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ' in nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee919-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="ee919-137">Standart uç noktalar < `standardEndpoints` > öğesinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ee919-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="ee919-138">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ' in nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee919-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="ee919-139">Standart uç nokta yapılandırmasını ekledikten sonra, aşağıdaki örnekte gösterildiği gibi her bir uç nokta için < `endpoint` > öğesinde yapılandırmaya başvurun.</span><span class="sxs-lookup"><span data-stu-id="ee919-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="ee919-140">Bulma sırasında kullanılan diğer standart uç noktaların aksine, <xref:System.ServiceModel.Discovery.DynamicEndpoint> için bir bağlama ve sözleşme belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee919-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="ee919-141">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DynamicEndpoint> ' ın nasıl ekleneceğini ve yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee919-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="ee919-142">Standart uç noktalar hakkında daha fazla bilgi için bkz. [standart uç noktalar](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="ee919-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
