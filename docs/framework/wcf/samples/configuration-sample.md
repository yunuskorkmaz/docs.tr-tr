---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 6d84085d06da117ebf13fa4bb714513aacc3abd6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594731"
---
# <a name="configuration-sample"></a><span data-ttu-id="371fe-102">Yapılandırma Örneği</span><span class="sxs-lookup"><span data-stu-id="371fe-102">Configuration Sample</span></span>
<span data-ttu-id="371fe-103">Bu örnek, bir hizmetin bulunabilir olması için bir yapılandırma dosyası kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="371fe-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="371fe-104">Bu örnek, yapılandırmada bulma işlemini uygular.</span><span class="sxs-lookup"><span data-stu-id="371fe-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="371fe-105">Kodda bulmayı uygulayan bir örnek için bkz. [temel](basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="371fe-105">For a sample that implements discovery in code, see [Basic](basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="371fe-106">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="371fe-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="371fe-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="371fe-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="371fe-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="371fe-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="371fe-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="371fe-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="371fe-110">Hizmet yapılandırması</span><span class="sxs-lookup"><span data-stu-id="371fe-110">Service Configuration</span></span>  
 <span data-ttu-id="371fe-111">Bu örnekteki yapılandırma dosyası iki özelliği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="371fe-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="371fe-112">Hizmetin bir standart üzerinde bulunabilir hale getirilmesi <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="371fe-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="371fe-113">Hizmetin uygulama uç noktası için bulma ile ilgili bilgileri ayarlama ve standart uç noktada bazı bulma ile ilgili ayarları ayarlama.</span><span class="sxs-lookup"><span data-stu-id="371fe-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="371fe-114">Bulmayı etkinleştirmek için, hizmet için uygulama yapılandırma dosyasında birkaç değişiklik yapılmalıdır:</span><span class="sxs-lookup"><span data-stu-id="371fe-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="371fe-115">Bir bulma uç noktasının öğeye eklenmesi gerekir `<service>` .</span><span class="sxs-lookup"><span data-stu-id="371fe-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="371fe-116">Bu, standart bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="371fe-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="371fe-117">Bu, çalışma zamanının bulma hizmetiyle ilişkilendiğini belirten bir sistem uç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="371fe-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="371fe-118">Bulma hizmeti bu uç noktada iletileri dinler.</span><span class="sxs-lookup"><span data-stu-id="371fe-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="371fe-119">`<serviceDiscovery>`Bölüme bir davranış eklenir `<serviceBehaviors>` .</span><span class="sxs-lookup"><span data-stu-id="371fe-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="371fe-120">Bu, hizmetin çalışma zamanında keşfedilmesini sağlar ve daha önce bulma ve iletileri dinlemek için bahsedilen bulma uç noktasını `Probe` kullanır `Resolve` .</span><span class="sxs-lookup"><span data-stu-id="371fe-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="371fe-121">Bu iki eklemele, hizmet belirtilen bulma uç noktasında bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="371fe-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="371fe-122">Aşağıdaki yapılandırma kod parçacığında, bir uygulama uç noktasına ve tanımlı bulma uç noktasına sahip bir hizmet gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="371fe-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="371fe-123">Duyuruların avantajlarından yararlanmak için bir duyuru uç noktası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="371fe-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="371fe-124">Bunu yapmak için, yapılandırma dosyasını aşağıdaki kodda gösterildiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="371fe-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="371fe-125">Bulma hizmeti davranışına bir duyuru uç noktası eklemek, hizmet için varsayılan bir duyuru istemcisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="371fe-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="371fe-126">Bu, hizmetin sırasıyla açık ve kapalı olduğu durumlarda hizmetin çevrimiçi ve çevrimdışı duyuru göndermesini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="371fe-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="371fe-127">Bu yapılandırma dosyası, ek davranışları değiştirerek yalnızca bu basit adımların ötesine geçer.</span><span class="sxs-lookup"><span data-stu-id="371fe-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="371fe-128">Belirli uç noktaları kullanarak bulma ile ilgili bilgileri denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="371fe-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="371fe-129">Diğer bir deyişle, bir Kullanıcı bir uç noktanın keşfedilip edilmeyeceğini denetleyebilir ve Kullanıcı bu uç noktayı <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> ve özel XML meta verilerini de işaretleyebilir.</span><span class="sxs-lookup"><span data-stu-id="371fe-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="371fe-130">Bunu yapmak için, kullanıcının `behaviorConfiguration` uygulama uç noktasına bir özellik eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="371fe-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="371fe-131">Bu durumda, aşağıdaki özellik uygulama uç noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="371fe-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="371fe-132">Şimdi, davranış yapılandırma öğesi sayesinde, bulma ile ilgili öznitelikleri denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="371fe-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="371fe-133">Bu durumda, uygulama uç noktasına iki kapsam eklenir.</span><span class="sxs-lookup"><span data-stu-id="371fe-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="371fe-134">Kapsamlar hakkında daha fazla bilgi için bkz. [bulma bulma ve FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="371fe-134">For more information about scopes, see [Discovery Find and FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="371fe-135">Bulma uç noktasının belirli ayrıntılarını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="371fe-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="371fe-136">Bu, aracılığıyla yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection> .</span><span class="sxs-lookup"><span data-stu-id="371fe-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="371fe-137">Bu örnekte, kullanılan protokolün sürümü değiştirilmiştir ve `maxResponseDelay` Aşağıdaki kod örneğinde gösterildiği gibi bir özniteliği ekler.</span><span class="sxs-lookup"><span data-stu-id="371fe-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="371fe-138">Aşağıda, bu örnekte kullanılan tüm yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="371fe-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="371fe-139">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="371fe-139">Client Configuration</span></span>  
 <span data-ttu-id="371fe-140">İstemcinin uygulama yapılandırma dosyasında, bir `standardEndpoint` türü `dynamicEndpoint` aşağıdaki yapılandırma parçacığında gösterildiği gibi bulmayı kullanmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="371fe-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="371fe-141">Bir istemci bir kullanırken `dynamicEndpoint` , çalışma zamanı bulmayı otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="371fe-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="371fe-142">Bulma sırasında, `discoveryClientSettings` kullanılacak bulma uç noktasının türünü belirten, bölümünde tanımlananlar gibi çeşitli ayarlar kullanılır:</span><span class="sxs-lookup"><span data-stu-id="371fe-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="371fe-143">Hizmetleri aramak için kullanılan bulma ölçütü:</span><span class="sxs-lookup"><span data-stu-id="371fe-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="371fe-144">Bu örnek, bu özelliği genişletir ve <xref:System.ServiceModel.Discovery.FindCriteria> istemcinin, bulma için kullanılan bazı özellikler özelliklerinin yanı sıra istemci tarafından kullanılan özellikleri değiştirir `updDiscoveryEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="371fe-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="371fe-145">, <xref:System.ServiceModel.Discovery.FindCriteria> Bir kapsamı ve belirli bir `scopeMatchBy` algoritmayı ve özel sonlandırma ölçütlerini kullanacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="371fe-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="371fe-146">Ayrıca, örnek ayrıca, bir istemcinin iletileri kullanarak nasıl XML öğeleri gönderebilirim gösterilmektedir `Probe` .</span><span class="sxs-lookup"><span data-stu-id="371fe-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="371fe-147">Son olarak, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> aşağıdaki yapılandırma dosyasında gösterildiği gibi, kullanılan protokol sürümü ve UDP 'ye özgü ayarlar gibi bazı değişiklikler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="371fe-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="371fe-148">Örnekte kullanılan tüm istemci yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="371fe-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
</configuration>
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="371fe-149">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="371fe-149">To use this sample</span></span>  
  
1. <span data-ttu-id="371fe-150">Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="371fe-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="371fe-151">Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="371fe-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="371fe-152">Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir.</span><span class="sxs-lookup"><span data-stu-id="371fe-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="371fe-153">Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="371fe-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="371fe-154">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="371fe-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="371fe-155">Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="371fe-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="371fe-156">İstemci yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="371fe-156">Run the client executable.</span></span> <span data-ttu-id="371fe-157">İstemcinin hizmeti bulabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="371fe-157">Note that the client is able to locate the service.</span></span>  
