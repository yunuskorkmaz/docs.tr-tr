---
title: Standart Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: a2f8d45990c5bc845aeee87ee82a2d043d6d1292
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246452"
---
# <a name="standard-endpoints"></a><span data-ttu-id="ba10d-102">Standart Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="ba10d-102">Standard Endpoints</span></span>

<span data-ttu-id="ba10d-103">Uç noktalar bir adres, bağlama ve bir sözleşme belirtilerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ba10d-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="ba10d-104">Bir uç noktada ayarlanmış olabilecek diğer parametreler, davranış yapılandırması, üst bilgiler ve dinleme URI 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="ba10d-105">Belirli uç nokta türleri için bu değerler değişmez.</span><span class="sxs-lookup"><span data-stu-id="ba10d-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="ba10d-106">Örneğin, meta veri değişimi uç noktaları sözleşmeyi her zaman kullanır <xref:System.ServiceModel.Description.IMetadataExchange> .</span><span class="sxs-lookup"><span data-stu-id="ba10d-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="ba10d-107"><xref:System.ServiceModel.Description.WebHttpEndpoint>Her zaman belirli bir uç nokta davranışı gerektiren diğer uç noktalar.</span><span class="sxs-lookup"><span data-stu-id="ba10d-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="ba10d-108">Bir uç noktanın kullanılabilirliği, yaygın olarak kullanılan uç nokta özellikleri için varsayılan değerlere sahip uç noktalara sahip olunarak artırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="ba10d-109">Standart uç noktalar, bir geliştiricinin varsayılan değerleri olan veya bir ya da daha fazla bitiş noktası özelliklerinin değişmediğinden bir uç nokta tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba10d-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="ba10d-110">Bu uç noktalar, statik bir doğası bilgilerini belirtmek zorunda kalmadan böyle bir uç nokta kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba10d-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="ba10d-111">Standart uç noktalar, altyapı ve uygulama uç noktaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="ba10d-112">Altyapı uç noktaları</span><span class="sxs-lookup"><span data-stu-id="ba10d-112">Infrastructure Endpoints</span></span>  

 <span data-ttu-id="ba10d-113">Bir hizmet, hizmet yazarı tarafından açıkça uygulanmayan bazı özelliklerle uç noktalar açığa çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="ba10d-114">Örneğin, meta veri değişimi uç noktası sözleşmeyi kullanıma sunar <xref:System.ServiceModel.Description.IMetadataExchange> , ancak bir hizmet yazarı olarak bu arabirimi uygulamaz, WCF tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba10d-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="ba10d-115">Bu tür altyapı uç noktaları, bir veya daha fazla uç nokta özelliği için varsayılan değerlere sahiptir ve bunlardan bazıları geri alınamaz.</span><span class="sxs-lookup"><span data-stu-id="ba10d-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="ba10d-116"><xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>Meta veri değişimi uç noktasının özelliği olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange> ; ancak bağlama gibi diğer özellikler geliştirici tarafından sağlanabilecek.</span><span class="sxs-lookup"><span data-stu-id="ba10d-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="ba10d-117">Altyapı uç noktaları, <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliği olarak ayarlanarak tanımlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="ba10d-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="ba10d-118">Uygulama uç noktaları</span><span class="sxs-lookup"><span data-stu-id="ba10d-118">Application Endpoints</span></span>  

 <span data-ttu-id="ba10d-119">Uygulama geliştiricileri, adres, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktalarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="ba10d-120">Bir sınıf türeterek <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç nokta özelliklerini ayarlayarak standart bir uç nokta tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="ba10d-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="ba10d-121">Değiştirilebilen özellikler için varsayılan değerler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba10d-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="ba10d-122">Bazı diğer özellikler, değişmeyen statik değerlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="ba10d-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="ba10d-123">Aşağıdaki örnek, standart bir uç noktanın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-123">The following example shows how to implement a standard endpoint.</span></span>  
  
```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    { }  

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    { }  

    // Create the custom endpoint with a fixed binding
    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    // Definition of the additional property of this endpoint
    public bool Property { get; set; }
}
```
  
 <span data-ttu-id="ba10d-124">Bir yapılandırma dosyasında Kullanıcı tanımlı özel uç nokta kullanmak için, öğesinden bir sınıf türetmeniz <xref:System.ServiceModel.Configuration.StandardEndpointElement> , öğesinden bir sınıf türetmeniz <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> ve yeni standart uç noktayı app.config veya machine.config uzantı bölümüne kaydetmeniz gerekir.  , <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç nokta için yapılandırma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba10d-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    // Definition of the additional property for the standard endpoint element
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    // The additional property needs to be added to the properties of the standard endpoint element
    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    // Return the type of this standard endpoint
    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    // Create the custom service endpoint
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // Read the value given to the property in config and save it
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    // No validation in this sample
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```  
  
 <span data-ttu-id="ba10d-125">, <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> `standardEndpoints` Standart uç nokta yapılandırmasındaki <> bölümü altında görüntülenen koleksiyon için yedekleme türünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba10d-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="ba10d-126">Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="ba10d-127">Aşağıdaki örnek, uzantılar bölümünde standart bir uç noktanın nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
      </standardEndpointExtensions>
</extensions>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="ba10d-128">Standart uç nokta yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba10d-128">Configuring a Standard Endpoint</span></span>  

 <span data-ttu-id="ba10d-129">Standart uç noktalar, koda veya yapılandırmaya eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ba10d-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="ba10d-130">Koda standart bir uç nokta eklemek için, uygun standart uç nokta türünü örnek olarak oluşturmanız ve aşağıdaki örnekte gösterildiği gibi hizmet ana bilgisayarına eklemeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="ba10d-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="ba10d-131">Yapılandırmaya standart bir uç nokta eklemek için, `endpoint` <`service`> öğesine ve gerekli yapılandırma ayarlarına <> öğesinde bir <> öğesi ekleyin `standardEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="ba10d-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="ba10d-132">Aşağıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , ile birlikte gelen standart uç noktalardan birini nasıl ekleneceğini gösterir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ba10d-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
```xml  
<services>  
  <service>  
    <endpoint isSystemEndpoint="true" kind="udpDiscoveryEndpoint" />  
  </service>  
</services>  
<standardEndpoints>
  <udpDiscoveryEndpoint>  
     <standardEndpoint multicastAddress="soap.udp://239.255.255.250:3702" />
  </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="ba10d-133">Standart uç nokta türü, <> öğesindeki Kind özniteliği kullanılarak belirtilir `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="ba10d-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="ba10d-134">Uç nokta <> öğesi içinde yapılandırılır `standardEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="ba10d-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="ba10d-135">Yukarıdaki örnekte, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç nokta eklenir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ba10d-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="ba10d-136"><`udpDiscoveryEndpoint`> öğesi `standardEndpoint` , öğesinin özelliğini ayarlayan bir <> içerir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="ba10d-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="ba10d-137">.NET Framework birlikte gönderilen standart uç noktalar</span><span class="sxs-lookup"><span data-stu-id="ba10d-137">Standard Endpoints Shipped with the .NET Framework</span></span>  

 <span data-ttu-id="ba10d-138">Aşağıdaki tabloda ile birlikte gelen standart uç noktalar listelenmiştir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ba10d-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="ba10d-139">Hizmet meta verilerini açığa çıkarmak için kullanılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="ba10d-140">Hizmetler tarafından duyuru iletileri göndermek için kullanılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="ba10d-141">Bulma iletilerini göndermek için hizmetler tarafından kullanılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="ba10d-142">Bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="ba10d-143">Hizmetler tarafından bir UDP bağlaması üzerinden duyuru iletileri göndermek için kullanılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="ba10d-144">Çalışma zamanında dinamik olarak uç nokta adresini bulmak için WS-Discovery kullanan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="ba10d-145">Meta veri değişimi için standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="ba10d-146"><xref:System.ServiceModel.WebHttpBinding>Otomatik olarak davranışını ekleyen bağlama içeren standart bir uç nokta <xref:System.ServiceModel.Description.WebHttpBehavior></span><span class="sxs-lookup"><span data-stu-id="ba10d-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="ba10d-147"><xref:System.ServiceModel.WebHttpBinding>Davranışı otomatik olarak ekleyen bağlama içeren standart bir uç nokta <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .</span><span class="sxs-lookup"><span data-stu-id="ba10d-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="ba10d-148">Bağlama içeren standart bir uç nokta <xref:System.ServiceModel.WebHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="ba10d-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="ba10d-149">İş akışı örneklerinde denetim işlemlerini çağırmanızı sağlayan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="ba10d-150">İş akışı oluşturmayı ve sürdürme yer işaretini destekleyen standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ba10d-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
