---
title: Basitleştirilmiş Yapılandırma
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249636"
---
# <a name="simplified-configuration"></a><span data-ttu-id="a54a1-102">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-102">Simplified Configuration</span></span>
<span data-ttu-id="a54a1-103">Windows Communication Foundation (WCF) hizmetlerini yapılandırmak karmaşık bir görev olabilir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="a54a1-104">Birçok farklı seçenek vardır ve hangi ayarların gerekli olduğunu belirlemek her zaman kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="a54a1-105">Yapılandırma dosyaları WCF hizmetlerinin esnekliğini artırırken, aynı zamanda bulunması zor birçok sorunun kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="a54a1-106">bu sorunları giderir ve hizmet yapılandırmasının boyutunu ve karmaşıklığını azaltmanın bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a54a1-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="a54a1-107">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-107">Simplified Configuration</span></span>  
 <span data-ttu-id="a54a1-108">WCF hizmet yapılandırma dosyalarında, <`system.serviceModel`> `service` bölümü barındırılan her hizmet için <bir> öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="a54a1-109"><`service`> öğesi, her `endpoint` hizmet için maruz kalan uç noktaları ve isteğe bağlı olarak bir hizmet davranışı kümesini belirten <> öğeleri koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="a54a1-110"><`endpoint`> öğeleri, bitiş noktası tarafından maruz kalan adresi, bağlamayı ve sözleşmeyi ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="a54a1-111"><`system.serviceModel`> bölümü, hizmet `behaviors` veya bitiş noktası davranışlarını belirtmenize olanak tanıyan <bir> öğesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="a54a1-112">Aşağıdaki örnek, yapılandırma `system.serviceModel` dosyasının <> bölümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="a54a1-113"><`service`> öğesi gereksinimini kaldırarak bir WCF hizmetini yapılandırmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="a54a1-114"><`service`> bölümü eklemezseniz veya <`service`> bölümüne herhangi bir uç nokta eklemezseniz ve hizmetiniz programlı olarak herhangi bir uç nokta tanımlamazsa, her hizmet temel adresi ve hizmetinizin uyguladığı her sözleşme için otomatik olarak bir dizi varsayılan uç nokta hizmetinize eklenir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="a54a1-115">Bu uç noktaların her birinde, bitiş noktası adresi temel adrese karşılık gelir, bağlama temel adres şeması tarafından belirlenir ve sözleşme hizmetiniz tarafından uygulanan adrestir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="a54a1-116">Herhangi bir uç nokta veya hizmet davranışı belirtmeniz veya bağlayıcı ayar değişiklikleri yapmanız gerekmiyorsa, bir hizmet yapılandırma dosyası belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a54a1-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="a54a1-117">Bir hizmet iki sözleşme uygularsa ve ana bilgisayar hem HTTP hem de TCP taşımasına olanak tanırsa, hizmet ana bilgisayarı her aktarım ı kullanan her sözleşme için bir tane olmak üzere dört varsayılan uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a54a1-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="a54a1-118">Varsayılan uç noktaları oluşturmak için hizmet ana bilgisayar hangi bağlamaları kullanacağını bilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="a54a1-119">Bu ayarlar, <`protocolMappings` `system.serviceModel`> bölümünde ki <> bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="a54a1-120"><`protocolMappings`> bölümü, bağlama türlerine eşlenen aktarım protokolü düzenlerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="a54a1-121">Hizmet ana bilgisayarı, hangi bağlamanın kullanılacağını belirlemek için ona aktarılan temel adresleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="a54a1-122">Aşağıdaki örnekte <`protocolMappings`> öğesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="a54a1-123">Bağlamalar veya davranışlar gibi varsayılan yapılandırma öğelerini değiştirmek, bu varsayılan bağlamaları ve davranışları kullandıklarından, yapılandırma hiyerarşisinin alt düzeylerinde tanımlanan hizmetleri etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="a54a1-124">Bu nedenle, varsayılan bağlamaları ve davranışları değiştiren kişinin, bu değişikliklerin hiyerarşideki diğer hizmetleri etkileyebileceğinibilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a54a1-125">Internet Information Services (IIS) veya Windows Process Activation Service (WAS) kapsamında barındırılan hizmetler, sanal dizini temel adresleri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="a54a1-126">Önceki örnekte, "http" şeması ile başlayan bir taban adresi <xref:System.ServiceModel.BasicHttpBinding>ile bir bitiş noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="a54a1-127">"net.tcp" şeması ile başlayan bir taban adresi olan <xref:System.ServiceModel.NetTcpBinding>bir bitiş noktası kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="a54a1-128">Yerel bir App.config veya Web.config dosyasındaki ayarları geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a54a1-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="a54a1-129"><`protocolMappings`> bölümündeki her öğe bir şema ve bağlama belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="a54a1-130">İsteğe bağlı olarak, yapılandırma dosyasının <`bindingConfiguration` `bindings`> bölümünde bağlayıcı yapılandırma belirten bir öznitelik belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="a54a1-131">Hiçbir `bindingConfiguration` belirtilmemişse, uygun bağlama türünün anonim bağlama yapılandırması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="a54a1-132">Hizmet davranışları, <`behavior` `serviceBehaviors`> bölümlerdeki anonim <> bölümleri kullanılarak varsayılan uç noktalar için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="a54a1-133">> <`behavior` `serviceBehaviors` içindeki adsız <> öğeler, hizmet davranışlarını yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="a54a1-134">Örneğin, aşağıdaki yapılandırma dosyası ana bilgisayardaki tüm hizmetler için hizmet meta veri yayımlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="a54a1-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="a54a1-135">Bitiş noktası davranışları,> `behavior` `serviceBehaviors` <bölümlerdeki anonim <> bölümleri kullanılarak yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="a54a1-136">Aşağıdaki örnek, basitleştirilmiş yapılandırma modelini kullanan bu konunun başındakine eşdeğer bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a54a1-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="a54a1-137">Bu özellik yalnızca Istemci yapılandırması ile değil, yalnızca WCF hizmet yapılandırması ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="a54a1-138">Çoğu zaman, WCF istemci yapılandırmasvcutil.exe veya Visual Studio bir hizmet başvurusu ekleyerek gibi bir araç tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a54a1-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="a54a1-139">Bir WCF istemcisini el ile yapılandırıyorsanız yapılandırmaya bir \<istemci> öğesi eklemeniz ve aramak istediğiniz uç noktaları belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a54a1-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54a1-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a54a1-140">See also</span></span>

- [<span data-ttu-id="a54a1-141">Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="a54a1-142">Hizmetler için Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="a54a1-143">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a54a1-144">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="a54a1-145">WCF hizmetlerinin yapılandırılması</span><span class="sxs-lookup"><span data-stu-id="a54a1-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="a54a1-146">WCF Hizmetlerini Kodda Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a54a1-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
