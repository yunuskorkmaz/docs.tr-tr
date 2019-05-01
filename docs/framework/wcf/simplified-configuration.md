---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 13cf8bd46ef3aabb011cb2ddd207963235468662
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967901"
---
# <a name="simplified-configuration"></a><span data-ttu-id="04b7a-102">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-102">Simplified Configuration</span></span>
<span data-ttu-id="04b7a-103">Windows Communication Foundation (WCF) hizmetlerini yapılandırmak, karmaşık bir görev olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="04b7a-104">Çok sayıda farklı seçeneğiniz vardır ve her zaman gerekli ayarları belirlemek kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="04b7a-105">Yapılandırma dosyalarını WCF hizmetleri esnekliğini artırın, ancak bunlar ayrıca sorunları bulmak sabit bir çoğu için işlemcilerden kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="04b7a-106">Bu sorunları giderir ve büyüklüğü ve karmaşıklığı ile hizmet yapılandırmasının azaltmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b7a-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="04b7a-107">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-107">Simplified Configuration</span></span>  
 <span data-ttu-id="04b7a-108">WCF hizmeti yapılandırma dosyalarında <`system.serviceModel`> bölüm içeren bir <`service`> barındırılan her hizmet için öğesi.</span><span class="sxs-lookup"><span data-stu-id="04b7a-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="04b7a-109"><`service`> Öğesi içeren bir koleksiyon, <`endpoint`> her hizmet ve isteğe bağlı olarak bir dizi hizmet davranışları için açık Uç noktalara belirten öğeler.</span><span class="sxs-lookup"><span data-stu-id="04b7a-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="04b7a-110"><`endpoint`> Elementleri bağlama, adresi ve Sözleşme, uç nokta ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışları ortaya.</span><span class="sxs-lookup"><span data-stu-id="04b7a-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="04b7a-111"><`system.serviceModel`> Bölümü içerecek bir <`behaviors`> öğesi hizmet veya uç nokta davranışları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b7a-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="04b7a-112">Aşağıdaki örnekte gösterildiği <`system.serviceModel`> yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="04b7a-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="04b7a-113">gereksinimini ortadan kaldırarak daha kolay bir WCF hizmeti yapılandırma yapar <`service`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="04b7a-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="04b7a-114">Değil eklerseniz bir <`service`> bölümünde veya tüm uç noktaların ekleme bir <`service`> bölüm ve hizmetinizi programlı olarak tanımlamıyor tüm uç noktaları ve hizmetiniz için birer tane olmak üzere otomatik olarak bir varsayılan uç nokta kümesine eklenir Hizmet temel adresi ve hizmetiniz tarafından uygulanan her bir sözleşme için.</span><span class="sxs-lookup"><span data-stu-id="04b7a-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="04b7a-115">Her birinde Bu uç noktaları, uç nokta adresini temel adresine karşılık gelen, bağlama temel adres düzeni tarafından belirlenir ve hizmetiniz tarafından uygulanan bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="04b7a-116">Herhangi bir uç noktaları veya hizmet davranışları belirtin veya bağlama ayarı değişiklik gerekmez, hizmet yapılandırma dosyasını belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="04b7a-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="04b7a-117">Bir hizmeti iki sözleşmeleri uygular ve ana bilgisayar hem HTTP hem de TCP aktarımlarını etkinleştirir dört varsayılan uç noktalar, her aktarım kullanarak her bir sözleşme için bir hizmet konağı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="04b7a-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="04b7a-118">Hizmet ana bilgisayarı varsayılan uç noktalar oluşturmak için kullanılacak hangi bağlamaları bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="04b7a-119">Bu ayarları belirtilmiş bir <`protocolMappings`> içinde bölümünde <`system.serviceModel`> bölümü.</span><span class="sxs-lookup"><span data-stu-id="04b7a-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="04b7a-120"><`protocolMappings`> Bölümü, taşıma protokol şemaları bağlama türleri için eşlenmiş bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="04b7a-121">Hizmet ana bilgisayarını kullanmak için hangi bağlama belirlemek için geçirilen temel adresler kullanır.</span><span class="sxs-lookup"><span data-stu-id="04b7a-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="04b7a-122">Aşağıdaki örnekte <`protocolMappings`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="04b7a-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="04b7a-123">Varsayılan bağlamaları veya davranışlar gibi yapılandırma öğelerini değiştirme, bu varsayılan bağlamaları ve davranışları kullanabilecek beri yapılandırma hiyerarşisinde daha düşük düzeylerde tanımlı hizmetleri etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="04b7a-124">Bu nedenle, kişi varsayılan bağlamaları ve davranışları değiştirir bu değişiklikleri hiyerarşideki diğer hizmetleri etkileyebilir farkında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04b7a-125">Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında barındırılan hizmetler, sanal dizin kendi taban adresi olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="04b7a-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="04b7a-126">Önceki örnekte, "http" düzeni ile başlayan bir taban adresi ile bir uç nokta kullanan <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="04b7a-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="04b7a-127">"Net.tcp" düzeni başlatan temel adresine sahip bir uç nokta kullanan <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="04b7a-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="04b7a-128">Yerel bir App.config veya Web.config dosyasındaki ayarları geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04b7a-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="04b7a-129">Her öğe içinde <`protocolMappings`> bölümü, bir şema ve bağlama belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="04b7a-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="04b7a-130">İsteğe bağlı olarak belirtebilirsiniz bir `bindingConfiguration` içinde bir bağlama yapılandırmasını belirten Öznitelik <`bindings`> yapılandırma dosyası bölümünü.</span><span class="sxs-lookup"><span data-stu-id="04b7a-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="04b7a-131">Hayır ise `bindingConfiguration` belirtilirse, uygun bağlama türü anonim bir bağlama yapılandırmasını kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04b7a-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="04b7a-132">Hizmet davranışları, varsayılan uç noktaları için anonim kullanılarak yapılandırılır <`behavior`> içinde bölümler <`serviceBehaviors`> bölümler.</span><span class="sxs-lookup"><span data-stu-id="04b7a-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="04b7a-133">Tüm adlandırılmamış <`behavior`> öğeleri içinde <`serviceBehaviors`> Hizmet davranışları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04b7a-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="04b7a-134">Örneğin, aşağıdaki yapılandırma dosyası, konak içindeki tüm hizmetleri için hizmet meta verileri yayımlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="04b7a-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="04b7a-135">Uç nokta davranışları, anonim kullanılarak yapılandırılır <`behavior`> içinde bölümler <`serviceBehaviors`> bölümler.</span><span class="sxs-lookup"><span data-stu-id="04b7a-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="04b7a-136">Aşağıdaki örnek, Basitleştirilmiş yapılandırma modelini kullanan bu konunun başında bir eşdeğer bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="04b7a-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="04b7a-137">Bu özellik yalnızca WCF Hizmeti Yapılandırması istemci yapılandırmasını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="04b7a-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="04b7a-138">Çoğu durumda, WCF istemci yapılandırması svcutil.exe veya Visual Studio'dan bir hizmet başvurusu ekleme gibi bir araç tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="04b7a-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="04b7a-139">Bir WCF istemcisi elle yapılandırıyorsanız eklemeniz gerekecektir bir \<istemci > yapılandırma öğesi ve çağırmak istediğiniz uç nokta belirtin.</span><span class="sxs-lookup"><span data-stu-id="04b7a-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04b7a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04b7a-140">See also</span></span>

- [<span data-ttu-id="04b7a-141">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [<span data-ttu-id="04b7a-142">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="04b7a-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="04b7a-144">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)
- [<span data-ttu-id="04b7a-145">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="04b7a-146">Code’da WCF Hizmetlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="04b7a-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
