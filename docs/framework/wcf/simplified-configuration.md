---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 3bed6fe961712c976d5e1446ace43e7073036697
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423717"
---
# <a name="simplified-configuration"></a><span data-ttu-id="664bf-102">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-102">Simplified Configuration</span></span>
<span data-ttu-id="664bf-103">Windows Communication Foundation (WCF) hizmetleri yapılandırmak karmaşık bir görev olabilir.</span><span class="sxs-lookup"><span data-stu-id="664bf-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="664bf-104">Birçok farklı seçenek vardır ve hangi ayarların gerekli olduğunu belirlemek her zaman kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="664bf-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="664bf-105">Yapılandırma dosyaları WCF hizmetlerinin esnekliğini artırırken, ayrıca sorunları bulmak için çok zor olan kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="664bf-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="664bf-106">bu sorunları ele almaktadır ve hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="664bf-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="664bf-107">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-107">Simplified Configuration</span></span>  
 <span data-ttu-id="664bf-108">WCF hizmeti yapılandırma dosyalarında < `system.serviceModel` > bölümü barındırılan her hizmet için bir < `service` > öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="664bf-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="664bf-109">`service`> öğesi, her bir hizmet için sunulan uç noktaları ve isteğe bağlı olarak bir hizmet davranışı kümesini belirten <`endpoint`> öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="664bf-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="664bf-110"><`endpoint`> öğeleri, uç nokta tarafından kullanıma sunulan adresi, bağlamayı ve sözleşmeyi belirtir ve isteğe bağlı olarak yapılandırma ve uç nokta davranışları bağlama.</span><span class="sxs-lookup"><span data-stu-id="664bf-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="664bf-111">`system.serviceModel`> bölümü Ayrıca hizmet veya uç nokta davranışları belirtmenize izin veren bir <`behaviors`> öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="664bf-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="664bf-112">Aşağıdaki örnek, bir yapılandırma dosyasının < `system.serviceModel` > bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="664bf-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="664bf-113">, <`service`> öğesi gereksinimini kaldırarak bir WCF hizmetini yapılandırmayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="664bf-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="664bf-114">Bir < `service` > bölümü ekleyemez veya bir < `service` > bölümünde herhangi bir uç nokta eklerseniz ve hizmetiniz program aracılığıyla herhangi bir uç nokta tanımlamıyor, her hizmet temel adresi için bir varsayılan uç nokta kümesi otomatik olarak hizmetinize eklenir ve hizmetiniz tarafından uygulanan her sözleşme için.</span><span class="sxs-lookup"><span data-stu-id="664bf-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="664bf-115">Bu uç noktaların her birinde, uç nokta adresi temel adrese karşılık gelir, bağlama ise temel adres düzeni tarafından belirlenir ve sözleşme hizmetiniz tarafından uygulanan bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="664bf-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="664bf-116">Herhangi bir uç nokta veya hizmet davranışı belirtmeniz veya herhangi bir bağlama ayarı değişikliği yapmanız gerekmiyorsa, bir hizmet yapılandırma dosyası belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="664bf-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="664bf-117">Bir hizmet iki sözleşme uygularsa ve ana bilgisayar hem HTTP hem de TCP taşımalarını etkinleştirse, hizmet ana bilgisayarı her bir taşıyıcı kullanan her bir sözleşme için dört varsayılan uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="664bf-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="664bf-118">Varsayılan uç noktalar oluşturmak için hizmet ana bilgisayarının hangi bağlamaları kullanacağınızı bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="664bf-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="664bf-119">Bu ayarlar < `system.serviceModel` > bölümündeki bir < `protocolMappings` > bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="664bf-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="664bf-120"><`protocolMappings`> bölümü, bağlama türlerine eşlenmiş Aktarım Protokolü düzenlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="664bf-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="664bf-121">Hizmet ana bilgisayarı, hangi bağlamanın kullanılacağını belirleyen, kendisine geçirilen temel adresleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="664bf-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="664bf-122">Aşağıdaki örnek < `protocolMappings` > öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="664bf-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="664bf-123">Bağlamalar veya davranışlar gibi varsayılan yapılandırma öğelerinin değiştirilmesi, bu varsayılan bağlamaları ve davranışları kullandıklarından, yapılandırma hiyerarşisinin daha düşük düzeylerinde tanımlanan Hizmetleri etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="664bf-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="664bf-124">Bu nedenle, varsayılan bağlamaları ve davranışları değiştirmenin, bu değişikliklerin hiyerarşideki diğer hizmetleri etkileyebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="664bf-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="664bf-125">Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında barındırılan hizmetler, sanal dizini kendi temel adresleri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="664bf-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="664bf-126">Önceki örnekte, "http" düzeniyle başlayan temel adrese sahip bir uç nokta <xref:System.ServiceModel.BasicHttpBinding> kullanır.</span><span class="sxs-lookup"><span data-stu-id="664bf-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="664bf-127">Temel adresi "net. TCP" düzeniyle başlayan bir uç nokta, <xref:System.ServiceModel.NetTcpBinding> kullanır.</span><span class="sxs-lookup"><span data-stu-id="664bf-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="664bf-128">Yerel bir App. config veya Web. config dosyasındaki ayarları geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="664bf-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="664bf-129"><`protocolMappings`> bölümündeki her öğe bir düzen ve bir bağlama belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="664bf-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="664bf-130">İsteğe bağlı olarak, yapılandırma dosyasının < `bindings` > bölümünde bir bağlama yapılandırması belirten `bindingConfiguration` özniteliği belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="664bf-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="664bf-131">`bindingConfiguration` belirtilmemişse, uygun bağlama türünün adsız bağlama yapılandırması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="664bf-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="664bf-132">Hizmet davranışları, < `serviceBehaviors` > bölümlerinde anonim < `behavior` > bölümleri kullanılarak varsayılan uç noktalar için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="664bf-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="664bf-133">`serviceBehaviors`> içindeki adlandırılmamış <`behavior`> öğeleri hizmet davranışlarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="664bf-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="664bf-134">Örneğin, aşağıdaki yapılandırma dosyası konak içindeki tüm hizmetler için hizmet meta verileri yayımlamayı mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="664bf-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="664bf-135">Uç nokta davranışları < `serviceBehaviors` > bölümlerinde anonim < `behavior` > bölümleri kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="664bf-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="664bf-136">Aşağıdaki örnek, Basitleştirilmiş yapılandırma modelini kullanan bu konunun başındaki bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="664bf-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="664bf-137">Bu özellik yalnızca WCF hizmeti yapılandırmasıyla ilgilidir, istemci yapılandırması değildir.</span><span class="sxs-lookup"><span data-stu-id="664bf-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="664bf-138">Çoğu kez, WCF istemci yapılandırması Svcutil. exe gibi bir araçla veya Visual Studio 'dan bir hizmet başvurusu eklenerek oluşturulacaktır.</span><span class="sxs-lookup"><span data-stu-id="664bf-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="664bf-139">Bir WCF istemcisini el ile yapılandırıyorsanız, yapılandırmaya bir \<client > öğesi eklemeniz ve çağırmak istediğiniz uç noktaları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="664bf-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664bf-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="664bf-140">See also</span></span>

- [<span data-ttu-id="664bf-141">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="664bf-142">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="664bf-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="664bf-144">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="664bf-145">WCF hizmetlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="664bf-146">Code’da WCF Hizmetlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="664bf-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
