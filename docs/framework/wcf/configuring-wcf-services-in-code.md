---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: c6bcf08511470d28e1087108d95e477683b0338b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320638"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="cc79b-102">WCF Hizmetlerini Kodda Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="cc79b-103">Windows Communication Foundation (WCF), geliştiricilerin yapılandırma dosyalarını veya kodu kullanarak hizmetleri yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="cc79b-104">Yapılandırma dosyaları, bir hizmetin dağıtıldıktan sonra yapılandırılması gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="cc79b-105">Yapılandırma dosyalarını kullanırken, bir BT uzmanı 'nın yalnızca yapılandırma dosyasını güncelleştirmesi gerekir, yeniden derleme gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cc79b-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="cc79b-106">Bununla birlikte yapılandırma dosyaları, karmaşık ve bakım açısından zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc79b-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="cc79b-107">Yapılandırma dosyalarını hata ayıklama desteği yoktur ve yapılandırma öğeleri, yazma yapılandırma dosyalarını hata-açık ve zor hale getiren adlara göre başvurulur.</span><span class="sxs-lookup"><span data-stu-id="cc79b-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="cc79b-108">WCF Ayrıca koddaki Hizmetleri yapılandırmanıza de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="cc79b-109">WCF 'nin önceki sürümlerinde (4,0 ve önceki sürümler), kodda hizmetleri yapılandırmak kendi kendine barındırılan senaryolarda kolaydır. <xref:System.ServiceModel.ServiceHost> sınıfı, ServiceHost. Open çağrılmadan önce uç noktaları ve davranışları yapılandırmanıza izin verilir.</span><span class="sxs-lookup"><span data-stu-id="cc79b-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="cc79b-110">Ancak, Web 'de barındırılan senaryolarda <xref:System.ServiceModel.ServiceHost> sınıfına doğrudan erişiminiz yoktur.</span><span class="sxs-lookup"><span data-stu-id="cc79b-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="cc79b-111">Web 'de barındırılan bir hizmeti yapılandırmak için, <xref:System.ServiceModel.Activation.ServiceHostFactory> ' i oluşturan ve gerekli tüm yapılandırmaları gerçekleştiren bir `System.ServiceModel.ServiceHostFactory` oluşturmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="cc79b-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="cc79b-112">WCF, .NET 4,5 ile başlayarak, kodda hem şirket içinde barındırılan hem de Web 'de barındırılan Hizmetleri yapılandırmanın daha kolay bir yolunu sunar.</span><span class="sxs-lookup"><span data-stu-id="cc79b-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="cc79b-113">Configure yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc79b-113">The Configure method</span></span>  
 <span data-ttu-id="cc79b-114">Hizmet uygulama Sınıfınıza aşağıdaki imzaya sahip `Configure` adlı ortak bir statik yöntem tanımlamanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="cc79b-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="cc79b-115">Configure yöntemi, geliştiricinin uç noktalar ve davranışlar eklemesini sağlayan <xref:System.ServiceModel.ServiceConfiguration> örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="cc79b-116">Bu yöntem, hizmet ana bilgisayarı açılmadan önce WCF tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="cc79b-117">Tanımlandığında, bir App. config veya Web. config dosyasında belirtilen herhangi bir hizmet yapılandırma ayarı yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="cc79b-118">Aşağıdaki kod parçacığı `Configure` yönteminin nasıl tanımlanacağını ve bir hizmet uç noktası, bir uç nokta davranışı ve hizmet davranışı nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cc79b-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 <span data-ttu-id="cc79b-119">Bir hizmet için https gibi bir protokolü etkinleştirmek için, protokolü kullanan bir uç noktayı açıkça ekleyebilir veya her temel adres için bir uç nokta ekleyen ServiceConfiguration. EnableProtocol (bağlama) çağırarak uç noktaları otomatik olarak ekleyebilirsiniz protokolle ve tanımlanan her hizmet sözleşmesiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="cc79b-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="cc79b-120">Aşağıdaki kod, ServiceConfiguration. EnableProtocol yönteminin nasıl kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cc79b-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 <span data-ttu-id="cc79b-121">< @No__t-0 > bölümündeki ayarlar yalnızca <xref:System.ServiceModel.ServiceConfiguration> programlama yoluyla hiçbir uygulama uç noktası eklenmemişse kullanılır. İsteğe bağlı olarak, hizmet yapılandırmasını, <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ' yi çağırarak varsayılan uygulama yapılandırma dosyasından yükleyebilirsiniz ve sonra ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc79b-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="cc79b-122">@No__t-0 sınıfı, merkezi bir yapılandırmadan yapılandırmayı yüklemenize de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc79b-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="cc79b-123">Aşağıdaki kod, bunun nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cc79b-123">The following code illustrates how to implement this:</span></span>  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="cc79b-124">@No__t-0 < < `system.serviceModel` > etiketindeki `host` > ayarları yoksayar.</span><span class="sxs-lookup"><span data-stu-id="cc79b-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="cc79b-125">Kavramsal olarak, < `host` >, hizmet yapılandırması değil konak yapılandırması ile ilgilidir ve Configure Yöntemi yürütülmeden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cc79b-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc79b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc79b-126">See also</span></span>

- [<span data-ttu-id="cc79b-127">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="cc79b-128">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="cc79b-129">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="cc79b-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="cc79b-131">IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cc79b-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="cc79b-132">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="cc79b-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="cc79b-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc79b-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="cc79b-134">Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme</span><span class="sxs-lookup"><span data-stu-id="cc79b-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="cc79b-135">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc79b-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="cc79b-136">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="cc79b-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="cc79b-137">Nasıl yapılır: Yapılandırmada İstemci Bağlaması Belirtme</span><span class="sxs-lookup"><span data-stu-id="cc79b-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
