---
title: Standart Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747777"
---
# <a name="standard-endpoints"></a><span data-ttu-id="fbff5-102">Standart Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="fbff5-102">Standard Endpoints</span></span>
<span data-ttu-id="fbff5-103">Uç noktaları bir adresi, bağlama ve bir sözleşme belirterek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fbff5-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="fbff5-104">Bir uç nokta üzerinde ayarlanabilir diğer parametreler URI'ler dinlemek ve daha davranışı yapılandırmasına, üstbilgiler, içerir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="fbff5-105">Belirli türde uç noktalar, bu değerleri değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="fbff5-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="fbff5-106">Örneğin, meta veri değişimi uç noktalar her zaman kullan <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme.</span><span class="sxs-lookup"><span data-stu-id="fbff5-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="fbff5-107">Diğer uç noktalardan gibi <xref:System.ServiceModel.Description.WebHttpEndpoint> her zaman bir belirtilen uç nokta davranışı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="fbff5-108">Bir uç noktanın kullanılabilirliğini uç noktaları için yaygın olarak kullanılan uç noktası özellikleri varsayılan değerlerle sağlayarak geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="fbff5-109">Standart uç noktalarının etkinleştirilmesi varsayılan değerlerine sahip bir uç noktayı tanımlamak bir geliştirici ya da burada bir veya daha fazla uç noktasının özelliklerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="fbff5-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="fbff5-110">Bu uç noktaları, statik yapısı bilgileri belirtmenize gerek kalmadan bu tür, bir uç noktası kullan olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fbff5-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="fbff5-111">Standart uç noktaları, altyapı ve uygulama uç noktaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="fbff5-112">Altyapı uç noktaları</span><span class="sxs-lookup"><span data-stu-id="fbff5-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="fbff5-113">Bir hizmet uç noktaları bazı hizmet yazarı tarafından açıkça uygulanan özellikleri ile ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="fbff5-114">Örneğin, meta veri değişimi uç noktası sunar <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme ancak bir hizmet olarak, yazdığınız arabirimi uygulamaz, WCF tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fbff5-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="fbff5-115">Bu tür altyapı uç noktalarına bazıları başka türlü değiştirilemez olabilir, bir veya daha fazla uç noktası özellikleri için varsayılan değerleri var.</span><span class="sxs-lookup"><span data-stu-id="fbff5-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="fbff5-116"><xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Özelliği meta veri değişimi uç olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange>, bağlama gibi diğer özellikleri, geliştirici tarafından sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="fbff5-117">Altyapı uç noktaları ayarlanarak tanımlanır <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fbff5-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="fbff5-118">Uygulama uç noktaları</span><span class="sxs-lookup"><span data-stu-id="fbff5-118">Application Endpoints</span></span>  
 <span data-ttu-id="fbff5-119">Uygulama geliştiricileri, adresi, bağlama veya sözleşme için varsayılan değerleri belirten standart, kendi uç noktalarını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbff5-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="fbff5-120">Öğesinden bir sınıf türetilerek standart uç nokta tanımladığınız <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç noktaya özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="fbff5-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="fbff5-121">Değiştirilebilir özellikler için varsayılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbff5-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="fbff5-122">Diğer bazı özellikler, değiştiremezsiniz statik değerlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="fbff5-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="fbff5-123">Aşağıdaki örnek, bir standart uç nokta uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="fbff5-124">Kullanıcı tanımlı özel uç nokta yapılandırma dosyasında kullanmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointElement>, öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>ve app.config veya machine.config uzantıları bölümünde yeni standart uç noktasını kaydetme.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç nokta için yapılandırma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbff5-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fbff5-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Yedekleme türü altında görünür koleksiyonu sağlar <`standardEndpoints`> standart bitiş noktası için yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fbff5-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="fbff5-126">Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="fbff5-127">Aşağıdaki örnek, uzantıları bölümünde bir standart uç nokta kaydetmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="fbff5-128">Standart uç nokta yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fbff5-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="fbff5-129">Standart uç noktaları, kod veya yapılandırma eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="fbff5-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="fbff5-130">Kodda bir standart uç noktası eklemek için yalnızca uygun standart uç nokta türü örneği oluşturun ve aşağıdaki örnekte gösterildiği gibi hizmet konağı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="fbff5-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="fbff5-131">Standart uç nokta yapılandırması eklemek için Ekle bir <`endpoint`> öğesi <`service`> öğesi ve tüm gerekli yapılandırma ayarlarında <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbff5-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="fbff5-132">Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, birlikte standart uç noktalardan biri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbff5-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="fbff5-133">Standart uç nokta türünü tür özniteliği kullanarak belirtilen <`endpoint`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbff5-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="fbff5-134">Uç nokta yapılandırılır <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="fbff5-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="fbff5-135">Yukarıdaki örnekte bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası eklenir ve yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="fbff5-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="fbff5-136"><`udpDiscoveryEndpoint`> Öğesi içeren bir <`standardEndpoint`> Ayarlar <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> özelliği <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="fbff5-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="fbff5-137">.NET Framework ile birlikte gelen standart uç noktaları</span><span class="sxs-lookup"><span data-stu-id="fbff5-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="fbff5-138">Aşağıdaki tablo ile birlikte gelen standart uç noktaları listeler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fbff5-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="fbff5-139">Hizmet meta verileri kullanıma sunmak için kullanılan bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="fbff5-140">Duyurunun ileti göndermek için hizmetler tarafından kullanılan bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="fbff5-141">Hizmetler tarafından bulma ileti göndermek için kullanılan bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="fbff5-142">Bulma işlemleri için bir UDP çok noktaya yayın üzerinden önceden yapılandırılmış bir standart uç nokta bağlama.</span><span class="sxs-lookup"><span data-stu-id="fbff5-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="fbff5-143">Üzerinden bir UDP bağlama Duyurunun ileti göndermek için hizmetler tarafından kullanılan bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="fbff5-144">WS-bulma uç nokta adresini çalışma zamanında dinamik olarak bulmak için kullandığı standart bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="fbff5-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="fbff5-145">Meta veri değişimi için bir standart bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="fbff5-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="fbff5-146">Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebHttpBehavior> davranışı</span><span class="sxs-lookup"><span data-stu-id="fbff5-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="fbff5-147">Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışı.</span><span class="sxs-lookup"><span data-stu-id="fbff5-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="fbff5-148">Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="fbff5-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="fbff5-149">İş akışı örnekleri denetimi işlemleri çağırmak sağlayan bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="fbff5-150">İş akışı oluşturma ve yer imi sürdürme destekleyen bir standart uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fbff5-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
