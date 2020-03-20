---
title: WCF Hizmetlerini Kodda Yapılandırma
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174816"
---
# <a name="configuring-wcf-services-in-code"></a><span data-ttu-id="9f65b-102">WCF Hizmetlerini Kodda Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-102">Configuring WCF Services in Code</span></span>
<span data-ttu-id="9f65b-103">Windows Communication Foundation (WCF), geliştiricilerin hizmetleri yapılandırma dosyalarını veya kodunu kullanarak yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-103">Windows Communication Foundation (WCF) allows developers to configure services using configuration files or code.</span></span>  <span data-ttu-id="9f65b-104">Yapılandırma dosyaları, bir hizmetin dağıtıldıktan sonra yapılandırılması gerektiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-104">Configuration files are useful when a service needs to be configured after being deployed.</span></span> <span data-ttu-id="9f65b-105">Yapılandırma dosyalarını kullanırken, bt uzmanının yalnızca yapılandırma dosyasını güncelleştirmesi gerekir, yeniden derleme gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9f65b-105">When using configuration files, an IT professional only needs to update the configuration file, no recompilation is required.</span></span> <span data-ttu-id="9f65b-106">Ancak yapılandırma dosyaları karmaşık ve bakımı zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f65b-106">Configuration files, however, can be complex and difficult to maintain.</span></span> <span data-ttu-id="9f65b-107">Hata ayıklama yapılandırma dosyaları için destek yoktur ve yapılandırma öğeleri yapılandırma dosyaları yazma hata eğilimli ve zor kılan adlarla başvurur.</span><span class="sxs-lookup"><span data-stu-id="9f65b-107">There is no support for debugging configuration files and configuration elements are referenced by names which makes authoring configuration files error-prone and difficult.</span></span> <span data-ttu-id="9f65b-108">WCF ayrıca hizmetleri kod halinde yapılandırmanıza da olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-108">WCF also allows you to configure services in code.</span></span> <span data-ttu-id="9f65b-109">WCF'nin önceki sürümlerinde (4.0 ve daha önceki) hizmetleri kodda yapılandırmak kendi kendine barındırılan senaryolarda kolaydı, <xref:System.ServiceModel.ServiceHost> sınıf ServiceHost.Open'ı aramadan önce uç noktaları ve davranışları yapılandırmanıza olanak sağladı.</span><span class="sxs-lookup"><span data-stu-id="9f65b-109">In earlier versions of WCF (4.0 and earlier) configuring services in code was easy in self-hosted scenarios, the <xref:System.ServiceModel.ServiceHost> class allowed you to configure endpoints and behaviors prior to calling ServiceHost.Open.</span></span> <span data-ttu-id="9f65b-110">Ancak, web barındırılan senaryolarda <xref:System.ServiceModel.ServiceHost> sınıfa doğrudan erişiminiz yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f65b-110">In web hosted scenarios, however, you don’t have direct access to the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="9f65b-111">Web barındırılan bir hizmeti yapılandırmak `System.ServiceModel.ServiceHostFactory` için, <xref:System.ServiceModel.Activation.ServiceHostFactory> gerekli yapılandırmayı oluşturan ve gerçekleştiren bir web barındırma hizmeti oluşturmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="9f65b-111">To configure a web hosted service you were required to create a `System.ServiceModel.ServiceHostFactory` that created the <xref:System.ServiceModel.Activation.ServiceHostFactory> and performed any needed configuration.</span></span> <span data-ttu-id="9f65b-112">.NET 4.5 ile başlayarak WCF, hem kendi kendine barındırılan hem de web barındırılan hizmetleri kod halinde yapılandırmanın daha kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f65b-112">Starting with .NET 4.5, WCF provides an easier way to configure both self-hosted and web hosted services in code.</span></span>  
  
## <a name="the-configure-method"></a><span data-ttu-id="9f65b-113">Yapılandırma yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f65b-113">The Configure method</span></span>  
 <span data-ttu-id="9f65b-114">Hizmet uygulama sınıfınızda `Configure` aşağıdaki imzayla çağrılan genel statik bir yöntem tanımlamanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="9f65b-114">Simply define a public static method called `Configure` with the following signature in your service implementation class:</span></span>  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 <span data-ttu-id="9f65b-115">Yapılandırma yöntemi, geliştiricinin uç nokta ve davranış eklemesine olanak tanıyan bir <xref:System.ServiceModel.ServiceConfiguration> örnek alır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-115">The Configure method takes a <xref:System.ServiceModel.ServiceConfiguration> instance that enables the developer to add endpoints and behaviors.</span></span> <span data-ttu-id="9f65b-116">Bu yöntem, hizmet ana bilgisayarı açılmadan önce WCF tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-116">This method is called by WCF before the service host is opened.</span></span> <span data-ttu-id="9f65b-117">Tanımlandığında, app.config veya web.config dosyasında belirtilen hizmet yapılandırma ayarları yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="9f65b-117">When defined, any service configuration settings specified in an app.config or web.config file will be ignored.</span></span>  
  
 <span data-ttu-id="9f65b-118">Aşağıdaki kod parçacığı `Configure` yöntemi tanımlamak ve bir hizmet bitiş noktası, bir bitiş noktası davranışı ve hizmet davranışları eklemek nasıl gösteriş:</span><span class="sxs-lookup"><span data-stu-id="9f65b-118">The following code snippet illustrates how to define the `Configure` method and add a service endpoint, an endpoint behavior and service behaviors:</span></span>  
  
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
  
 <span data-ttu-id="9f65b-119">Bir hizmet için https gibi bir protokolü etkinleştirmek için, protokolü kullanan bir bitiş noktası nı açıkça ekleyebilirsiniz veya her temel adres için bir bitiş noktası ekleyen ServiceConfiguration.EnableProtocol(Binding) numaralı telefonu arayarak otomatik olarak uç noktaları ekleyebilirsiniz protokol ve tanımlanan her hizmet sözleşmesi ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="9f65b-119">To enable a protocol such as https for a service, you can either explicitly add an endpoint that uses the protocol or you can automatically add endpoints by calling ServiceConfiguration.EnableProtocol(Binding) which adds an endpoint for each base address compatible with the protocol and each service contract defined.</span></span> <span data-ttu-id="9f65b-120">Aşağıdaki kod ServiceConfiguration.EnableProtocol yönteminin nasıl kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9f65b-120">The following code illustrates how to use the ServiceConfiguration.EnableProtocol method:</span></span>  
  
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
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 <span data-ttu-id="9f65b-121"><`protocolMappings`> bölümündeki ayarlar yalnızca <xref:System.ServiceModel.ServiceConfiguration> programlı olarak uygulama uç noktaları eklenmezse kullanılır. Varsayılan uygulama yapılandırma dosyasından isteğe bağlı olarak <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> hizmet yapılandırmasını arayarak yükleyebilir ve ardından ayarları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f65b-121">The settings in the <`protocolMappings`> section are only used if no application endpoints are added to the <xref:System.ServiceModel.ServiceConfiguration> programmatically.You can optionally load the service configuration from the default application configuration file by calling <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> and then change the settings.</span></span> <span data-ttu-id="9f65b-122">Sınıf <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> ayrıca merkezi bir yapılandırma yapılandırma yüklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f65b-122">The <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> class also allows you to load configuration from a centralized configuration.</span></span> <span data-ttu-id="9f65b-123">Aşağıdaki kod, bunun nasıl uygulanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9f65b-123">The following code illustrates how to implement this:</span></span>  
  
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
> <span data-ttu-id="9f65b-124"><`system.serviceModel` <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>> <`host` `service`> etiketindeki <> ayarları yok saydığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9f65b-124">Note that <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignores <`host`> settings within the <`service`> tag of <`system.serviceModel`>.</span></span> <span data-ttu-id="9f65b-125">Kavramsal olarak, `host` <> hizmet yapılandırması ile değil, ana bilgisayar yapılandırması ile ilgilidir ve Yapılandırma yöntemi yürütülmeden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9f65b-125">Conceptually, <`host`> is about host configuration, not service configuration, and it gets loaded before the Configure method executes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f65b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f65b-126">See also</span></span>

- [<span data-ttu-id="9f65b-127">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-127">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="9f65b-128">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-128">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
- [<span data-ttu-id="9f65b-129">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-129">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="9f65b-130">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-130">Configuration</span></span>](./samples/configuration-sample.md)
- [<span data-ttu-id="9f65b-131">IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="9f65b-131">Configuration-Based Activation in IIS and WAS</span></span>](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [<span data-ttu-id="9f65b-132">Yapılandırma ve Meta Veri Desteği</span><span class="sxs-lookup"><span data-stu-id="9f65b-132">Configuration and Metadata Support</span></span>](./extending/configuration-and-metadata-support.md)
- [<span data-ttu-id="9f65b-133">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f65b-133">Configuration</span></span>](./diagnostics/exceptions-reference/configuration.md)
- [<span data-ttu-id="9f65b-134">Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="9f65b-134">How to: Specify a Service Binding in Configuration</span></span>](how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="9f65b-135">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f65b-135">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="9f65b-136">Nasıl yapılır: Yapılandırma Dosyası Kullanarak Bir Hizmet için Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="9f65b-136">How to: Publish Metadata for a Service Using a Configuration File</span></span>](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9f65b-137">Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme</span><span class="sxs-lookup"><span data-stu-id="9f65b-137">How to: Specify a Client Binding in Configuration</span></span>](how-to-specify-a-client-binding-in-configuration.md)
