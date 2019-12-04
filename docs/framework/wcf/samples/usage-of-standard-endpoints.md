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
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="dceb8-102">Standart Uç Noktaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="dceb8-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="dceb8-103">Bu örnek, hizmet yapılandırma dosyalarında standart uç noktaların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="dceb8-104">Standart bir uç nokta, bir adres, bağlama ve sözleşme birleşimini onunla ilişkili ek özelliklerle birlikte belirtmek için tek bir özellik kullanarak Endpoint tanımlarını basitleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="dceb8-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="dceb8-105">Bu örnek, özel bir standart uç noktanın nasıl tanımlanacağını ve uygulanacağını ve uç noktada belirli özelliklerin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="dceb8-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dceb8-106">Sample Details</span></span>

<span data-ttu-id="dceb8-107">Hizmet uç noktaları üç parametre sunarak belirtilebilir: adres, bağlama ve anlaşma.</span><span class="sxs-lookup"><span data-stu-id="dceb8-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="dceb8-108">Sağlanabilecek diğer parametreler, davranış yapılandırması, üst bilgiler, dinleme URI 'SI vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="dceb8-109">Bazı durumlarda, adreslerin, bağlamaların ve sözleşmelerin tümünün veya tümünün değiştirebir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="dceb8-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="dceb8-110">Bu nedenle, standart uç noktaları kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="dceb8-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="dceb8-111">Bu uç noktalara bazı örnekler, meta veri değişim uç noktaları ve bulma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="dceb8-112">Standart uç noktalar Ayrıca, sabit bir doğası hakkında bilgi sağlamak veya kendi standart uç noktalarını oluşturmak zorunda kalmadan hizmet uç noktalarının yapılandırılmasına izin vererek kullanılabilirliği artırır. Örneğin, makul bir varsayılan kümesi sağlayarak kullanılabilirliği artırmak için değerler ve bu sayede yapılandırma dosyalarının ayrıntı düzeyini azaltır.</span><span class="sxs-lookup"><span data-stu-id="dceb8-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="dceb8-113">Bu örnek iki projeden oluşur: iki standart uç noktayı ve hizmetle iletişim kuran istemciyi tanımlayan hizmet.</span><span class="sxs-lookup"><span data-stu-id="dceb8-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="dceb8-114">Yapılandırma dosyasında hizmet için standart uç noktaların tanımlandığı şekilde aşağıdaki örnekte gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="dceb8-115">Hizmet için tanımlanan ilk uç nokta `customEndpoint`türüdür. Bu, tanımı `property` `true`değeri verilen `<standardEndpoints>` bölümünde görülebilir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="dceb8-116">Bu, yeni bir özellikle özelleştirilmiş bir uç noktanın durumdur.</span><span class="sxs-lookup"><span data-stu-id="dceb8-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="dceb8-117">İkinci uç nokta, adres, bağlama ve anlaşma değerlerinin düzeltildiği bir meta veri uç noktasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="dceb8-118">Standart uç nokta öğesini tanımlamak için, `StandardEndpointElement` türetilen bir sınıfın oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="dceb8-119">Bu örnek söz konusu olduğunda, `CustomEndpointElement` sınıfı aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dceb8-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="dceb8-120">`CreateServiceEndpoint` işlevinde, bir `CustomEndpoint` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dceb8-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="dceb8-121">Tanımı aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="dceb8-121">Its definition is shown in the following example:</span></span>

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

 <span data-ttu-id="dceb8-122">Hizmet ile istemci arasındaki iletişimi gerçekleştirmek için istemcide hizmet başvurusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dceb8-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="dceb8-123">Örnek oluşturulup yürütüldüğünde, hizmet yürütülür ve istemci onunla iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="dceb8-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="dceb8-124">Hizmette her değişiklik olduğunda hizmet başvurusunun güncelleştirilmesini gerekeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dceb8-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="dceb8-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dceb8-125">To use this sample</span></span>

1. <span data-ttu-id="dceb8-126">Visual Studio 2012 kullanarak StandardEndpoints. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="dceb8-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="dceb8-127">Birden çok projenin başlatılmasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-127">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="dceb8-128">**Çözüm Gezgini**, standart uç noktalar çözümüne sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="dceb8-129">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç**projesi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="dceb8-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="dceb8-130">**Eylem** **Başlangıç**olarak ayarlanmış şekilde, hizmet projesini listenin başına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="dceb8-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="dceb8-131">Istemci projesini, **eylem** olarak ayarlanmış şekilde, hizmet projesinden sonra da **taşıyın.**</span><span class="sxs-lookup"><span data-stu-id="dceb8-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="dceb8-132">Bu, Istemci projesinin hizmet projesinden sonra yürütüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="dceb8-133">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="dceb8-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="dceb8-134">Bu adımlar işe yoksa, aşağıdaki adımları kullanarak ortamınızın düzgün şekilde ayarlandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="dceb8-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="dceb8-135">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="dceb8-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="dceb8-136">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="dceb8-137">Örneği tek veya birden çok bilgisayar yapılandırmasında çalıştırmak için, [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dceb8-138">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="dceb8-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dceb8-139">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="dceb8-140">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="dceb8-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dceb8-141">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="dceb8-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
