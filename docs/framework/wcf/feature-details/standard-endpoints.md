---
title: Standart Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 880601664d7602e279c5d022fa37c44914a58772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184400"
---
# <a name="standard-endpoints"></a><span data-ttu-id="ec3fd-102">Standart Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="ec3fd-102">Standard Endpoints</span></span>
<span data-ttu-id="ec3fd-103">Uç noktalar bir adres, bir bağlama ve sözleşme belirtilerek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="ec3fd-104">Bitiş noktasına ayarlanabilecek diğer parametreler davranış yapılandırması, üstbilgi ve dinleme URI'lerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="ec3fd-105">Belirli uç nokta türleri için bu değerler değişmez.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="ec3fd-106">Örneğin, meta veri alışverişi uç <xref:System.ServiceModel.Description.IMetadataExchange> noktaları her zaman sözleşmeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="ec3fd-107">Her zaman belirtilen <xref:System.ServiceModel.Description.WebHttpEndpoint> bir bitiş noktası davranışı gerektiren gibi diğer uç noktalar.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="ec3fd-108">Bir uç noktanın kullanılabilirliği, sık kullanılan uç nokta özellikleri için varsayılan değerlere sahip uç noktalarına sahip olarak geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="ec3fd-109">Standart uç noktalar, bir geliştiricinin varsayılan değerlere sahip veya bir veya daha fazla uç noktanın özelliklerinin değişmediği bir uç nokta tanımlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="ec3fd-110">Bu uç noktalar, statik bir niteen bilgi belirtmek zorunda kalmadan böyle bir bitiş noktası kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="ec3fd-111">Standart uç noktaları altyapı ve uygulama uç noktaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="ec3fd-112">Altyapı Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="ec3fd-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="ec3fd-113">Bir hizmet, hizmet yazarı tarafından açıkça uygulanmayan bazı özellikleri olan uç noktalarını ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="ec3fd-114">Örneğin, meta veri değişimi bitiş noktası <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi ortaya çıkarır, ancak bir hizmet yazarı olarak bu arabirimi uygulamazsanız, WCF tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="ec3fd-115">Bu tür altyapı uç noktaları, bazıları değiştirilemez olabilecek bir veya daha fazla uç nokta özelliği için varsayılan değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="ec3fd-116">Meta <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> veri alışverişi bitiş noktasının <xref:System.ServiceModel.Description.IMetadataExchange>özelliği, bağlama gibi diğer özellikler geliştirici tarafından sağlanabilirken olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="ec3fd-117">Altyapı uç noktaları <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliği ' `true`ne ayarlayarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="ec3fd-118">Uygulama Bitiş Noktaları</span><span class="sxs-lookup"><span data-stu-id="ec3fd-118">Application Endpoints</span></span>  
 <span data-ttu-id="ec3fd-119">Uygulama geliştiricileri, adres, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktalarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="ec3fd-120">Bir sınıfı türeterek <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç nokta özelliklerini ayarlayarak standart bir bitiş noktası tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="ec3fd-121">Değiştirilebilen özellikler için varsayılan değerler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="ec3fd-122">Diğer bazı özellikleri değiştirilemez statik değerlere sahip olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="ec3fd-123">Aşağıdaki örnek, standart bir bitiş noktasının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="ec3fd-124">Yapılandırma dosyasında kullanıcı tanımlı özel bitiş noktası kullanmak için <xref:System.ServiceModel.Configuration.StandardEndpointElement>bir sınıf türetmeniz, bir sınıf <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>türetmeniz ve app.config veya machine.config'deki uzantılar bölümündeyeni standart bitiş noktasını kaydetmeniz gerekir.  Aşağıdaki <xref:System.ServiceModel.Configuration.StandardEndpointElement> örnekte gösterildiği gibi, standart bitiş noktası için yapılandırma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ec3fd-125">Standart <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> bitiş noktası için yapılandırmada <`standardEndpoints`> bölümünün altında görünen koleksiyon için destek türünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="ec3fd-126">Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="ec3fd-127">Aşağıdaki örnek, uzantılar bölümünde standart bir bitiş noktasının nasıl kaydedilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="ec3fd-128">Standart Bitiş Noktası Nı Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec3fd-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="ec3fd-129">Standart uç noktalar kodda veya yapılandırmada eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="ec3fd-130">Koda standart bir bitiş noktası eklemek için uygun standart uç nokta türünü anında anında anlamanız ve aşağıdaki örnekte gösterildiği gibi servis ana lığına eklemeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="ec3fd-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="ec3fd-131">Yapılandırmada standart bir bitiş noktası eklemek `endpoint` için, <`service`> öğesine ve <`standardEndpoints`> öğesinde gerekli yapılandırma ayarlarına <bir> öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="ec3fd-132">Aşağıdaki örnek, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, bir , standart uç noktalardan biri ile gemi nasıl ekler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="ec3fd-133">Standart bitiş noktası türü, <`endpoint`> öğesindeki tür özniteliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="ec3fd-134">Bitiş noktası <`standardEndpoints`> öğesi içinde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="ec3fd-135">Yukarıdaki örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> bir bitiş noktası eklenir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="ec3fd-136"><`udpDiscoveryEndpoint`> öğesi, `standardEndpoint` <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>'nin özelliğini ayarlayan <bir> içerir.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="ec3fd-137">.NET Çerçevesi ile Gönderilen Standart Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="ec3fd-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="ec3fd-138">Aşağıdaki tabloda, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]'ile gönderilen standart uç noktaları listele</span><span class="sxs-lookup"><span data-stu-id="ec3fd-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="ec3fd-139">Hizmet meta verilerini ortaya çıkarmak için kullanılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="ec3fd-140">Duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="ec3fd-141">Bulma iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="ec3fd-142">UDP çok noktaya yayın bağlama üzerinden bulma işlemleri için önceden yapılandırılan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="ec3fd-143">Bir UDP bağlama üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="ec3fd-144">Çalışma zamanında bitiş noktası adresini dinamik olarak bulmak için WS-Discovery kullanan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="ec3fd-145">Meta veri alışverişi için standart bir bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="ec3fd-146">Davranışı otomatik olarak <xref:System.ServiceModel.WebHttpBinding> ekleyen bir bağlama <xref:System.ServiceModel.Description.WebHttpBehavior> içeren standart bir bitiş noktası</span><span class="sxs-lookup"><span data-stu-id="ec3fd-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="ec3fd-147">Davranışı otomatik olarak <xref:System.ServiceModel.WebHttpBinding> ekleyen bağlayıcılı standart bir bitiş noktası. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior></span><span class="sxs-lookup"><span data-stu-id="ec3fd-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="ec3fd-148">Bağlamalı standart bir <xref:System.ServiceModel.WebHttpBinding> bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="ec3fd-149">İş akışı örneklerinde denetim işlemlerini aramanızı sağlayan standart bir uç nokta.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="ec3fd-150">İş akışı oluşturmayı ve yer imi yeniden başlatılmasını destekleyen standart bir bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ec3fd-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
