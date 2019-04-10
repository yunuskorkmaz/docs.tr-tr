---
title: Standart uç noktaları
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 4ef0714acad12db1414e34fbb476b4ae7d1d9fb2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304616"
---
# <a name="usage-of-standard-endpoints"></a>Standart uç noktaları

Bu örnek, hizmet yapılandırma dosyalarında standart uç noktaları kullanma işlemini gösterir. Standart uç nokta, uç nokta tanımları ile ilişkili ek özellikleri bir adres, bağlama ve sözleşme birleşimi açıklamak için tek bir özellik kullanarak basitleştirmek kullanıcı sağlar. Bu örnek nasıl tanımlaması ve özel bir standart uç noktası ve bitiş noktasını belirli özelliklerini tanımlamak nasıl gösterir.

## <a name="sample-details"></a>Örnek Ayrıntıları

Hizmet uç noktaları, üç parametre sağlanarak belirtilebilir: adres, bağlama ve sözleşme. Sağlanabilir diğer parametreler davranışı yapılandırmasına, üst bilgiler, dinleme URI vb. içerir. Bazı durumlarda, tüm veya tüm adresler, bağlamalar ve sözleşmeler değiştiremezsiniz değerlere sahipsiniz. Bu nedenle, standart uç noktaları kullanmak da mümkündür. Bu uç noktaları bazı örnekleri, meta veri değişimi uç noktaları ve bulma uç noktaları içerir. Standart uç noktaları da sabit yapısı bilgileri sağlamak ya da makul bir varsayılan kümesini sağlayarak kullanılabilirliği iyileştirmek, örneğin standart, kendi uç noktalar oluşturmak için gerek kalmadan hizmet uç noktaları yapılandırılmasını sağlayarak artırmamıza değerleri ve bu nedenle, yapılandırma dosyalarının ayrıntı düzeyini azaltır.

Bu örnek iki projeden oluşan: iki standart uç nokta tanımlayan hizmet ve hizmeti ile iletişim kuran istemci. Standart uç noktaları için hizmet yapılandırma dosyasında tanımlanan aşağıdaki örnekte show yoludur.

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

Hizmet türü için tanımlanan ilk uç nokta `customEndpoint`, tanımları görülebilir `<standardEndpoints>` bölümünde, özellik `property` değerin `true`. Yeni bir özellik ile özelleştirilmiş bir uç nokta durum budur. İkinci uç nokta adresi, bağlama ve sözleşme değerlerini düzeltilen bir meta veri uç noktasına karşılık gelir.

Standart uç nokta öğenin türetildiği bir sınıf tanımlamak için `StandardEndpointElement` oluşturulması gerekir. Bu örnek, söz konusu olduğunda `CustomEndpointElement` aşağıdaki örnekte gösterildiği gibi sınıfı tanımlanmış.

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

İçinde `CreateServiceEndpoint` işlevi, bir `CustomEndpoint` nesnesi oluşturulur. Tanımı aşağıdaki örnekte gösterilmiştir:

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

 Hizmet ve istemci arasındaki iletişimin gerçekleştirmek için bir hizmet başvurusu hizmeti istemcisi oluşturulur. Örneği oluşturulan ve yürütülen hizmeti yürütür ve istemci ile iletişim kurar. Var. her zaman bazı değişiklik hizmetinde hizmet başvurusunu güncelleştirilmesi gerektiğini unutmayın.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Visual Studio 2012 kullanarak, StandardEndpoints.sln dosyasını açın.

2. Başlamak birden çok proje etkinleştirin.

    1.  İçinde **Çözüm Gezgini**, standart uç noktaları çözüme sağ tıklayın ve ardından **özellikleri**.

    2.  İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.

    3.  Hizmet projesi ile listenin başına taşı **eylem** kümesine **Başlat**.

    4.  İstemci projesi hizmet projesi sonra da WITH move **eylem** kümesine **Başlat**.

         Bu, istemci projesinin sonra hizmet projesi yürütüldüğünü belirtir.

3. Çözümü çalıştırmak için F5 tuşuna basın.

> [!NOTE]
> Adımları işe yaramazsa, ortamınızı düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığından emin olun:
>
> 1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).
> 3. Tek bir veya birden çok bilgisayar yapılandırmalarını örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).

> [!IMPORTANT]
> Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
