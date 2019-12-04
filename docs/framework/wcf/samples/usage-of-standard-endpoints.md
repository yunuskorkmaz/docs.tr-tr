---
title: Standart Uç Noktaları Kullanma
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715340"
---
# <a name="usage-of-standard-endpoints"></a>Standart Uç Noktaları Kullanma

Bu örnek, hizmet yapılandırma dosyalarında standart uç noktaların nasıl kullanılacağını gösterir. Standart bir uç nokta, bir adres, bağlama ve sözleşme birleşimini onunla ilişkili ek özelliklerle birlikte belirtmek için tek bir özellik kullanarak Endpoint tanımlarını basitleştirmesini sağlar. Bu örnek, özel bir standart uç noktanın nasıl tanımlanacağını ve uygulanacağını ve uç noktada belirli özelliklerin nasıl tanımlanacağını gösterir.

## <a name="sample-details"></a>Örnek Ayrıntılar

Hizmet uç noktaları üç parametre sunarak belirtilebilir: adres, bağlama ve anlaşma. Sağlanabilecek diğer parametreler, davranış yapılandırması, üst bilgiler, dinleme URI 'SI vb. içerir. Bazı durumlarda, adreslerin, bağlamaların ve sözleşmelerin tümünün veya tümünün değiştirebir değer vardır. Bu nedenle, standart uç noktaları kullanmak mümkündür. Bu uç noktalara bazı örnekler, meta veri değişim uç noktaları ve bulma uç noktaları içerir. Standart uç noktalar Ayrıca, sabit bir doğası hakkında bilgi sağlamak veya kendi standart uç noktalarını oluşturmak zorunda kalmadan hizmet uç noktalarının yapılandırılmasına izin vererek kullanılabilirliği artırır. Örneğin, makul bir varsayılan kümesi sağlayarak kullanılabilirliği artırmak için değerler ve bu sayede yapılandırma dosyalarının ayrıntı düzeyini azaltır.

Bu örnek iki projeden oluşur: iki standart uç noktayı ve hizmetle iletişim kuran istemciyi tanımlayan hizmet. Yapılandırma dosyasında hizmet için standart uç noktaların tanımlandığı şekilde aşağıdaki örnekte gösterilmektedir.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

Hizmet için tanımlanan ilk uç nokta `customEndpoint`türüdür. Bu, tanımı `property` `true`değeri verilen `<standardEndpoints>` bölümünde görülebilir. Bu, yeni bir özellikle özelleştirilmiş bir uç noktanın durumdur. İkinci uç nokta, adres, bağlama ve anlaşma değerlerinin düzeltildiği bir meta veri uç noktasına karşılık gelir.

Standart uç nokta öğesini tanımlamak için, `StandardEndpointElement` türetilen bir sınıfın oluşturulması gerekir. Bu örnek söz konusu olduğunda, `CustomEndpointElement` sınıfı aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

`CreateServiceEndpoint` işlevinde, bir `CustomEndpoint` nesnesi oluşturulur. Tanımı aşağıdaki örnekte gösterilmiştir:

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 Hizmet ile istemci arasındaki iletişimi gerçekleştirmek için istemcide hizmet başvurusu oluşturulur. Örnek oluşturulup yürütüldüğünde, hizmet yürütülür ve istemci onunla iletişim kurar. Hizmette her değişiklik olduğunda hizmet başvurusunun güncelleştirilmesini gerekeceğini unutmayın.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak StandardEndpoints. sln dosyasını açın.

2. Birden çok projenin başlatılmasını etkinleştirin.

    1. **Çözüm Gezgini**, standart uç noktalar çözümüne sağ tıklayın ve ardından **Özellikler**' i seçin.

    2. **Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç**projesi ' ne tıklayın.

    3. **Eylem** **Başlangıç**olarak ayarlanmış şekilde, hizmet projesini listenin başına taşıyın.

    4. Istemci projesini, **eylem** olarak ayarlanmış şekilde, hizmet projesinden sonra da **taşıyın.**

         Bu, Istemci projesinin hizmet projesinden sonra yürütüleceğini belirtir.

3. Çözümü çalıştırmak için F5 'e basın.

> [!NOTE]
> Bu adımlar işe yoksa, aşağıdaki adımları kullanarak ortamınızın düzgün şekilde ayarlandığından emin olun:
>
> 1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.
> 2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.
> 3. Örneği tek veya birden çok bilgisayar yapılandırmasında çalıştırmak için, [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
