---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: eb02b5d01b3f95ef741aa689cc66616fd598577b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741961"
---
# <a name="configuration-sample"></a><span data-ttu-id="8f750-102">Yapılandırma Örneği</span><span class="sxs-lookup"><span data-stu-id="8f750-102">Configuration Sample</span></span>
<span data-ttu-id="8f750-103">Bu örnek, bir hizmetin bulunabilir olması için bir yapılandırma dosyası kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f750-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f750-104">Bu örnek, yapılandırmada bulma işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="8f750-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="8f750-105">Kodda bulmayı uygulayan bir örnek için bkz. [temel](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8f750-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f750-106">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f750-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8f750-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8f750-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8f750-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8f750-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f750-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8f750-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="8f750-110">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8f750-110">Service Configuration</span></span>  
 <span data-ttu-id="8f750-111">Bu örnekteki yapılandırma dosyası iki özelliği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8f750-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="8f750-112">Hizmeti standart bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>bulunabilir hale getirme.</span><span class="sxs-lookup"><span data-stu-id="8f750-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="8f750-113">Hizmetin uygulama uç noktası için bulma ile ilgili bilgileri ayarlama ve standart uç noktada bazı bulma ile ilgili ayarları ayarlama.</span><span class="sxs-lookup"><span data-stu-id="8f750-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="8f750-114">Bulmayı etkinleştirmek için, hizmet için uygulama yapılandırma dosyasında birkaç değişiklik yapılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8f750-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="8f750-115">`<service>` öğesine bir bulma uç noktası eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f750-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="8f750-116">Bu bir standart <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="8f750-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="8f750-117">Bu, çalışma zamanının bulma hizmetiyle ilişkilendiğini belirten bir sistem uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="8f750-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="8f750-118">Bulma hizmeti bu uç noktada iletileri dinler.</span><span class="sxs-lookup"><span data-stu-id="8f750-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="8f750-119">`<serviceBehaviors>` bölümüne `<serviceDiscovery>` davranış eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f750-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="8f750-120">Bu, hizmetin çalışma zamanında keşfedilmesini sağlar ve daha önce bulma `Probe` ve `Resolve` iletilerini dinlemek için belirtilen bulma uç noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f750-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="8f750-121">Bu iki eklemele, hizmet belirtilen bulma uç noktasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="8f750-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="8f750-122">Aşağıdaki yapılandırma kod parçacığında, bir uygulama uç noktasına ve tanımlı bulma uç noktasına sahip bir hizmet gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8f750-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="8f750-123">Duyuruların avantajlarından yararlanmak için bir duyuru uç noktası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f750-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="8f750-124">Bunu yapmak için, yapılandırma dosyasını aşağıdaki kodda gösterildiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8f750-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="8f750-125">Bulma hizmeti davranışına bir duyuru uç noktası eklemek, hizmet için varsayılan bir duyuru istemcisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f750-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="8f750-126">Bu, hizmetin sırasıyla açık ve kapalı olduğu durumlarda hizmetin çevrimiçi ve çevrimdışı duyuru göndermesini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="8f750-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="8f750-127">Bu yapılandırma dosyası, ek davranışları değiştirerek yalnızca bu basit adımların ötesine geçer.</span><span class="sxs-lookup"><span data-stu-id="8f750-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="8f750-128">Belirli uç noktaları kullanarak bulma ile ilgili bilgileri denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8f750-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="8f750-129">Diğer bir deyişle, bir Kullanıcı bir uç noktanın keşfedilip edilmeyeceğini denetleyebilir ve Kullanıcı bu uç noktayı <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verileriyle işaretleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8f750-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="8f750-130">Bunu yapmak için, kullanıcının uygulama uç noktasına bir `behaviorConfiguration` özelliği eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f750-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="8f750-131">Bu durumda, aşağıdaki özellik uygulama uç noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="8f750-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="8f750-132">Şimdi, davranış yapılandırma öğesi sayesinde, bulma ile ilgili öznitelikleri denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f750-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="8f750-133">Bu durumda, uygulama uç noktasına iki kapsam eklenir.</span><span class="sxs-lookup"><span data-stu-id="8f750-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="8f750-134">Kapsamlar hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="8f750-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="8f750-135">Bulma uç noktasının belirli ayrıntılarını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f750-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="8f750-136">Bu, <xref:System.ServiceModel.Configuration.StandardEndpointsSection>aracılığıyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="8f750-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="8f750-137">Bu örnekte, kullanılan protokolün sürümü, aşağıdaki kod örneğinde gösterildiği gibi `maxResponseDelay` özniteliği eklenerek değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f750-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="8f750-138">Aşağıda, bu örnekte kullanılan tüm yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8f750-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="8f750-139">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="8f750-139">Client Configuration</span></span>  
 <span data-ttu-id="8f750-140">İstemcinin uygulama yapılandırma dosyasında, aşağıdaki yapılandırma parçacığında gösterildiği gibi bulmayı kullanmak için `dynamicEndpoint` türünde bir `standardEndpoint` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f750-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="8f750-141">İstemci bir `dynamicEndpoint`kullanırken, çalışma zamanı keşfi otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8f750-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="8f750-142">Bulma sırasında, kullanılacak bulma uç noktasının türünü belirten `discoveryClientSettings` bölümünde tanımlananlar gibi çeşitli ayarlar kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8f750-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="8f750-143">Hizmetleri aramak için kullanılan bulma ölçütü:</span><span class="sxs-lookup"><span data-stu-id="8f750-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="8f750-144">Bu örnek, bu özelliği genişleterek istemci tarafından kullanılan <xref:System.ServiceModel.Discovery.FindCriteria> ve bulma için kullanılan standart `updDiscoveryEndpoint` bazı özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8f750-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="8f750-145"><xref:System.ServiceModel.Discovery.FindCriteria>, bir kapsamı ve belirli bir `scopeMatchBy` algoritmasını ve özel sonlandırma ölçütlerini kullanacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="8f750-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="8f750-146">Ayrıca, örnek ayrıca, bir istemcinin `Probe` iletileri kullanarak nasıl XML öğeleri gönderebilirim gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f750-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="8f750-147">Son olarak, aşağıdaki yapılandırma dosyasında gösterildiği gibi, kullanılan protokol sürümü ve UDP 'ye özgü ayarlar gibi <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>bazı değişiklikler yapılır.</span><span class="sxs-lookup"><span data-stu-id="8f750-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="8f750-148">Örnekte kullanılan tüm istemci yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8f750-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8f750-149">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="8f750-149">To use this sample</span></span>  
  
1. <span data-ttu-id="8f750-150">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8f750-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="8f750-151">Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="8f750-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="8f750-152">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="8f750-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="8f750-153">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f750-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="8f750-154">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8f750-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="8f750-155">Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f750-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="8f750-156">İstemci yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8f750-156">Run the client executable.</span></span> <span data-ttu-id="8f750-157">İstemcinin hizmeti bulabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f750-157">Note that the client is able to locate the service.</span></span>  
