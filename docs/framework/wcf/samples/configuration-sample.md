---
title: Yapılandırma Örneği
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 5ac72db1fce0862381cd614499b5db4b9d95b2d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183910"
---
# <a name="configuration-sample"></a><span data-ttu-id="0ad23-102">Yapılandırma Örneği</span><span class="sxs-lookup"><span data-stu-id="0ad23-102">Configuration Sample</span></span>
<span data-ttu-id="0ad23-103">Bu örnek, bir hizmeti keşfedilebilir hale getirmek için bir yapılandırma dosyasının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ad23-104">Bu örnek yapılandırmada bulma uygular.</span><span class="sxs-lookup"><span data-stu-id="0ad23-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="0ad23-105">Kodda bulma uygulayan bir örnek için [Temel'e](../../../../docs/framework/wcf/samples/basic-sample.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0ad23-106">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0ad23-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad23-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0ad23-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="0ad23-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0ad23-109">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="0ad23-110">Hizmet Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="0ad23-110">Service Configuration</span></span>  
 <span data-ttu-id="0ad23-111">Bu örnekteki yapılandırma dosyası iki özellik gösterir:</span><span class="sxs-lookup"><span data-stu-id="0ad23-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="0ad23-112">Hizmetin standart <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>üzerinden keşfedilebilir hale getirilmesi.</span><span class="sxs-lookup"><span data-stu-id="0ad23-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="0ad23-113">Hizmetin uygulama bitiş noktası için keşifle ilgili bilgileri ayarlama ve standart bitiş noktasında keşifle ilgili ayarların bazılarını ayarlama.</span><span class="sxs-lookup"><span data-stu-id="0ad23-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="0ad23-114">Keşfi etkinleştirmek için, hizmetin uygulama yapılandırma dosyasında birkaç değişiklik yapılması gerekir:</span><span class="sxs-lookup"><span data-stu-id="0ad23-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="0ad23-115">`<service>` Öğeye bir bulma bitiş noktası eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="0ad23-116">Bu standart <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> bir bitiş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="0ad23-117">Bu, çalışma zamanının bulma hizmetiyle ilişkilendirdiyi gösteren bir sistem bitiş noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="0ad23-118">Bulma hizmeti bu uç noktadaki iletileri dinler.</span><span class="sxs-lookup"><span data-stu-id="0ad23-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="0ad23-119">`<serviceBehaviors>` Bölüme bir `<serviceDiscovery>` davranış eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="0ad23-120">Bu, hizmetin çalışma zamanında bulunmasını sağlar ve keşif `Probe` ve `Resolve` iletileri dinlemek için daha önce bahsedilen keşif bitiş noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="0ad23-121">Bu iki eklemeyle, hizmet belirtilen bulma bitiş noktasında keşfedilebilir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="0ad23-122">Aşağıdaki config snippet, uygulama bitiş noktası ve bir bulma bitiş noktası tanımlanan bir hizmeti gösterir:</span><span class="sxs-lookup"><span data-stu-id="0ad23-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="0ad23-123">Duyurulardan yararlanmak için bir duyuru bitiş noktası eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="0ad23-124">Bunu yapmak için, yapılandırma dosyasını aşağıdaki kodda gösterildiği şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0ad23-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="0ad23-125">Bulma hizmeti davranışına bir duyuru bitiş noktası eklemek, hizmet için varsayılan bir duyuru istemcisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ad23-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="0ad23-126">Bu, hizmet sırasıyla açılıp kapandığında hizmetin çevrimiçi ve çevrimdışı bir duyuru göndereceğini garanti eder.</span><span class="sxs-lookup"><span data-stu-id="0ad23-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="0ad23-127">Bu yapılandırma dosyası, ek davranışları değiştirerek bu basit adımların ötesine geçer.</span><span class="sxs-lookup"><span data-stu-id="0ad23-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="0ad23-128">Belirli uç noktaları kullanarak keşifle ilgili bilgileri denetlemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0ad23-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="0ad23-129">Diğer bir nokta, bir uç noktanın bulunup bulunamayacağını denetleyebilir ve <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> kullanıcı da bu bitiş noktasını ve özel XML meta verilerini işaretleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="0ad23-130">Bunu yapmak için, kullanıcı `behaviorConfiguration` uygulama bitiş noktasına bir özellik eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="0ad23-131">Bu durumda, uygulama bitiş noktasına aşağıdaki özellik eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="0ad23-132">Şimdi, davranış yapılandırma öğesi aracılığıyla, keşifle ilgili öznitelikleri denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad23-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="0ad23-133">Bu durumda, uygulama bitiş noktasına iki kapsam eklenir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="0ad23-134">Kapsamlar hakkında daha fazla bilgi [için, Bulma Ve Bulma Ölçütleri'ne](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="0ad23-135">Ayrıca, bulma bitiş noktasının belirli ayrıntılarını da denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad23-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="0ad23-136">Bu yapılır <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="0ad23-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="0ad23-137">Bu örnekte, kullanılan protokolün sürümü, aşağıdaki kod `maxResponseDelay` örneğinde gösterildiği gibi bir öznitelik eklemenin yanı sıra değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="0ad23-138">Bu örnekte kullanılan yapılandırma dosyasının tamamı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0ad23-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="0ad23-139">İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="0ad23-139">Client Configuration</span></span>  
 <span data-ttu-id="0ad23-140">İstemci için uygulama yapılandırma `standardEndpoint` dosyasında, aşağıdaki config snippet'te gösterildiği gibi keşfi kullanmak için bir tür `dynamicEndpoint` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="0ad23-141">İstemci bir `dynamicEndpoint`, çalışma zamanı otomatik olarak keşif gerçekleştirir kullanır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="0ad23-142">Keşif sırasında, kullanılacak keşif bitiş noktasının `discoveryClientSettings` türünü belirten bölümde tanımlananlar gibi çeşitli ayarlar kullanılır:</span><span class="sxs-lookup"><span data-stu-id="0ad23-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="0ad23-143">Hizmetleri aramak için kullanılan bul ölçütleri:</span><span class="sxs-lookup"><span data-stu-id="0ad23-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="0ad23-144">Bu örnek bu özelliği genişletir <xref:System.ServiceModel.Discovery.FindCriteria> ve istemci tarafından kullanılan yanı sıra keşif `updDiscoveryEndpoint` için kullanılan standardın bazı özelliklerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="0ad23-145">Bir <xref:System.ServiceModel.Discovery.FindCriteria> kapsam ve belirli `scopeMatchBy` bir algoritmanın yanı sıra özel sonlandırma ölçütlerini kullanmak üzere değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="0ad23-146">Ayrıca, örnek, iletileri kullanarak `Probe` istemcinin XML öğelerini nasıl gönderebileceğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="0ad23-147">Son olarak, aşağıdaki yapılandırma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>dosyasında gösterildiği gibi kullanılan protokolün sürümü ve UDP'ye özgü ayarlar gibi bazı değişiklikler yapılır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="0ad23-148">Aşağıda örnekte kullanılan tam istemci yapılandırmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0ad23-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0ad23-149">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0ad23-149">To use this sample</span></span>  
  
1. <span data-ttu-id="0ad23-150">Bu örnek, HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ALA'ları eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="0ad23-151">Daha fazla bilgi için [http ve HTTPS yapılandırma](../feature-details/configuring-http-and-https.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="0ad23-152">Aşağıdaki komutu yükseltilmiş bir ayrıcalıkta yürütmek uygun ALA'ları eklemelidir.</span><span class="sxs-lookup"><span data-stu-id="0ad23-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="0ad23-153">Komut olduğu gibi çalışmıyorsa, Etki Alanı nızı ve Kullanıcı Adınızı aşağıdaki bağımsız değişkenler için değiştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ad23-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="0ad23-154">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="0ad23-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="0ad23-155">Yapı dizininden çalıştırılabilen hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="0ad23-156">İstemciyi çalıştırılabilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-156">Run the client executable.</span></span> <span data-ttu-id="0ad23-157">İstemcinin hizmeti bulabilmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ad23-157">Note that the client is able to locate the service.</span></span>  
