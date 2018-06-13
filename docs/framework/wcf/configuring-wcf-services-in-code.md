---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 714236bcdb562840323698622cdf3d0c6c89b6ca
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804153"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="6518f-102">WCF Hizmetlerini Kodda Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="6518f-103">Windows Communication Foundation (WCF) hizmetlerini yapılandırma dosyalarının veya kod kullanarak yapılandırmak geliştiricilerin sağlar.</span><span class="sxs-lookup"><span data-stu-id="6518f-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="6518f-104">Yapılandırma dosyaları bir hizmet dağıtılan sonra yapılandırılması gerektiğinde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="6518f-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="6518f-105">Yapılandırma dosyaları kullanırken, bir BT Uzmanı yapılandırma dosyasını güncelleştirmek yeterlidir, hiçbir yeniden derlenmek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6518f-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="6518f-106">Yapılandırma dosyaları, ancak, karmaşık ve korumak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6518f-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="6518f-107">Hata ayıklama yapılandırma dosyaları için desteği yoktur ve yapılandırma öğeleri zor ve hataya yatkın yapılandırma dosyalarını geliştirme kılan adları tarafından başvurulur.</span><span class="sxs-lookup"><span data-stu-id="6518f-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="6518f-108">WCF hizmetlerini kodda yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6518f-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="6518f-109">WCF (4.0 ve önceki) yapılandırma Hizmetleri kod, önceki sürümlerindeki kendini barındıran senaryolarda kolay olan <xref:System.ServiceModel.ServiceHost> uç noktaları ve ServiceHost.Open çağırmadan önce davranışları yapılandırmak için sınıfa izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="6518f-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="6518f-110">Webde barındırılan senaryolarda, ancak, doğrudan erişiminiz yok <xref:System.ServiceModel.ServiceHost> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6518f-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="6518f-111">Barındırılan hizmeti oluşturmak için gerekli bir web yapılandırmak için bir `System.ServiceModel.ServiceHostFactory` oluşturulan <xref:System.ServiceModel.Activation.ServiceHostFactory> ve gerekli olan herhangi bir yapılandırmaya gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6518f-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="6518f-112">.NET 4. 5'ile başlayarak, her ikisi de yapılandırmak için daha kolay bir yolu kendi kendini barındıran ve web kodu Hizmetleri'nde barındırılan WCF sağlar.</span><span class="sxs-lookup"><span data-stu-id="6518f-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="6518f-113">Yapılandırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="6518f-113">The Configure method</span></span>  
 <span data-ttu-id="6518f-114">Yalnızca adlı genel statik yöntemi tanımlayın `Configure` hizmet uygulaması sınıfınızda aşağıdaki imzayla:</span><span class="sxs-lookup"><span data-stu-id="6518f-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="6518f-115">Yapılandırma yöntemine geçen bir <xref:System.ServiceModel.ServiceConfiguration> uç noktaları ve davranışları eklemek Geliştirici etkinleştirir örneği.</span><span class="sxs-lookup"><span data-stu-id="6518f-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="6518f-116">Hizmet ana bilgisayarı açılmadan önce bu yöntem WCF tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6518f-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="6518f-117">Tanımlandığında, bir app.config veya web.config dosyasında belirtilen tüm hizmet yapılandırma ayarları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="6518f-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="6518f-118">Aşağıdaki kod parçacığını nasıl tanımlanacağı gösterilmektedir `Configure` yöntemi ve hizmet uç noktası, bir uç noktası davranışı ve hizmet davranışları ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6518f-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
            return string.Format("You entered: {0}", value);  
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
  
 <span data-ttu-id="6518f-119">Bir hizmet için https gibi bir protokolü etkinleştirmek için ya da açıkça protokolünü kullanan bir uç nokta ekleyebilir ve her taban adresi için bir uç nokta ekleyen ServiceConfiguration.EnableProtocol(Binding) çağırarak otomatik olarak uç noktalar ekleyebilirsiniz protokol ve tanımlanan her hizmet sözleşmesi ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="6518f-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="6518f-120">Aşağıdaki kod ServiceConfiguration.EnableProtocol yönteminin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6518f-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
  
 <span data-ttu-id="6518f-121">Ayarlarında <`protocolMappings`> bölümünde hiç uygulama uç nokta eklenir, yalnızca kullanılır <xref:System.ServiceModel.ServiceConfiguration> programlı olarak. Çağırarak hizmet yapılandırmasını varsayılan uygulama yapılandırma dosyasından isteğe bağlı olarak yükleyebilir <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ve ayarlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6518f-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="6518f-122"><xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> Sınıfı ayrıca yapılandırma merkezi yapılandırmasından yük olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6518f-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="6518f-123">Aşağıdaki kod, bu uygulama verilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6518f-123">The following code illustrates how to implement this:</span></span>  
  
```  
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
>  <span data-ttu-id="6518f-124">Unutmayın <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> yoksayar <`host`> içindeki ayarlar <`service`> etiket <`system.serviceModel`>.</span><span class="sxs-lookup"><span data-stu-id="6518f-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="6518f-125">Kavramsal olarak, <`host`> ana bilgisayar yapılandırması, değil hizmet yapılandırmasını ve bu hakkında yapılandırma yöntemi yürütülmeden önce yüklenen alır.</span><span class="sxs-lookup"><span data-stu-id="6518f-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6518f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6518f-126">See Also</span></span>  
 [<span data-ttu-id="6518f-127">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-127">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="6518f-128">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-128">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="6518f-129">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-129">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="6518f-130">Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6518f-130">Configuration-Based Activation</span></span>](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [<span data-ttu-id="6518f-131">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-131">Configuration</span></span>](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [<span data-ttu-id="6518f-132">IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="6518f-132">Configuration-Based Activation in IIS and WAS</span></span>](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [<span data-ttu-id="6518f-133">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="6518f-133">Configuration and Metadata Support</span></span>](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [<span data-ttu-id="6518f-134">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6518f-134">Configuration</span></span>](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [<span data-ttu-id="6518f-135">Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme</span><span class="sxs-lookup"><span data-stu-id="6518f-135">How to: Specify a Service Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [<span data-ttu-id="6518f-136">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6518f-136">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [<span data-ttu-id="6518f-137">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="6518f-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="6518f-138">Nasıl yapılır: Yapılandırmada İstemci Bağlaması Belirtme</span><span class="sxs-lookup"><span data-stu-id="6518f-138">How to: Specify a Client Binding in Configuration</span></span>](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
