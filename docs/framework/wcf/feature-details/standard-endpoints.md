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
# <a name="standard-endpoints"></a>Standart Uç Noktaları

Uç noktalar bir adres, bağlama ve bir sözleşme belirtilerek tanımlanır. Bir uç noktada ayarlanmış olabilecek diğer parametreler, davranış yapılandırması, üst bilgiler ve dinleme URI 'Leri içerir.  Belirli uç nokta türleri için bu değerler değişmez. Örneğin, meta veri değişimi uç noktaları sözleşmeyi her zaman kullanır <xref:System.ServiceModel.Description.IMetadataExchange> . <xref:System.ServiceModel.Description.WebHttpEndpoint>Her zaman belirli bir uç nokta davranışı gerektiren diğer uç noktalar. Bir uç noktanın kullanılabilirliği, yaygın olarak kullanılan uç nokta özellikleri için varsayılan değerlere sahip uç noktalara sahip olunarak artırılabilir. Standart uç noktalar, bir geliştiricinin varsayılan değerleri olan veya bir ya da daha fazla bitiş noktası özelliklerinin değişmediğinden bir uç nokta tanımlamasını sağlar.  Bu uç noktalar, statik bir doğası bilgilerini belirtmek zorunda kalmadan böyle bir uç nokta kullanmanızı sağlar. Standart uç noktalar, altyapı ve uygulama uç noktaları için kullanılabilir.  
  
## <a name="infrastructure-endpoints"></a>Altyapı uç noktaları  

 Bir hizmet, hizmet yazarı tarafından açıkça uygulanmayan bazı özelliklerle uç noktalar açığa çıkabilir. Örneğin, meta veri değişimi uç noktası sözleşmeyi kullanıma sunar <xref:System.ServiceModel.Description.IMetadataExchange> , ancak bir hizmet yazarı olarak bu arabirimi uygulamaz, WCF tarafından uygulanır. Bu tür altyapı uç noktaları, bir veya daha fazla uç nokta özelliği için varsayılan değerlere sahiptir ve bunlardan bazıları geri alınamaz. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>Meta veri değişimi uç noktasının özelliği olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange> ; ancak bağlama gibi diğer özellikler geliştirici tarafından sağlanabilecek. Altyapı uç noktaları, <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliği olarak ayarlanarak tanımlanır `true` .  
  
## <a name="application-endpoints"></a>Uygulama uç noktaları  

 Uygulama geliştiricileri, adres, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktalarını tanımlayabilir. Bir sınıf türeterek <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç nokta özelliklerini ayarlayarak standart bir uç nokta tanımlarsınız. Değiştirilebilen özellikler için varsayılan değerler sağlayabilirsiniz. Bazı diğer özellikler, değişmeyen statik değerlere sahip olur. Aşağıdaki örnek, standart bir uç noktanın nasıl uygulanacağını gösterir.  
  
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
  
 Bir yapılandırma dosyasında Kullanıcı tanımlı özel uç nokta kullanmak için, öğesinden bir sınıf türetmeniz <xref:System.ServiceModel.Configuration.StandardEndpointElement> , öğesinden bir sınıf türetmeniz <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> ve yeni standart uç noktayı app.config veya machine.config uzantı bölümüne kaydetmeniz gerekir.  , <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç nokta için yapılandırma desteği sağlar.  
  
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
  
 , <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> `standardEndpoints` Standart uç nokta yapılandırmasındaki <> bölümü altında görüntülenen koleksiyon için yedekleme türünü sağlar.  Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Aşağıdaki örnek, uzantılar bölümünde standart bir uç noktanın nasıl kaydedileceği gösterilmektedir.

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
  
## <a name="configuring-a-standard-endpoint"></a>Standart uç nokta yapılandırma  

 Standart uç noktalar, koda veya yapılandırmaya eklenebilir.  Koda standart bir uç nokta eklemek için, uygun standart uç nokta türünü örnek olarak oluşturmanız ve aşağıdaki örnekte gösterildiği gibi hizmet ana bilgisayarına eklemeniz yeterlidir:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Yapılandırmaya standart bir uç nokta eklemek için, `endpoint` <`service`> öğesine ve gerekli yapılandırma ayarlarına <> öğesinde bir <> öğesi ekleyin `standardEndpoints` . Aşağıdaki örnek <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> , ile birlikte gelen standart uç noktalardan birini nasıl ekleneceğini gösterir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .  
  
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
  
 Standart uç nokta türü, <> öğesindeki Kind özniteliği kullanılarak belirtilir `endpoint` . Uç nokta <> öğesi içinde yapılandırılır `standardEndpoints` . Yukarıdaki örnekte, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç nokta eklenir ve yapılandırılır. <`udpDiscoveryEndpoint`> öğesi `standardEndpoint` , öğesinin özelliğini ayarlayan bir <> içerir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> .  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>.NET Framework birlikte gönderilen standart uç noktalar  

 Aşağıdaki tabloda ile birlikte gelen standart uç noktalar listelenmiştir [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .  
  
 `Mex Endpoint`  
 Hizmet meta verilerini açığa çıkarmak için kullanılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Hizmetler tarafından duyuru iletileri göndermek için kullanılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Bulma iletilerini göndermek için hizmetler tarafından kullanılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Bir UDP çok noktaya yayın bağlaması üzerinde bulma işlemleri için önceden yapılandırılmış standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Hizmetler tarafından bir UDP bağlaması üzerinden duyuru iletileri göndermek için kullanılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Çalışma zamanında dinamik olarak uç nokta adresini bulmak için WS-Discovery kullanan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Meta veri değişimi için standart bir uç nokta.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.WebHttpBinding>Otomatik olarak davranışını ekleyen bağlama içeren standart bir uç nokta <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.WebHttpBinding>Davranışı otomatik olarak ekleyen bağlama içeren standart bir uç nokta <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> .  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Bağlama içeren standart bir uç nokta <xref:System.ServiceModel.WebHttpBinding> .  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 İş akışı örneklerinde denetim işlemlerini çağırmanızı sağlayan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 İş akışı oluşturmayı ve sürdürme yer işaretini destekleyen standart bir uç nokta.
