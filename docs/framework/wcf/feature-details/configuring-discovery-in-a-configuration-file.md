---
description: 'Daha fazla bilgi edinin: yapılandırma dosyasında bulmayı yapılandırma'
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 95ac1a08d40f16141dc5c8763640a258b15ef497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743297"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="7af03-103">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7af03-103">Configuring Discovery in a Configuration File</span></span>

<span data-ttu-id="7af03-104">Bulma sırasında kullanılan dört ana yapılandırma ayarı grubu vardır.</span><span class="sxs-lookup"><span data-stu-id="7af03-104">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="7af03-105">Bu konu, her birini kısaca betimleyen ve bunların nasıl yapılandırılacağını gösteren örnekler gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="7af03-105">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="7af03-106">Her bölüm için, her alanla ilgili daha ayrıntılı bir belge bağlantısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7af03-106">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="7af03-107">Davranış yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7af03-107">Behavior Configuration</span></span>  

 <span data-ttu-id="7af03-108">Bulma hizmeti davranışlarını ve uç nokta davranışlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="7af03-108">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="7af03-109"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Davranış, bir hizmetin tüm uç noktaları için bulmayı sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7af03-109">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="7af03-110">Aşağıdaki örnek, ' nin nasıl ekleneceğini <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç noktasının nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7af03-110">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="7af03-111">Davranışı belirttikten sonra, `service` Aşağıdaki örnekte gösterildiği gibi bir <> öğesinden başvuru yapın.</span><span class="sxs-lookup"><span data-stu-id="7af03-111">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="7af03-112">Bir hizmetin bulunabilir olması için, bir bulma uç noktası da eklemeniz gerekir, yukarıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Standart bir uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="7af03-112">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="7af03-113">Duyuru uç noktaları eklediğinizde, `services` Aşağıdaki örnekte gösterildiği gibi <> öğesine bir duyuru dinleyicisi hizmeti de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7af03-113">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7af03-114"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Davranış, belirli bir uç noktanın bulunmasını etkinleştirmek veya devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7af03-114">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="7af03-115">Aşağıdaki örnek, bir hizmeti bulma etkin ve diğeri de bulma devre dışı olan iki uygulama uç noktası ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7af03-115">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="7af03-116">Her bitiş noktası için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış eklenir.</span><span class="sxs-lookup"><span data-stu-id="7af03-116">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="7af03-117">Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış, hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7af03-117">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="7af03-118">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7af03-118">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="7af03-119"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>Bu davranış, istemcilerin Hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7af03-119">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="7af03-120">Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7af03-120">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="7af03-121">Hakkında daha fazla bilgi <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> için <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz. [WCF bulmaya genel bakış](wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7af03-121">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="7af03-122">Bağlama öğesi yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7af03-122">Binding Element Configuration</span></span>  

 <span data-ttu-id="7af03-123">Bağlama öğesi yapılandırması, istemci tarafında en ilginç bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="7af03-123">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="7af03-124">Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırma kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7af03-124">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="7af03-125">Aşağıdaki örnek, kanalla birlikte özel bir bağlama oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> ve bir tür ve kapsam içeren bulma ölçütünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7af03-125">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="7af03-126">Ayrıca, ve özellikleri için değerleri belirtir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> .</span><span class="sxs-lookup"><span data-stu-id="7af03-126">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="7af03-127">Bu özel bağlama yapılandırmasına bir istemci uç noktası tarafından başvurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="7af03-127">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="7af03-128">Bulma ölçütü hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="7af03-128">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="7af03-129">Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz. [WCF bulgu genel bakış](wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="7af03-129">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="7af03-130">Standart uç nokta yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7af03-130">Standard Endpoint Configuration</span></span>  

 <span data-ttu-id="7af03-131">Standart uç noktalar bir veya daha fazla Özellik (adres, bağlama veya sözleşme) veya değiştirebir veya daha fazla özellik değeri için varsayılan değerlere sahip önceden tanımlanmış uç noktalardır.</span><span class="sxs-lookup"><span data-stu-id="7af03-131">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="7af03-132">.NET 4, 3 bulma ile ilgili standart uç noktaları ile birlikte gelir: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> , ve <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7af03-132">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="7af03-133">, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> BIR UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="7af03-133">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="7af03-134">, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> BIR UDP bağlaması üzerinden duyuru iletileri gönderecek şekilde önceden yapılandırılmış standart bir uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="7af03-134">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="7af03-135">, <xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma kullanan standart bir uç noktadır ve bulunan bir hizmetin uç nokta adresini çalışma zamanında dinamik olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="7af03-135">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="7af03-136">Standart bağlamalar, `endpoint` eklenecek standart uç nokta türünü belirtilen tür özniteliğini içeren bir <> öğesiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7af03-136">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="7af03-137">Aşağıdaki örnek, ve ' nin nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7af03-137">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="7af03-138">Standart uç noktalar bir <`standardEndpoints`> öğesinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7af03-138">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="7af03-139">Aşağıdaki örnek, ve ' nin nasıl yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7af03-139">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="7af03-140">Standart uç nokta yapılandırmasını ekledikten sonra, `endpoint` Aşağıdaki örnekte gösterildiği gibi her bir uç nokta için <> öğesindeki yapılandırmaya başvurun.</span><span class="sxs-lookup"><span data-stu-id="7af03-140">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="7af03-141">Bulma sırasında kullanılan diğer standart uç noktaların aksine, için bir bağlama ve sözleşme belirtirsiniz <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7af03-141">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="7af03-142">Aşağıdaki örnek, ' nin nasıl ekleneceğini ve yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.DynamicEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7af03-142">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="7af03-143">Standart uç noktalar hakkında daha fazla bilgi için bkz. [standart uç noktalar](standard-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="7af03-143">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
