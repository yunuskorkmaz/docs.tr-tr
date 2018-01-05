---
title: "Standart uç noktaları kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ac8a9c639099e952f6030f5625958dd2bf84757
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="74f62-102">Standart uç noktaları kullanma</span><span class="sxs-lookup"><span data-stu-id="74f62-102">Usage of Standard Endpoints</span></span>
<span data-ttu-id="74f62-103">Bu örnek, hizmet yapılandırma dosyalarını standart uç noktaları kullanımı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="74f62-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="74f62-104">Standart bir uç noktası için ilişkili ek özellikleri ile bir adresi, bağlama ve sözleşme birleşimi açıklamak için tek bir özellik kullanarak uç nokta tanımları basitleştirme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="74f62-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="74f62-105">Bu örnek nasıl tanımlamak ve özel bir standart uç noktası uygulanacağını ve uç belirli özelliklerini tanımlamak nasıl gösterilir.</span><span class="sxs-lookup"><span data-stu-id="74f62-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="74f62-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="74f62-106">Sample Details</span></span>  
 <span data-ttu-id="74f62-107">Hizmet uç noktaları üç parametresi sağlanarak belirtilebilir: Sözleşme ve adresi, bağlama.</span><span class="sxs-lookup"><span data-stu-id="74f62-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="74f62-108">Sağlanabilir diğer parametreleri davranışı yapılandırmasını, üstbilgiler, dinleme URI vb. içerir.</span><span class="sxs-lookup"><span data-stu-id="74f62-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="74f62-109">Bazı durumlarda, tüm veya tüm adresleri, bağlamalar ve sözleşmeler değiştiremezsiniz değerlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="74f62-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="74f62-110">Bu nedenle, standart uç noktaları kullanmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="74f62-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="74f62-111">Bu tür uç noktaları bazı örnekleri meta verileri exchange uç noktaları ve bulma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="74f62-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="74f62-112">Ayrıca standart uç noktaları varsayılan makul bir kümesini sağlayarak kullanılabilirliğini artıran örneğin kendi standart uç noktaları oluşturmak için veya bir sabit doğası bilgi sağlamak zorunda kalmadan hizmet uç noktaları yapılandırılmasını sağlayarak kullanılabilirliğini artıran değerler ve böylece yapılandırma dosyalarını ayrıntı düzeyini azaltır.</span><span class="sxs-lookup"><span data-stu-id="74f62-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>  
  
 <span data-ttu-id="74f62-113">Bu örnek iki projeden oluşan: iki standart uç noktaları tanımlar hizmeti ve istemcinin hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="74f62-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="74f62-114">Standart uç noktaları hizmet yapılandırma dosyasında tanımlanmış Göster aşağıdaki örnekte bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="74f62-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>  
  
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
  
 <span data-ttu-id="74f62-115">Hizmet türü için tanımlanan ilk uç noktası `customEndpoint`, tanımları içinde görülme `<standardEndpoints>` bölümünde, hangi özelliği `property` değeri verildiğinde `true`.</span><span class="sxs-lookup"><span data-stu-id="74f62-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="74f62-116">Bu ada sahip yeni bir özellik özelleştirilmiş bir uç nokta durumdur.</span><span class="sxs-lookup"><span data-stu-id="74f62-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="74f62-117">İkinci uç nokta adresi, bağlama ve sözleşme değerlerini sabit bir meta veri uç noktasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="74f62-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>  
  
 <span data-ttu-id="74f62-118">Öğesinden türeyen bir sınıf bir standart bitiş noktası öğesinin tanımlamak için `StandardEndpointElement` oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="74f62-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="74f62-119">Bu örnek, söz konusu olduğunda `CustomEndpointElement` aşağıdaki örnekte gösterildiği gibi sınıfı tanımlandı.</span><span class="sxs-lookup"><span data-stu-id="74f62-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="74f62-120">İçinde `CreateServiceEndpoint` işlevi, bir `CustomEndpoint` nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="74f62-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="74f62-121">Tanımına aşağıdaki örnekte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="74f62-121">Its definition is shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="74f62-122">Hizmet ve istemci arasındaki iletişimin gerçekleştirmek için İstemci hizmetine hizmet başvurusu oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="74f62-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="74f62-123">Örnek yerleşik ve yürütülen hizmeti yürütür ve istemci ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="74f62-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="74f62-124">Olduğundan her zaman hizmetinde bazı değişiklik hizmet başvurusu güncelleştirilmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74f62-124">Note that the service reference should be updated every time there is some change in the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="74f62-125">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="74f62-125">To use this sample</span></span>  
  
1.  <span data-ttu-id="74f62-126">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], StandardEndpoints.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="74f62-126">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the StandardEndpoints.sln file.</span></span>  
  
2.  <span data-ttu-id="74f62-127">Başlamak birden çok proje etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="74f62-127">Enable multiple projects to start up.</span></span>  
  
    1.  <span data-ttu-id="74f62-128">İçinde **Çözüm Gezgini**, standart uç noktaları çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="74f62-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="74f62-129">İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="74f62-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>  
  
    3.  <span data-ttu-id="74f62-130">Hizmet projesi ile listesi başlangıcına Taşı **eylem** kümesine **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="74f62-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>  
  
    4.  <span data-ttu-id="74f62-131">İstemci projesi hizmet projesi sonra da WITH move **eylem** kümesine **Başlat**.</span><span class="sxs-lookup"><span data-stu-id="74f62-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>  
  
         <span data-ttu-id="74f62-132">Bu, istemci projesi sonra hizmet projesi yürütülür belirtir.</span><span class="sxs-lookup"><span data-stu-id="74f62-132">This specifies that the Client project is executed after the Service project.</span></span>  
  
3.  <span data-ttu-id="74f62-133">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="74f62-133">To run the solution, press F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74f62-134">Bu adımlar işe yaramazsa, ortamınızın düzgün bir şekilde, aşağıdaki adımları kullanarak ayarlandığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="74f62-134">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="74f62-135">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74f62-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="74f62-136">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74f62-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="74f62-137">Tek bir veya birden çok bilgisayar yapılandırması örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74f62-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="74f62-138">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="74f62-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74f62-139">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74f62-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74f62-140">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="74f62-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74f62-141">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="74f62-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## <a name="see-also"></a><span data-ttu-id="74f62-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74f62-142">See Also</span></span>
