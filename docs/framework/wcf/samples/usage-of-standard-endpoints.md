---
title: Standart uç noktaları
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 5502d42d6a576509c826e05c8781662d374fbff4
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584292"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="08e41-102">Standart uç noktaları</span><span class="sxs-lookup"><span data-stu-id="08e41-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="08e41-103">Bu örnek, hizmet yapılandırma dosyalarında standart uç noktaları kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="08e41-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="08e41-104">Standart uç nokta, uç nokta tanımları ile ilişkili ek özellikleri bir adres, bağlama ve sözleşme birleşimi açıklamak için tek bir özellik kullanarak basitleştirmek kullanıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="08e41-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="08e41-105">Bu örnek nasıl tanımlaması ve özel bir standart uç noktası ve bitiş noktasını belirli özelliklerini tanımlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="08e41-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="08e41-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="08e41-106">Sample Details</span></span>

<span data-ttu-id="08e41-107">Hizmet uç noktaları, üç parametre sağlanarak belirtilebilir: adres, bağlama ve sözleşme.</span><span class="sxs-lookup"><span data-stu-id="08e41-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="08e41-108">Sağlanabilir diğer parametreler davranışı yapılandırmasına, üst bilgiler, dinleme URI vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="08e41-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="08e41-109">Bazı durumlarda, tüm veya tüm adresler, bağlamalar ve sözleşmeler değiştiremezsiniz değerlere sahipsiniz.</span><span class="sxs-lookup"><span data-stu-id="08e41-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="08e41-110">Bu nedenle, standart uç noktaları kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="08e41-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="08e41-111">Bu uç noktaları bazı örnekleri, meta veri değişimi uç noktaları ve bulma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="08e41-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="08e41-112">Standart uç noktaları da sabit yapısı bilgileri sağlamak ya da makul bir varsayılan kümesini sağlayarak kullanılabilirliği iyileştirmek, örneğin standart, kendi uç noktalar oluşturmak için gerek kalmadan hizmet uç noktaları yapılandırılmasını sağlayarak artırmamıza değerleri ve bu nedenle, yapılandırma dosyalarının ayrıntı düzeyini azaltır.</span><span class="sxs-lookup"><span data-stu-id="08e41-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="08e41-113">Bu örnek iki projeden oluşan: iki standart uç nokta tanımlayan hizmet ve hizmeti ile iletişim kuran istemci.</span><span class="sxs-lookup"><span data-stu-id="08e41-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="08e41-114">Standart uç noktaları için hizmet yapılandırma dosyasında tanımlanan aşağıdaki örnekte show yoludur.</span><span class="sxs-lookup"><span data-stu-id="08e41-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="08e41-115">Hizmet türü için tanımlanan ilk uç nokta `customEndpoint`, tanımları görülebilir `<standardEndpoints>` bölümünde, özellik `property` değerin `true`.</span><span class="sxs-lookup"><span data-stu-id="08e41-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="08e41-116">Yeni bir özellik ile özelleştirilmiş bir uç nokta durum budur.</span><span class="sxs-lookup"><span data-stu-id="08e41-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="08e41-117">İkinci uç nokta adresi, bağlama ve sözleşme değerlerini düzeltilen bir meta veri uç noktasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="08e41-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="08e41-118">Standart uç nokta öğenin türetildiği bir sınıf tanımlamak için `StandardEndpointElement` oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08e41-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="08e41-119">Bu örnek, söz konusu olduğunda `CustomEndpointElement` aşağıdaki örnekte gösterildiği gibi sınıfı tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="08e41-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="08e41-120">İçinde `CreateServiceEndpoint` işlevi, bir `CustomEndpoint` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08e41-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="08e41-121">Tanımı aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="08e41-121">Its definition is shown in the following example:</span></span>

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

 <span data-ttu-id="08e41-122">Hizmet ve istemci arasındaki iletişimin gerçekleştirmek için bir hizmet başvurusu hizmeti istemcisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="08e41-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="08e41-123">Örneği oluşturulan ve yürütülen hizmeti yürütür ve istemci ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="08e41-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="08e41-124">Var. her zaman bazı değişiklik hizmetinde hizmet başvurusunu güncelleştirilmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="08e41-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="08e41-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="08e41-125">To use this sample</span></span>

1.  <span data-ttu-id="08e41-126">Visual Studio 2012 kullanarak, StandardEndpoints.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="08e41-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2.  <span data-ttu-id="08e41-127">Başlamak birden çok proje etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="08e41-127">Enable multiple projects to start up.</span></span>

    1.  <span data-ttu-id="08e41-128">İçinde **Çözüm Gezgini**, standart uç noktaları çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="08e41-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2.  <span data-ttu-id="08e41-129">İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="08e41-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3.  <span data-ttu-id="08e41-130">Hizmet projesi ile listenin başına taşı **eylem** kümesine **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="08e41-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4.  <span data-ttu-id="08e41-131">İstemci projesi hizmet projesi sonra da WITH move **eylem** kümesine **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="08e41-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="08e41-132">Bu, istemci projesinin sonra hizmet projesi yürütüldüğünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="08e41-132">This specifies that the Client project is executed after the Service project.</span></span>

3.  <span data-ttu-id="08e41-133">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="08e41-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="08e41-134">Adımları işe yaramazsa, ortamınızı düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="08e41-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="08e41-135">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08e41-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="08e41-136">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08e41-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="08e41-137">Tek bir veya birden çok bilgisayar yapılandırmalarını örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08e41-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08e41-138">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="08e41-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="08e41-139">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="08e41-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="08e41-140">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="08e41-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08e41-141">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="08e41-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
