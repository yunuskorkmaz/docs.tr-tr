---
title: Standart Uç Noktaları
ms.date: 03/30/2017
ms.assetid: 3fcb4225-addc-44f2-935d-30e4943a8812
ms.openlocfilehash: 395d910ddabc553cca47dcdd038f44b1470b3455
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="standard-endpoints"></a>Standart Uç Noktaları
Uç noktaları bir adresi, bağlama ve bir sözleşme belirterek tanımlanır. Bir noktadaki ayarlanabilir diğer parametreler URI'ler dinleme ve davranış yapılandırmasını, üstbilgiler, içerir.  Belirli uç noktaları türleri bu değerleri değiştirmeyin. Örneğin, meta veri exchange uç noktalarını her zaman kullanın <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme. Diğer uç noktaları gibi <xref:System.ServiceModel.Description.WebHttpEndpoint> her zaman bir belirtilen uç nokta davranışını gerektirir. Bir uç nokta kullanılabilirliğini uç ile sık kullanılan endpoint özelliklerinin varsayılan değerlerini sağlayarak geliştirilebilir. Standart uç noktaları varsayılan değerlerine sahip bir uç nokta tanımlamak bir geliştirici etkinleştirmek veya burada bir veya daha fazla uç noktanın özellikleri değiştirmez.  Bu uç noktaları gibi bir uç nokta statik yapısı bilgilerinin belirtmek zorunda kalmadan kullanmanızı sağlar. Standart uç noktaları için altyapı ve uygulama uç noktaları kullanılabilir.  
  
## <a name="infrastructure-endpoints"></a>Altyapı uç noktaları  
 Bir hizmet uç noktaları bazı açıkça hizmet yazar tarafından uygulanan özellikler getirebilir. Örneğin, meta verileri exchange endpoint sunan <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme ancak bir hizmet olarak yazar arabirimi uygulamaz, WCF tarafından uygulanır. Bu tür altyapı uç noktaları bazıları türlü değiştirilemez olabilir, bir veya daha fazla uç noktası özellikleri için varsayılan değerler atanmıştır. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Meta verileri exchange uç noktasının özelliği olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange>, bağlama gibi başka özellikler geliştirici tarafından sağlanabilir. Altyapı uç noktaları ayarlanarak tanımlanır <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliğine `true`.  
  
## <a name="application-endpoints"></a>Uygulama uç noktaları  
 Uygulama geliştiricilerinin adresi, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktaları tanımlayabilirsiniz. Öğesinden bir sınıf türetme tarafından standart bir uç noktasını tanımlamanız <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç noktası özelliklerini ayarlama. Değiştirilebilir özellikler için varsayılan değerleri sağlayabilir. Diğer bazı özellikler değiştiremezsiniz statik değerlere sahip olur. Aşağıdaki örnek, standart bir uç nokta uygulamak gösterilmiştir.  
  
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
  
 Bir kullanıcı tanımlı özel uç noktası bir yapılandırma dosyasında kullanılacak öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointElement>, öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>ve app.config veya machine.config uzantıları bölümünde yeni standart uç noktasını Kaydet.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç noktası için yapılandırma desteği sağlar.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Altında görünür koleksiyonu sağlayan yedekleme türü <`standardEndpoints`> standart uç noktası için yapılandırma bölümünde.  Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Aşağıdaki örnek uzantıları bölümünde standart bir uç noktasını kaydetmek nasıl gösterir.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Standart bir uç noktası yapılandırma  
 Standart uç noktaları, kod veya yapılandırma eklenebilir.  Kodda standart bir uç noktası eklemek için yalnızca uygun standart uç nokta türü örneği ve hizmet ana bilgisayarı için aşağıdaki örnekte gösterildiği gibi ekleyin:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Standart bir uç nokta yapılandırması eklemek için Ekle bir <`endpoint`> öğesi <`service`> öğesi ve tüm gerekli yapılandırma ayarlarını <`standardEndpoints`> öğesi. Aşağıdaki örnekte nasıl ekleneceğini gösterir bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, birlikte standart uç noktalardan biri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Standart uç nokta türü tür özniteliğini kullanarak belirtilen <`endpoint`> öğesi. Uç nokta içinde yapılandırılmış <`standardEndpoints`> öğesi. Yukarıdaki örnekte bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç nokta eklenir ve yapılandırılmış. <`udpDiscoveryEndpoint`> Öğesi içeren bir <`standardEndpoint`> ayarlayan <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> özelliği <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>.NET Framework ile birlikte gelen standart uç noktaları  
 Aşağıdaki tablo ile birlikte gelen standart uç noktaları listeler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Hizmet meta verilerini kullanıma sunmak için kullanılan bir standart uç noktası.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç noktası.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Hizmetler tarafından bulma iletileri göndermek için kullanılan bir standart uç noktası.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Bulma işlemleri için çok noktaya yayın UDP üzerinden bir önceden yapılandırılmış standart bir uç nokta bağlama.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 UDP bağlama üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan bir standart uç noktası.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Uç nokta adresi çalışma zamanında dinamik olarak bulmak için WS-bulma kullandığı bir standart uç noktası.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Meta veri değişimi standart uç noktası.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebHttpBehavior> davranışı  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışı.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Standart bir uç noktası ile bir <xref:System.ServiceModel.WebHttpBinding> bağlama.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 İş akışı örnekleri üzerinde denetim işlemlerini çağırma olanak tanıyan bir standart uç noktası.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 İş akışı oluşturma ve yer işareti sürdürme destekleyen bir standart uç noktası.
