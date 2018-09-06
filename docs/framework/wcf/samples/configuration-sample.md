---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: ae1b98d4afcc4a7bc97a4668ef7d974b27cafed9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862085"
---
# <a name="configuration-sample"></a><span data-ttu-id="d2d93-102">Yapılandırma Örneği</span><span class="sxs-lookup"><span data-stu-id="d2d93-102">Configuration Sample</span></span>
<span data-ttu-id="d2d93-103">Bu örnek, bir hizmet bulunabilir hale getirmek için bir yapılandırma dosyası kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2d93-104">Bu örnek yapılandırmada bulma uygular.</span><span class="sxs-lookup"><span data-stu-id="d2d93-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="d2d93-105">Bulma uygulayan kodda bir örnek için bkz. [temel](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d2d93-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2d93-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d2d93-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d2d93-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d2d93-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d2d93-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d2d93-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2d93-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2d93-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="d2d93-110">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d2d93-110">Service Configuration</span></span>  
 <span data-ttu-id="d2d93-111">Bu örnek yapılandırma dosyasında iki özelliklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="d2d93-111">The configuration file in this sample demonstrates two features:</span></span>  
  
-   <span data-ttu-id="d2d93-112">Hizmetin bir standart bulunabilir olmasını sağlama <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="d2d93-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
-   <span data-ttu-id="d2d93-113">Bulma ile ilgili bilgi hizmetin uygulama uç noktası ve bazı standart uç noktasında bulma ile ilgili ayarlar ayarlama için ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="d2d93-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="d2d93-114">Bulmayı etkinleştirmek için birkaç değişiklik hizmeti için uygulama yapılandırma dosyasında yapılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="d2d93-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
-   <span data-ttu-id="d2d93-115">Bulma uç noktası eklenmelidir `<service>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d2d93-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="d2d93-116">Bu bir standarttır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası.</span><span class="sxs-lookup"><span data-stu-id="d2d93-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="d2d93-117">Bu çalışma zamanı bulma hizmeti ile ilişkilendiren bir sistem uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="d2d93-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="d2d93-118">Bu uç nokta ileti bulma hizmeti dinler.</span><span class="sxs-lookup"><span data-stu-id="d2d93-118">The discovery service listens for messages on this endpoint.</span></span>  
  
-   <span data-ttu-id="d2d93-119">A `<serviceDiscovery>` davranışı eklenir `<serviceBehaviors>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="d2d93-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="d2d93-120">Bu çalışma zamanında bulunacak hizmetini etkinleştirir ve bulma için dinlemek için daha önce bahsedilen bulma uç noktası kullanan `Probe` ve `Resolve` iletileri.</span><span class="sxs-lookup"><span data-stu-id="d2d93-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="d2d93-121">Bu iki eklemeleriyle, hizmet belirtilen bulma uç noktada bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="d2d93-122">Yapılandırma aşağıdaki kod parçacığında, bir uygulama uç noktası ve tanımlanmış bir bulma uç noktası ile bir hizmeti gösterir:</span><span class="sxs-lookup"><span data-stu-id="d2d93-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="d2d93-123">Duyuruları yararlanmak için bir duyuru uç noktası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="d2d93-124">Bunu yapmak için aşağıdaki kodda gösterildiği gibi yapılandırma dosyasını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="d2d93-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="d2d93-125">Bir duyuru uç nokta ekleme için bulma hizmet davranışı, hizmet için varsayılan bir duyuru istemcisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2d93-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="d2d93-126">Bu hizmeti açık ve kapalı sırasıyla hizmet çevrimiçi ve çevrimdışı duyuru gönderir güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="d2d93-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="d2d93-127">Bu yapılandırma dosyası, yalnızca basit adımları ek davranışları değiştirerek gider.</span><span class="sxs-lookup"><span data-stu-id="d2d93-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="d2d93-128">Özel uç noktaları kullanarak bulma ile ilgili bilgileri denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d2d93-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="d2d93-129">Diğer bir deyişle, bir kullanıcı bir uç nokta bulunan ve kullanıcı uç noktasına da işaretleyebilirsiniz denetleyebilirsiniz <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verileri.</span><span class="sxs-lookup"><span data-stu-id="d2d93-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="d2d93-130">Bunu yapmak için kullanıcıyı eklemeniz gerekir bir `behaviorConfiguration` özelliğini uygulama uç noktası.</span><span class="sxs-lookup"><span data-stu-id="d2d93-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="d2d93-131">Bu durumda, aşağıdaki özellik için uygulama uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="d2d93-132">Şimdi, davranış yapılandırma öğesi bulma ile ilgili özniteliklere denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d93-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="d2d93-133">Bu durumda, iki kapsam için bir uygulama uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="d2d93-134">Kapsamlar hakkında daha fazla bilgi için bkz: [bulma bulma ve FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="d2d93-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="d2d93-135">Belirli bir bulma uç noktası ayrıntılarını ayrıca denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d93-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="d2d93-136">Bu yoluyla yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="d2d93-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="d2d93-137">Bu örnekte, ekleme yanı sıra kullanılan protokol sürümünü değiştiren bir `maxResponseDelay` öznitelik aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d2d93-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="d2d93-138">Bu örnekte kullanılan tam yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d2d93-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="d2d93-139">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d2d93-139">Client Configuration</span></span>  
 <span data-ttu-id="d2d93-140">İstemci, uygulama yapılandırma dosyasında bir `standardEndpoint` türü `dynamicEndpoint` bulma aşağıdaki yapılandırma kod parçacığında gösterildiği gibi yararlanmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2d93-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="d2d93-141">Bir istemci kullanarak ne zaman bir `dynamicEndpoint`, çalışma zamanı otomatik olarak bulma işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="d2d93-142">İçinde tanımlanan gibi bulma sırasında kullanılan çeşitli ayarları `discoveryClientSettings` bölümünde, kullanmak için bulma uç noktası türünü belirtir:</span><span class="sxs-lookup"><span data-stu-id="d2d93-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="d2d93-143">Hizmetleri aramak için kullanılan Bulma ölçütü:</span><span class="sxs-lookup"><span data-stu-id="d2d93-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="d2d93-144">Bu örnek, bu özellik genişleten ve değiştiren <xref:System.ServiceModel.Discovery.FindCriteria> istemci yanı sıra tarafından standart bazı özellikler kullanılan `updDiscoveryEndpoint` bulma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d2d93-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="d2d93-145"><xref:System.ServiceModel.Discovery.FindCriteria> Kapsam ve belirli bir değişiklik `scopeMatchBy` özel sonlandırma ölçütünü yanı sıra algoritması.</span><span class="sxs-lookup"><span data-stu-id="d2d93-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="d2d93-146">Ayrıca, örnek aynı zamanda bir istemci kullanarak XML öğeleri nasıl gönderebilir gösterir `Probe` iletileri.</span><span class="sxs-lookup"><span data-stu-id="d2d93-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="d2d93-147">Son olarak, bazı değişiklikler yapılır <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>kullanılan protokol sürümünü ve UDP özgü ayarları aşağıdaki yapılandırma dosyasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d2d93-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="d2d93-148">Örnekte kullanılan tam istemci yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d2d93-149">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d2d93-149">To use this sample</span></span>  
  
1.  <span data-ttu-id="d2d93-150">Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="d2d93-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="d2d93-151">Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2d93-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="d2d93-152">Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2d93-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="d2d93-153">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d2d93-153">Build the solution.</span></span>  
  
3.  <span data-ttu-id="d2d93-154">Yürütülebilir hizmet oluşturma dizinden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2d93-154">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="d2d93-155">İstemci yürütülebilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2d93-155">Run the client executable.</span></span> <span data-ttu-id="d2d93-156">İstemci hizmetini bulun mümkün olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2d93-156">Note that the client is able to locate the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2d93-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2d93-157">See Also</span></span>
