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
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="9764a-102">Yapılandırma Dosyasındaki Bir Keşfi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9764a-102">Configuring Discovery in a Configuration File</span></span>
<span data-ttu-id="9764a-103">Keşifte kullanılan dört ana yapılandırma ayarı grubu vardır.</span><span class="sxs-lookup"><span data-stu-id="9764a-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="9764a-104">Bu konu, her birini kısaca açıklar ve bunları nasıl yapılandıracağınıza ait örnekler gösterir.</span><span class="sxs-lookup"><span data-stu-id="9764a-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="9764a-105">Her bölümü takip her alan hakkında daha derinlemesine belgeler için bir bağlantı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9764a-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="9764a-106">Davranış Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9764a-106">Behavior Configuration</span></span>  
 <span data-ttu-id="9764a-107">Bulma, hizmet davranışları ve uç nokta davranışları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9764a-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="9764a-108">Davranış, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir hizmetin tüm uç noktalarının bulunmasını sağlar ve duyuru uç noktalarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9764a-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="9764a-109">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru bitiş noktasının nasıl ekleyeceğinive belirtin.</span><span class="sxs-lookup"><span data-stu-id="9764a-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
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
  
 <span data-ttu-id="9764a-110">Davranışı belirttikten sonra, aşağıdaki örnekte gösterildiği gibi <`service`> öğesinden başvurun.</span><span class="sxs-lookup"><span data-stu-id="9764a-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="9764a-111">Bir hizmetin bulunabilmesi için, bir keşif bitiş noktası da eklemeniz <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> gerekir, yukarıdaki örnek standart bir bitiş noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="9764a-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="9764a-112">Duyuru bitiş noktaları eklediğinizde, aşağıdaki örnekte gösterildiği gibi `services` <> öğesine bir duyuru dinleyici hizmeti de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9764a-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9764a-113">Davranış, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> belirli bir bitiş noktasının keşfini etkinleştirmek veya devre dışı etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9764a-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="9764a-114">Aşağıdaki örnek, biri bulma etkinleştirilmiş, diğeri de bulma devre dışı bırakılmış iki uygulama uç noktası olan bir hizmeti yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="9764a-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="9764a-115">Her bitiş noktası <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için bir davranış eklenir.</span><span class="sxs-lookup"><span data-stu-id="9764a-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
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
  
 <span data-ttu-id="9764a-116">Davranış, <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> hizmet tarafından döndürülen uç nokta meta verilerine özel meta veri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9764a-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="9764a-117">Aşağıdaki örnekte, bunun nasıl yapılacağını gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9764a-117">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="9764a-118">Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> davranış, istemcilerin hizmetleri aramak için kullandığı kapsamları ve türleri eklemek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9764a-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="9764a-119">Aşağıdaki örnek, istemci tarafı yapılandırma dosyasında bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9764a-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
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
  
 <span data-ttu-id="9764a-120">Hakkında <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> daha fazla <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> bilgi için ve [WCF Discovery Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="9764a-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="9764a-121">Bağlama Öğesi Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9764a-121">Binding Element Configuration</span></span>  
 <span data-ttu-id="9764a-122">Bağlama öğesi yapılandırması istemci tarafında en ilginç.</span><span class="sxs-lookup"><span data-stu-id="9764a-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="9764a-123">Bir WCF istemci uygulamasından hizmetleri bulmak için kullanılan bulma ölçütlerini belirtmek için yapılandırmayı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9764a-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="9764a-124">Aşağıdaki örnek, <xref:System.ServiceModel.Discovery.DiscoveryClient> kanalla özel bir bağlama oluşturur ve bir tür ve kapsam içeren bul ölçütlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9764a-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="9764a-125">Buna ek olarak, özellikleri <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> ve <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9764a-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
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
  
 <span data-ttu-id="9764a-126">Bu özel bağlama yapılandırması istemci bitiş noktası ile başvurulmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9764a-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="9764a-127">Bulma ölçütleri hakkında daha fazla bilgi için [Bkz. Bulma Ve Bulma Kriterleri.](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)</span><span class="sxs-lookup"><span data-stu-id="9764a-127">For more information about find criteria see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="9764a-128">Bulma ve bağlama öğeleri hakkında daha fazla bilgi için bkz: [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9764a-128">For more information about discovery and binding elements see, [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="9764a-129">Standart Bitiş Noktası Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="9764a-129">Standard Endpoint Configuration</span></span>  
 <span data-ttu-id="9764a-130">Standart uç noktaları, bir veya daha fazla özellik (adres, bağlama veya sözleşme) veya değiştirilemeyen bir veya daha fazla özellik değerleri için varsayılan değerlere sahip önceden tanımlanmış uç noktalarıdır.</span><span class="sxs-lookup"><span data-stu-id="9764a-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="9764a-131">.NET 4 gemi ile 3 keşif <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>ilgili <xref:System.ServiceModel.Discovery.DynamicEndpoint>standart uç noktaları: , , ve .</span><span class="sxs-lookup"><span data-stu-id="9764a-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="9764a-132">UdP <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> çok noktaya yayın bağlama üzerinde bulma işlemleri için önceden yapılandırılan standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="9764a-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="9764a-133">UdP <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> bağlama üzerinden duyuru iletileri göndermek için önceden yapılandırılan standart bir bitiş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="9764a-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="9764a-134">Keşfedilen <xref:System.ServiceModel.Discovery.DynamicEndpoint> bir hizmetin bitiş noktası adresini çalışma zamanında dinamik olarak bulmak için keşfedilmeyi kullanan standart bir uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="9764a-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="9764a-135">Standart bağlamalar, eklenecek `endpoint` standart bitiş noktası türünü belirten tür özniteliği içeren <bir> öğesiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9764a-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="9764a-136">Aşağıdaki örnekte, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>a' nın nasıl eklendirilir</span><span class="sxs-lookup"><span data-stu-id="9764a-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="9764a-137">Standart uç noktalar <`standardEndpoints`> öğesi olarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9764a-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="9764a-138">Aşağıdaki örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> "ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9764a-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="9764a-139">Standart bitiş noktası yapılandırmasını ekledikten sonra, aşağıdaki `endpoint` örnekte gösterildiği gibi, her bitiş noktası için <> öğesindeki yapılandırmaya başvurun.</span><span class="sxs-lookup"><span data-stu-id="9764a-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="9764a-140">Keşifte kullanılan diğer standart uç noktaların aksine, <xref:System.ServiceModel.Discovery.DynamicEndpoint>bir bağlama ve sözleşme belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9764a-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="9764a-141">Aşağıdaki örnekte, bir <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9764a-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
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
  
 <span data-ttu-id="9764a-142">Standart uç noktaları hakkında daha fazla bilgi için [Bkz. Standart Uç Noktaları.](standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="9764a-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
