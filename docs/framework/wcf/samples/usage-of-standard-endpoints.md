---
description: 'Hakkında daha fazla bilgi edinin: standart uç noktaların kullanımı'
title: Standart Uç Noktaları Kullanma
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 804fdd84d3f6ff6f961aed81e8bd14cf8c43063c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99685419"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="d992d-103">Standart Uç Noktaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d992d-103">Usage of Standard Endpoints</span></span>

<span data-ttu-id="d992d-104">Bu örnek, hizmet yapılandırma dosyalarında standart uç noktaların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d992d-104">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="d992d-105">Standart bir uç nokta, bir adres, bağlama ve sözleşme birleşimini onunla ilişkili ek özelliklerle birlikte belirtmek için tek bir özellik kullanarak Endpoint tanımlarını basitleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d992d-105">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="d992d-106">Bu örnek, özel bir standart uç noktanın nasıl tanımlanacağını ve uygulanacağını ve uç noktada belirli özelliklerin nasıl tanımlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d992d-106">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="d992d-107">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d992d-107">Sample Details</span></span>

<span data-ttu-id="d992d-108">Hizmet uç noktaları üç parametre sunarak belirtilebilir: adres, bağlama ve anlaşma.</span><span class="sxs-lookup"><span data-stu-id="d992d-108">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="d992d-109">Sağlanabilecek diğer parametreler, davranış yapılandırması, üst bilgiler, dinleme URI 'SI vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="d992d-109">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="d992d-110">Bazı durumlarda, adreslerin, bağlamaların ve sözleşmelerin tümünün veya tümünün değiştirebir değer vardır.</span><span class="sxs-lookup"><span data-stu-id="d992d-110">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="d992d-111">Bu nedenle, standart uç noktaları kullanmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d992d-111">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="d992d-112">Bu uç noktalara bazı örnekler, meta veri değişim uç noktaları ve bulma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="d992d-112">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="d992d-113">Standart uç noktalar Ayrıca, sabit bir doğası hakkında bilgi sağlamak ya da kendi standart uç noktalarını oluşturmak zorunda kalmadan hizmet uç noktalarının yapılandırılmasına izin vererek kullanılabilirliği artırır. Örneğin, makul bir varsayılan değerler kümesi sağlayarak kullanılabilirliği artırmak ve bu sayede yapılandırma dosyalarının ayrıntı düzeyini azaltmak.</span><span class="sxs-lookup"><span data-stu-id="d992d-113">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="d992d-114">Bu örnek iki projeden oluşur: iki standart uç noktayı ve hizmetle iletişim kuran istemciyi tanımlayan hizmet.</span><span class="sxs-lookup"><span data-stu-id="d992d-114">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="d992d-115">Yapılandırma dosyasında hizmet için standart uç noktaların tanımlandığı şekilde aşağıdaki örnekte gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d992d-115">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

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

<span data-ttu-id="d992d-116">Hizmet için tanımlanan ilk uç nokta, `customEndpoint` tanımı, `<standardEndpoints>` özelliğin değeri verilen bölümünde görünebilen tür olur `property` `true` .</span><span class="sxs-lookup"><span data-stu-id="d992d-116">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="d992d-117">Bu, yeni bir özellikle özelleştirilmiş bir uç noktanın durumdur.</span><span class="sxs-lookup"><span data-stu-id="d992d-117">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="d992d-118">İkinci uç nokta, adres, bağlama ve anlaşma değerlerinin düzeltildiği bir meta veri uç noktasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="d992d-118">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="d992d-119">Standart uç nokta öğesini tanımlamak için, öğesinden türetilen bir sınıfın `StandardEndpointElement` oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d992d-119">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="d992d-120">Bu örnek söz konusu olduğunda, `CustomEndpointElement` sınıf aşağıdaki örnekte gösterildiği gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d992d-120">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

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

<span data-ttu-id="d992d-121">`CreateServiceEndpoint`İşlevinde bir `CustomEndpoint` nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d992d-121">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="d992d-122">Tanımı aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d992d-122">Its definition is shown in the following example:</span></span>

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

 <span data-ttu-id="d992d-123">Hizmet ile istemci arasındaki iletişimi gerçekleştirmek için istemcide hizmet başvurusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d992d-123">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="d992d-124">Örnek oluşturulup yürütüldüğünde, hizmet yürütülür ve istemci onunla iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d992d-124">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="d992d-125">Hizmette her değişiklik olduğunda hizmet başvurusunun güncelleştirilmesini gerekeceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d992d-125">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d992d-126">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="d992d-126">To use this sample</span></span>

1. <span data-ttu-id="d992d-127">Visual Studio 2012 kullanarak StandardEndpoints. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="d992d-127">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="d992d-128">Birden çok projenin başlatılmasını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d992d-128">Enable multiple projects to start up.</span></span>

    1. <span data-ttu-id="d992d-129">**Çözüm Gezgini**, standart uç noktalar çözümüne sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d992d-129">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2. <span data-ttu-id="d992d-130">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç** projesi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d992d-130">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3. <span data-ttu-id="d992d-131">**Eylem** **Başlangıç** olarak ayarlanmış şekilde, hizmet projesini listenin başına taşıyın.</span><span class="sxs-lookup"><span data-stu-id="d992d-131">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4. <span data-ttu-id="d992d-132">Istemci projesini, **eylem** olarak ayarlanmış şekilde, hizmet projesinden sonra da **taşıyın.**</span><span class="sxs-lookup"><span data-stu-id="d992d-132">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="d992d-133">Bu, Istemci projesinin hizmet projesinden sonra yürütüleceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d992d-133">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="d992d-134">Çözümü çalıştırmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="d992d-134">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="d992d-135">Bu adımlar işe yoksa, aşağıdaki adımları kullanarak ortamınızın düzgün şekilde ayarlandığından emin olun:</span><span class="sxs-lookup"><span data-stu-id="d992d-135">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="d992d-136">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d992d-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="d992d-137">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d992d-137">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="d992d-138">Örneği tek veya birden çok bilgisayar yapılandırmasında çalıştırmak için, [Windows Communication Foundation örneklerini çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d992d-138">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d992d-139">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d992d-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d992d-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d992d-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d992d-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d992d-141">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d992d-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d992d-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
