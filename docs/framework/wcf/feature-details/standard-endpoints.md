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
# <a name="standard-endpoints"></a>Standart Uç Noktaları
Uç noktalar bir adres, bir bağlama ve sözleşme belirtilerek tanımlanır. Bitiş noktasına ayarlanabilecek diğer parametreler davranış yapılandırması, üstbilgi ve dinleme URI'lerini içerir.  Belirli uç nokta türleri için bu değerler değişmez. Örneğin, meta veri alışverişi uç <xref:System.ServiceModel.Description.IMetadataExchange> noktaları her zaman sözleşmeyi kullanır. Her zaman belirtilen <xref:System.ServiceModel.Description.WebHttpEndpoint> bir bitiş noktası davranışı gerektiren gibi diğer uç noktalar. Bir uç noktanın kullanılabilirliği, sık kullanılan uç nokta özellikleri için varsayılan değerlere sahip uç noktalarına sahip olarak geliştirilebilir. Standart uç noktalar, bir geliştiricinin varsayılan değerlere sahip veya bir veya daha fazla uç noktanın özelliklerinin değişmediği bir uç nokta tanımlamasını sağlar.  Bu uç noktalar, statik bir niteen bilgi belirtmek zorunda kalmadan böyle bir bitiş noktası kullanmanıza olanak sağlar. Standart uç noktaları altyapı ve uygulama uç noktaları için kullanılabilir.  
  
## <a name="infrastructure-endpoints"></a>Altyapı Uç Noktaları  
 Bir hizmet, hizmet yazarı tarafından açıkça uygulanmayan bazı özellikleri olan uç noktalarını ortaya çıkarabilir. Örneğin, meta veri değişimi bitiş noktası <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi ortaya çıkarır, ancak bir hizmet yazarı olarak bu arabirimi uygulamazsanız, WCF tarafından uygulanır. Bu tür altyapı uç noktaları, bazıları değiştirilemez olabilecek bir veya daha fazla uç nokta özelliği için varsayılan değerlere sahiptir. Meta <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> veri alışverişi bitiş noktasının <xref:System.ServiceModel.Description.IMetadataExchange>özelliği, bağlama gibi diğer özellikler geliştirici tarafından sağlanabilirken olmalıdır. Altyapı uç noktaları <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliği ' `true`ne ayarlayarak tanımlanır.  
  
## <a name="application-endpoints"></a>Uygulama Bitiş Noktaları  
 Uygulama geliştiricileri, adres, bağlama veya sözleşme için varsayılan değerleri belirten kendi standart uç noktalarını tanımlayabilir. Bir sınıfı türeterek <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç nokta özelliklerini ayarlayarak standart bir bitiş noktası tanımlarsınız. Değiştirilebilen özellikler için varsayılan değerler sağlayabilirsiniz. Diğer bazı özellikleri değiştirilemez statik değerlere sahip olacaktır. Aşağıdaki örnek, standart bir bitiş noktasının nasıl uygulanacağını gösterir.  
  
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
  
 Yapılandırma dosyasında kullanıcı tanımlı özel bitiş noktası kullanmak için <xref:System.ServiceModel.Configuration.StandardEndpointElement>bir sınıf türetmeniz, bir sınıf <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>türetmeniz ve app.config veya machine.config'deki uzantılar bölümündeyeni standart bitiş noktasını kaydetmeniz gerekir.  Aşağıdaki <xref:System.ServiceModel.Configuration.StandardEndpointElement> örnekte gösterildiği gibi, standart bitiş noktası için yapılandırma desteği sağlar.  
  
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
  
 Standart <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> bitiş noktası için yapılandırmada <`standardEndpoints`> bölümünün altında görünen koleksiyon için destek türünü sağlar.  Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Aşağıdaki örnek, uzantılar bölümünde standart bir bitiş noktasının nasıl kaydedilebildiğini gösterir.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Standart Bitiş Noktası Nı Yapılandırma  
 Standart uç noktalar kodda veya yapılandırmada eklenebilir.  Koda standart bir bitiş noktası eklemek için uygun standart uç nokta türünü anında anında anlamanız ve aşağıdaki örnekte gösterildiği gibi servis ana lığına eklemeniz yeterlidir:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Yapılandırmada standart bir bitiş noktası eklemek `endpoint` için, <`service`> öğesine ve <`standardEndpoints`> öğesinde gerekli yapılandırma ayarlarına <bir> öğesi ekleyin. Aşağıdaki örnek, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, bir , standart uç noktalardan biri ile gemi nasıl ekler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]gösterir.  
  
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
  
 Standart bitiş noktası türü, <`endpoint`> öğesindeki tür özniteliği kullanılarak belirtilir. Bitiş noktası <`standardEndpoints`> öğesi içinde yapılandırılır. Yukarıdaki örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> bir bitiş noktası eklenir ve yapılandırılır. <`udpDiscoveryEndpoint`> öğesi, `standardEndpoint` <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>'nin özelliğini ayarlayan <bir> içerir.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>.NET Çerçevesi ile Gönderilen Standart Uç Noktaları  
 Aşağıdaki tabloda, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]'ile gönderilen standart uç noktaları listele  
  
 `Mex Endpoint`  
 Hizmet meta verilerini ortaya çıkarmak için kullanılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Bulma iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 UDP çok noktaya yayın bağlama üzerinden bulma işlemleri için önceden yapılandırılan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Bir UDP bağlama üzerinden duyuru iletileri göndermek için hizmetler tarafından kullanılan standart bir bitiş noktası.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 Çalışma zamanında bitiş noktası adresini dinamik olarak bulmak için WS-Discovery kullanan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Meta veri alışverişi için standart bir bitiş noktası.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Davranışı otomatik olarak <xref:System.ServiceModel.WebHttpBinding> ekleyen bir bağlama <xref:System.ServiceModel.Description.WebHttpBehavior> içeren standart bir bitiş noktası  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Davranışı otomatik olarak <xref:System.ServiceModel.WebHttpBinding> ekleyen bağlayıcılı standart bir bitiş noktası. <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Bağlamalı standart bir <xref:System.ServiceModel.WebHttpBinding> bitiş noktası.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 İş akışı örneklerinde denetim işlemlerini aramanızı sağlayan standart bir uç nokta.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 İş akışı oluşturmayı ve yer imi yeniden başlatılmasını destekleyen standart bir bitiş noktası.
