---
title: Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ba224bbf27e5a61168040c944bb940c3e6b0d8c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="71ca9-102">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71ca9-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="71ca9-103">Dört ana gruplarını bulmayı kullanılan yapılandırma ayarlarını vardır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="71ca9-104">Bu konuda kısaca açıklanmaktadır ve bunların nasıl yapılandırılacağı örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="71ca9-105">Her bölüm aşağıdaki her bir alan hakkında daha fazla ayrıntılı belgeler için bir bağlantı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="71ca9-106">Davranışını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71ca9-106">Behavior Configuration</span></span>  
 <span data-ttu-id="71ca9-107">Hizmet davranışları ve uç nokta davranışları bulma kullanır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="71ca9-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Davranışı bulma bir hizmetin bitiş noktalarının tümü için etkinleştirir ve duyuru uç noktaları belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="71ca9-109">Aşağıdaki örnekte nasıl ekleneceğini gösterir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve bir duyuru uç nokta belirtin.</span><span class="sxs-lookup"><span data-stu-id="71ca9-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-110">Davranış belirttiğinizde, ondan başvuran bir <`service`> Aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="71ca9-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-111">Yukarıdaki örnekte bir bulma uç noktası da eklemelisiniz bulunabilir olması bir hizmet için sırayla ekler bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="71ca9-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="71ca9-112">Duyuru uç noktaları eklerken bir duyuru dinleme hizmeti de eklemeniz gerekir <`services`> Aşağıdaki örnekte gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="71ca9-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranışı etkinleştirmek veya belirli bir uç bulmayı devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="71ca9-114">Aşağıdaki örnekte, iki uygulama uç noktaları olan bir hizmeti, etkin bulma ile diğeri devre dışı bulma ile yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="71ca9-115">Her uç noktası için bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranışı eklenir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranış da hizmet tarafından döndürülen uç noktası meta verileri için özel meta verileri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="71ca9-117">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> Davranış da kapsamlar ve Hizmetleri için aranacak istemcileri kullanmak türleri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="71ca9-119">Aşağıdaki örnek, bir istemci tarafı yapılandırma dosyasında bunu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-120">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bkz [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71ca9-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="71ca9-121">Bağlama öğesi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="71ca9-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="71ca9-122">Öğesi yapılandırma bağlama istemci tarafında en ilginç olacaktır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="71ca9-123">Yapılandırma Hizmetleri bir WCF istemci uygulamasından bulmak için kullanılan Bul ölçütlerini belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71ca9-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="71ca9-124">Aşağıdaki örnek ile özel bağlama oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> kanal ve türüne ve kapsamına içerir Bul ölçütlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="71ca9-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="71ca9-125">Ayrıca için değerleri belirtir <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="71ca9-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-126">Bu özel bağlama yapılandırma istemci uç noktası tarafından başvurulan gerekir:</span><span class="sxs-lookup"><span data-stu-id="71ca9-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
    </client>  
```  
  
 <span data-ttu-id="71ca9-127">Bulma ölçütleri hakkında daha fazla bilgi için bkz: [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="71ca9-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="71ca9-128">Bulma ve bağlama öğeleri bakın, hakkında daha fazla bilgi için [WCF keşif genel bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="71ca9-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="71ca9-129">Standart uç nokta yapılandırması</span><span class="sxs-lookup"><span data-stu-id="71ca9-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="71ca9-130">Standart uç noktaları, bir veya daha fazla özellikleri (adresi, bağlama veya sözleşme) veya değiştiremezsiniz bir veya daha fazla özellik değerleri için varsayılan değerleri olan önceden tanımlanmış noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="71ca9-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="71ca9-131">.NET 4, 3 ile birlikte gelen bulma ilgili standart uç noktaları: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, ve <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="71ca9-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="71ca9-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Olduğu için bulma işlemlerini UDP çok noktaya yayın önceden yapılandırılmış standart bir uç nokta bağlama.</span><span class="sxs-lookup"><span data-stu-id="71ca9-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="71ca9-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> UDP bağlama üzerinden duyuru iletileri göndermek üzere önceden yapılandırılmıştır standart bir uç noktası.</span><span class="sxs-lookup"><span data-stu-id="71ca9-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="71ca9-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint> Bulma bulunan hizmet uç noktası adresi çalışma zamanında dinamik olarak bulmak için kullandığı standart bir uç noktası.</span><span class="sxs-lookup"><span data-stu-id="71ca9-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="71ca9-135">Standart bağlamaları ile belirtilen bir <`endpoint`> öğesi eklemek için standart uç nokta türü belirtilen tür özniteliği içeriyor.</span><span class="sxs-lookup"><span data-stu-id="71ca9-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="71ca9-136">Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="71ca9-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-137">Standart uç noktaları olarak yapılandırılmış olan bir <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="71ca9-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="71ca9-138">Aşağıdaki örnekte nasıl yapılandırılacağını gösterir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="71ca9-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-139">Standart uç nokta yapılandırması ekledikten sonra yapılandırmada başvuru <`endpoint`> öğesi aşağıdaki örnekte gösterildiği gibi her bitiş noktasıyla ilgili.</span><span class="sxs-lookup"><span data-stu-id="71ca9-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-140">Bulmayı kullanılan diğer standart uç noktaları, farklı bir bağlama belirtin ve için sözleşme <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="71ca9-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="71ca9-141">Aşağıdaki örnek eklemek ve yapılandırmak nasıl gösterir bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="71ca9-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="71ca9-142">Standart uç noktaları hakkında daha fazla bilgi için bkz: [standart uç noktaları](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="71ca9-142">For more information about standard endpoints see [Standard Endpoints](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)</span></span>
