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
# <a name="standard-endpoints"></a>Standart Uç Noktaları
Uç noktaları bir adresi, bağlama ve bir sözleşme belirterek tanımlanır. Bir uç nokta üzerinde ayarlanabilir diğer parametreler URI'ler dinlemek ve daha davranışı yapılandırmasına, üstbilgiler, içerir.  Belirli türde uç noktalar, bu değerleri değiştirmeyin. Örneğin, meta veri değişimi uç noktalar her zaman kullan <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme. Diğer uç noktalardan gibi <xref:System.ServiceModel.Description.WebHttpEndpoint> her zaman bir belirtilen uç nokta davranışı gerektirir. Bir uç noktanın kullanılabilirliğini uç noktaları için yaygın olarak kullanılan uç noktası özellikleri varsayılan değerlerle sağlayarak geliştirilebilir. Standart uç noktalarının etkinleştirilmesi varsayılan değerlerine sahip bir uç noktayı tanımlamak bir geliştirici ya da burada bir veya daha fazla uç noktasının özelliklerini değiştirmez.  Bu uç noktaları, statik yapısı bilgileri belirtmenize gerek kalmadan bu tür, bir uç noktası kullan olanak tanır. Standart uç noktaları, altyapı ve uygulama uç noktaları için kullanılabilir.  
  
## <a name="infrastructure-endpoints"></a>Altyapı uç noktaları  
 Bir hizmet uç noktaları bazı hizmet yazarı tarafından açıkça uygulanan özellikleri ile ortaya çıkarabilir. Örneğin, meta veri değişimi uç noktası sunar <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme ancak bir hizmet olarak, yazdığınız arabirimi uygulamaz, WCF tarafından uygulanır. Bu tür altyapı uç noktalarına bazıları başka türlü değiştirilemez olabilir, bir veya daha fazla uç noktası özellikleri için varsayılan değerleri var. <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A> Özelliği meta veri değişimi uç olmalıdır <xref:System.ServiceModel.Description.IMetadataExchange>, bağlama gibi diğer özellikleri, geliştirici tarafından sağlanabilir. Altyapı uç noktaları ayarlanarak tanımlanır <xref:System.ServiceModel.Description.ServiceEndpoint.IsSystemEndpoint%2A> özelliğini `true`.  
  
## <a name="application-endpoints"></a>Uygulama uç noktaları  
 Uygulama geliştiricileri, adresi, bağlama veya sözleşme için varsayılan değerleri belirten standart, kendi uç noktalarını tanımlayabilirsiniz. Öğesinden bir sınıf türetilerek standart uç nokta tanımladığınız <xref:System.ServiceModel.Description.ServiceEndpoint> ve uygun uç noktaya özelliklerini ayarlama. Değiştirilebilir özellikler için varsayılan değerleri sağlar. Diğer bazı özellikler, değiştiremezsiniz statik değerlere sahip olur. Aşağıdaki örnek, bir standart uç nokta uygulamak gösterilmektedir.  
  
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
  
 Kullanıcı tanımlı özel uç nokta yapılandırma dosyasında kullanmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointElement>, öğesinden bir sınıf türetin <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602>ve app.config veya machine.config uzantıları bölümünde yeni standart uç noktasını kaydetme.  <xref:System.ServiceModel.Configuration.StandardEndpointElement> Aşağıdaki örnekte gösterildiği gibi standart uç nokta için yapılandırma desteği sağlar.  
  
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
  
 <xref:System.ServiceModel.Configuration.StandardEndpointCollectionElement%602> Yedekleme türü altında görünür koleksiyonu sağlar <`standardEndpoints`> standart bitiş noktası için yapılandırma bölümü.  Aşağıdaki örnek, bu sınıfın nasıl uygulanacağını gösterir.  
  
```csharp
public class CustomEndpointCollectionElement : StandardEndpointCollectionElement<CustomEndpoint, CustomEndpointElement>
{
    // ...
}
```

Aşağıdaki örnek, uzantıları bölümünde bir standart uç nokta kaydetmek gösterilmektedir.

```xml  
<extensions>  
      <standardEndpointExtensions>  
        <add  
          name="customStandardEndpoint"  
          type="CustomEndpointCollectionElement, Example.dll,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
```  
  
## <a name="configuring-a-standard-endpoint"></a>Standart uç nokta yapılandırma  
 Standart uç noktaları, kod veya yapılandırma eklenebilir.  Kodda bir standart uç noktası eklemek için yalnızca uygun standart uç nokta türü örneği oluşturun ve aşağıdaki örnekte gösterildiği gibi hizmet konağı ekleyin:  
  
```csharp  
serviceHost.AddServiceEndpoint(new CustomEndpoint());  
```  
  
 Standart uç nokta yapılandırması eklemek için Ekle bir <`endpoint`> öğesi <`service`> öğesi ve tüm gerekli yapılandırma ayarlarında <`standardEndpoints`> öğesi. Aşağıdaki örnek nasıl ekleneceğini gösterir. bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, birlikte standart uç noktalardan biri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
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
  
 Standart uç nokta türünü tür özniteliği kullanarak belirtilen <`endpoint`> öğesi. Uç nokta yapılandırılır <`standardEndpoints`> öğesi. Yukarıdaki örnekte bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> uç noktası eklenir ve yapılandırılmış. <`udpDiscoveryEndpoint`> Öğesi içeren bir <`standardEndpoint`> Ayarlar <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.MulticastAddress%2A> özelliği <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
## <a name="standard-endpoints-shipped-with-the-net-framework"></a>.NET Framework ile birlikte gelen standart uç noktaları  
 Aşağıdaki tablo ile birlikte gelen standart uç noktaları listeler [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
 `Mex Endpoint`  
 Hizmet meta verileri kullanıma sunmak için kullanılan bir standart uç nokta.  
  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
 Duyurunun ileti göndermek için hizmetler tarafından kullanılan bir standart uç nokta.  
  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
 Hizmetler tarafından bulma ileti göndermek için kullanılan bir standart uç nokta.  
  
 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
 Bulma işlemleri için bir UDP çok noktaya yayın üzerinden önceden yapılandırılmış bir standart uç nokta bağlama.  
  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
 Üzerinden bir UDP bağlama Duyurunun ileti göndermek için hizmetler tarafından kullanılan bir standart uç nokta.  
  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 WS-bulma uç nokta adresini çalışma zamanında dinamik olarak bulmak için kullandığı standart bitiş noktası.  
  
 <xref:System.ServiceModel.Description.ServiceMetadataEndpoint>  
 Meta veri değişimi için bir standart bitiş noktası.  
  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebHttpBehavior> davranışı  
  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> otomatik olarak bağlama ekler <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> davranışı.  
  
 <xref:System.ServiceModel.Description.WebServiceEndpoint>  
 Bir standart uç nokta ile bir <xref:System.ServiceModel.WebHttpBinding> bağlama.  
  
 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>  
 İş akışı örnekleri denetimi işlemleri çağırmak sağlayan bir standart uç nokta.  
  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>  
 İş akışı oluşturma ve yer imi sürdürme destekleyen bir standart uç nokta.
