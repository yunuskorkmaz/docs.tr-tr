---
title: "Standart Uç Noktaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de5f1c858b9018071489354441cab197bf5db6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="standard-endpoints"></a><span data-ttu-id="c4e25-102">Standart Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="c4e25-102">Standard Endpoints</span></span>
<span data-ttu-id="c4e25-103">Uç noktaları bir adresi, bağlama ve bir sözleşme belirterek tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c4e25-103">Endpoints are defined by specifying an address, a binding, and a contract.</span></span> <span data-ttu-id="c4e25-104">Bir noktadaki ayarlanabilir diğer parametreler URI'ler dinleme ve davranış yapılandırmasını, üstbilgiler, içerir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-104">Other parameters that may be set on an endpoint include behavior configuration, headers, and listen URIs.</span></span>  <span data-ttu-id="c4e25-105">Belirli uç noktaları türleri bu değerleri değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="c4e25-105">For certain types of endpoints these values do not change.</span></span> <span data-ttu-id="c4e25-106">Örneğin, meta veri exchange uç noktalarını her zaman kullanın <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme.</span><span class="sxs-lookup"><span data-stu-id="c4e25-106">For example, metadata exchange endpoints always use the <xref:System.ServiceModel.Description.IMetadataExchange> contract.</span></span> <span data-ttu-id="c4e25-107">Diğer uç noktaları gibi <xref:System.ServiceModel.Description.WebHttpEndpoint> her zaman bir belirtilen uç nokta davranışını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-107">Other endpoints, such as <xref:System.ServiceModel.Description.WebHttpEndpoint> always require a specified endpoint behavior.</span></span> <span data-ttu-id="c4e25-108">Bir uç nokta kullanılabilirliğini uç ile sık kullanılan endpoint özelliklerinin varsayılan değerlerini sağlayarak geliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-108">The usability of an endpoint can be improved by having endpoints with default values for commonly used endpoint properties.</span></span> <span data-ttu-id="c4e25-109">Standart uç noktaları varsayılan değerlerine sahip bir uç nokta tanımlamak bir geliştirici etkinleştirmek veya burada bir veya daha fazla uç noktanın özellikleri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c4e25-109">Standard endpoints enable a developer to define an endpoint that has default values or where one or more endpoint’s properties does not change.</span></span>  <span data-ttu-id="c4e25-110">Bu uç noktaları gibi bir uç nokta statik yapısı bilgilerinin belirtmek zorunda kalmadan kullanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e25-110">These endpoints allow you to use such an endpoint without having to specify information of a static nature.</span></span> <span data-ttu-id="c4e25-111">Standart uç noktaları için altyapı ve uygulama uç noktaları kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-111">Standard endpoints can be used for infrastructure and application endpoints.</span></span>  
  
## <a name="infrastructure-endpoints"></a><span data-ttu-id="c4e25-112">Altyapı uç noktaları</span><span class="sxs-lookup"><span data-stu-id="c4e25-112">Infrastructure Endpoints</span></span>  
 <span data-ttu-id="c4e25-113">Bir hizmet uç noktaları bazı açıkça hizmet yazar tarafından uygulanan özellikler getirebilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-113">A service may expose endpoints with some of the properties not explicitly implemented by the service author.</span></span> <span data-ttu-id="c4e25-114">Örneğin, meta verileri exchange endpoint sunan <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme ancak bir hizmet olarak yazar arabirimi uygulamaz, WCF tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c4e25-114">For example, the metadata exchange endpoint exposes the <xref:System.ServiceModel.Description.IMetadataExchange> contract but as a service author you do not implement that interface, it is implemented by WCF.</span></span> <span data-ttu-id="c4e25-115">Bu tür altyapı uç noktaları bazıları türlü değiştirilemez olabilir, bir veya daha fazla uç noktası özellikleri için varsayılan değerler atanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c4e25-115">Such infrastructure endpoints have default values for one or more endpoint properties, some of which may be unalterable.</span></span> <span data-ttu-id="c4e25-116"><xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Meta verileri exchange uç noktasının özelliği olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange>, bağlama gibi başka özellikler geliştirici tarafından sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-116">The <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> property of the metadata exchange endpoint must be <xref:System.ServiceModel.Description.IMetadataExchange>, while other properties like binding can be supplied by the developer.</span></span> <span data-ttu-id="c4e25-117">Altyapı uç noktaları ayarlanarak tanımlanır <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliğine `true`.</span><span class="sxs-lookup"><span data-stu-id="c4e25-117">Infrastructure endpoints are identified by setting the <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> property to `true`.</span></span>  
  
## <a name="application-endpoints"></a><span data-ttu-id="c4e25-118">Uygulama uç noktaları</span><span class="sxs-lookup"><span data-stu-id="c4e25-118">Application Endpoints</span></span>  
 <span data-ttu-id="c4e25-119">Uygulama geliştiricilerinin adresi, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4e25-119">Application developers can define their own standard endpoints which specify default values for the address, binding, or contract.</span></span> <span data-ttu-id="c4e25-120">Öğesinden bir sınıf türetme tarafından standart bir uç noktasını tanımlamanız <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç noktası özelliklerini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="c4e25-120">You define a standard endpoint by deriving a class from <xref:System.ServiceModel.Description.ServiceEndpoint> and setting the appropriate endpoint properties.</span></span> <span data-ttu-id="c4e25-121">Değiştirilebilir özellikler için varsayılan değerleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-121">You can provide default values for properties that can be changed.</span></span> <span data-ttu-id="c4e25-122">Diğer bazı özellikler değiştiremezsiniz statik değerlere sahip olur.</span><span class="sxs-lookup"><span data-stu-id="c4e25-122">Some other properties will have static values that cannot change.</span></span> <span data-ttu-id="c4e25-123">Aşağıdaki örnek, standart bir uç nokta uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-123">The following example shows how to implement a standard endpoint.</span></span>  
  
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
  
 <span data-ttu-id="c4e25-124">Bir kullanıcı tanımlı özel uç noktası bir yapılandırma dosyasında kullanılacak öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointElement>, öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>ve app.config veya machine.config uzantıları bölümünde yeni standart uç noktasını Kaydet.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç noktası için yapılandırma desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4e25-124">To use a user-defined custom endpoint in a configuration file you must derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointElement>, derive a class from <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>, and register the new standard endpoint in the extensions section in app.config or machine.config.  The <xref:System.ServiceModel.Configuration.StandardEndpointElement> provides configuration support for the standard endpoint, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c4e25-125"><xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Altında görünür koleksiyonu sağlayan yedekleme türü <`standardEndpoints`> standart uç noktası için yapılandırma bölümünde.</span><span class="sxs-lookup"><span data-stu-id="c4e25-125">The <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> provides the backing type for the collection that appears under the <`standardEndpoints`> section in the configuration for the standard endpoint.</span></span>  <span data-ttu-id="c4e25-126">Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-126">The following example shows how to implement this class.</span></span>  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

<span data-ttu-id="c4e25-127">Aşağıdaki örnek uzantıları bölümünde standart bir uç noktasını kaydetmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-127">The following example shows how to register a standard endpoint in the extensions section.</span></span>

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a><span data-ttu-id="c4e25-128">Standart bir uç noktası yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4e25-128">Configuring a Standard Endpoint</span></span>  
 <span data-ttu-id="c4e25-129">Standart uç noktaları, kod veya yapılandırma eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c4e25-129">Standard endpoints can be added in code or in configuration.</span></span>  <span data-ttu-id="c4e25-130">Kodda standart bir uç noktası eklemek için yalnızca uygun standart uç nokta türü örneği ve hizmet ana bilgisayarı için aşağıdaki örnekte gösterildiği gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c4e25-130">To add a standard endpoint in code simply instantiate the appropriate standard endpoint type and add it to the service host as shown in the following example:</span></span>  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 <span data-ttu-id="c4e25-131">Standart bir uç nokta yapılandırması eklemek için Ekle bir <`endpoint`> öğesi <`service`> öğesi ve tüm gerekli yapılandırma ayarlarını <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4e25-131">To add a standard endpoint in configuration, add an <`endpoint`> element to the <`service`> element and any needed configuration settings in the <`standardEndpoints`> element.</span></span> <span data-ttu-id="c4e25-132">Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, birlikte standart uç noktalardan biri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4e25-132">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, one of the standard endpoints that ships with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
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
  
 <span data-ttu-id="c4e25-133">Standart uç nokta türü tür özniteliğini kullanarak belirtilen <`endpoint`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4e25-133">The type of standard endpoint is specified using the kind attribute in the <`endpoint`> element.</span></span> <span data-ttu-id="c4e25-134">Uç nokta içinde yapılandırılmış <`standardEndpoints`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4e25-134">The endpoint is configured within the <`standardEndpoints`> element.</span></span> <span data-ttu-id="c4e25-135">Yukarıdaki örnekte bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç nokta eklenir ve yapılandırılmış.</span><span class="sxs-lookup"><span data-stu-id="c4e25-135">In the example above, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint is added and configured.</span></span> <span data-ttu-id="c4e25-136"><`udpDiscoveryEndpoint`> Öğesi içeren bir <`standardEndpoint`> ayarlayan <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> özelliği <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="c4e25-136">The <`udpDiscoveryEndpoint`> element contains a <`standardEndpoint`> that sets the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> property of the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a><span data-ttu-id="c4e25-137">.NET Framework ile birlikte gelen standart uç noktaları</span><span class="sxs-lookup"><span data-stu-id="c4e25-137">Standard Endpoints Shipped with the .NET Framework</span></span>  
 <span data-ttu-id="c4e25-138">Aşağıdaki tablo ile birlikte gelen standart uç noktaları listeler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c4e25-138">The following table lists the standard endpoints shipped with [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 `Mex Endpoint`  
 <span data-ttu-id="c4e25-139">Hizmet meta verilerini kullanıma sunmak için kullanılan bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-139">A standard endpoint that is used to expose service metadata.</span></span>  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 <span data-ttu-id="c4e25-140">Duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-140">A standard endpoint that is used by services to send announcement messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 <span data-ttu-id="c4e25-141">Hizmetler tarafından bulma iletileri göndermek için kullanılan bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-141">A standard endpoint that is used by services to send discovery messages.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 <span data-ttu-id="c4e25-142">Bulma işlemleri için çok noktaya yayın UDP üzerinden bir önceden yapılandırılmış standart bir uç nokta bağlama.</span><span class="sxs-lookup"><span data-stu-id="c4e25-142">A standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 <span data-ttu-id="c4e25-143">UDP bağlama üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-143">A standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span>  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <span data-ttu-id="c4e25-144">Uç nokta adresi çalışma zamanında dinamik olarak bulmak için WS-bulma kullandığı bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-144">A standard endpoint that uses WS-Discovery to find the endpoint address dynamically at runtime.</span></span>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 <span data-ttu-id="c4e25-145">Meta veri değişimi standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-145">A standard endpoint for metadata exchange.</span></span>  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <span data-ttu-id="c4e25-146">Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebHttpBehavior> davranışı</span><span class="sxs-lookup"><span data-stu-id="c4e25-146">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebHttpBehavior> behavior</span></span>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <span data-ttu-id="c4e25-147">Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışı.</span><span class="sxs-lookup"><span data-stu-id="c4e25-147">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding that automatically adds the <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> behavior.</span></span>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 <span data-ttu-id="c4e25-148">Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> bağlama.</span><span class="sxs-lookup"><span data-stu-id="c4e25-148">A standard endpoint with a <xref:System.ServiceModel.WebHttpBinding> binding.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 <span data-ttu-id="c4e25-149">İş akışı örnekleri üzerinde denetim işlemlerini çağırma olanak tanıyan bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-149">A standard endpoint that enables you to call control operations on workflow instances.</span></span>  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 <span data-ttu-id="c4e25-150">İş akışı oluşturma ve yer işareti sürdürme destekleyen bir standart uç noktası.</span><span class="sxs-lookup"><span data-stu-id="c4e25-150">A standard endpoint that supports workflow creation and bookmark resumption.</span></span>
