---
title: "Basitleştirilmiş Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7d8fea550d0def93cf1d86b9d4a7d6b09afaf90d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="simplified-configuration"></a><span data-ttu-id="3e7a6-102">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-102">Simplified Configuration</span></span>
<span data-ttu-id="3e7a6-103">Yapılandırma [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Hizmetleri, karmaşık bir görev olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-103">Configuring [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services can be a complex task.</span></span> <span data-ttu-id="3e7a6-104">Çok sayıda farklı seçeneğiniz vardır ve her zaman hangi ayarların gerekli olduğunu belirlemek kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="3e7a6-105">Yapılandırma dosyaları esnekliğini artırmak sırada [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetleri de oldukları sorunları bulmak sabit sayıda kaynağı.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-105">While configuration files increase the flexibility of [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="3e7a6-106">Bu sorunu giderir ve boyutunu ve hizmet yapılandırmasını karmaşıklığını azaltmak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="3e7a6-107">Basitleştirilmiş Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-107">Simplified Configuration</span></span>  
 <span data-ttu-id="3e7a6-108">İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet yapılandırma dosyaları, <`system.serviceModel`> bölüm içeren bir <`service`> öğesi barındırılan her hizmet için.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-108">In [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="3e7a6-109"><`service`> Öğesi içeren bir koleksiyonu <`endpoint`> her hizmet ve isteğe bağlı olarak bir dizi hizmet davranışları için kullanıma sunulan uç noktaları belirtin öğeleri.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="3e7a6-110"><`endpoint`> Öğelerini bağlama, adresi belirtin ve Sözleşme, bitiş noktası tarafından ve isteğe bağlı olarak bağlama yapılandırması ve uç nokta davranışları kullanıma.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="3e7a6-111"><`system.serviceModel`> Bölümünde de içeren bir <`behaviors`> hizmet veya uç nokta davranışları belirtmenize olanak tanır öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="3e7a6-112">Aşağıdaki örnekte gösterildiği <`system.serviceModel`> bir yapılandırma dosyası bölümünü.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="3e7a6-113">yapar yapılandırma bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet gereksinimini kaldırarak daha kolay <`service`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-113"> makes configuring a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="3e7a6-114">Değil eklerseniz, bir <`service`> bölümünde veya tüm uç noktalarını eklemek bir <`service`> bölümü ve hizmetinizi değil program aracılığıyla tanımlama uç nokta sonra varsayılan uç noktalar kümesi hizmetiniz için birer tane olmak üzere otomatik olarak eklenir Hizmet taban adresi ve hizmetiniz tarafından uygulanan her bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="3e7a6-115">Her birinde Bu uç noktalar, uç nokta adresi taban adresine karşılık gelen, bağlama temel adres düzeni tarafından belirlenir ve hizmetiniz tarafından uygulanan bir sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="3e7a6-116">Herhangi bir uç noktaları veya hizmet davranışları belirtin veya bağlama ayarı değişiklik gerekmez, hizmet yapılandırma dosyası belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="3e7a6-117">Bir hizmet iki sözleşmeleri uygular ve ana bilgisayar hem HTTP hem de TCP aktarımlarını etkinleştirir, hizmet ana bilgisayarı dört varsayılan uç noktalar, her aktarım kullanarak her sözleşme için bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="3e7a6-118">Varsayılan uç hizmet ana bilgisayarını oluşturmak için kullanmak üzere hangi bağlamaları bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="3e7a6-119">Bu ayarları belirtilen bir <`protocolMappings`> içinde bölümünde <`system.serviceModel`> bölümü.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="3e7a6-120"><`protocolMappings`> Bölümüne Aktarım Protokolü düzenleri türleri bağlama için eşlenmiş bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="3e7a6-121">Hizmet ana bilgisayarı kendisine geçirilen temel adresler kullanmak için hangi bağlama belirlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="3e7a6-122">Aşağıdaki örnek kullanır <`protocolMappings`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3e7a6-123">Varsayılan yapılandırma öğelerini bağlamaları veya davranışları gibi değiştirme Hizmetleri bu varsayılan bağlamalar ve davranışları kullanabilecek beri yapılandırma hiyerarşisinin düzeylerinde tanımlı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="3e7a6-124">Bu nedenle, aktaranın varsayılan bağlamalar ve davranış değişiklikleri bu değişiklikleri hiyerarşideki diğer hizmetler etkileyebilecek farkında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e7a6-125">Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında barındırılan hizmetleri sanal dizini kendi taban adresi olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="3e7a6-126">Önceki örnekte, "http" düzeni ile başlayan bir taban adresi noktayla kullanır <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="3e7a6-127">Bir uç nokta "net.tcp" düzeni ile başlayan bir taban adresi kullanan <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="3e7a6-128">Yerel bir App.config veya Web.config dosyasında ayarlarını geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="3e7a6-129">Her öğe içinde <`protocolMappings`> bölümü, bir şema ve bağlama belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="3e7a6-130">İsteğe bağlı olarak belirtebilirsiniz bir `bindingConfiguration` içinde bir bağlaması yapılandırma belirten özniteliği <`bindings`> yapılandırma dosyası bölümünü.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="3e7a6-131">Öyle değilse `bindingConfiguration` belirtilirse, uygun bağlama türü anonim bağlama yapılandırması kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="3e7a6-132">Hizmet davranışları, varsayılan uç noktaları için anonim kullanılarak yapılandırılır <`behavior`> içindeki bölümler <`serviceBehaviors`> bölümler.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="3e7a6-133">Herhangi bir adlandırılmamış <`behavior`> içinde öğelerin <`serviceBehaviors`> Hizmet davranışları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="3e7a6-134">Örneğin, aşağıdaki yapılandırma dosyası ana bilgisayarı içindeki tüm hizmetler için hizmet meta veri yayımlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="3e7a6-135">Uç nokta davranışları anonim kullanılarak yapılandırılır <`behavior`> içindeki bölümler <`serviceBehaviors`> bölümler.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="3e7a6-136">Aşağıdaki örnek Basitleştirilmiş yapılandırma modelini kullanır, bu konunun başında bir için eşdeğer bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <bindings>  
       <basicHttpBinding>  
          <binding maxBufferSize="100"  
                   maxReceiveBufferSize="100" />  
       </basicHttpBinding>  
    </bindings>    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->  
    <!-- The service behavior with name="" will be picked up by the service -->  
    <protocolMapping>  
      <add scheme="http"     binding="basicHttpBinding" / </protocolMapping>  
  </system.serviceModel>  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e7a6-137">Bu özellik yalnızca WCF hizmeti yapılandırmasını istemci yapılandırmasını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="3e7a6-138">Çoğu kez, WCF istemci yapılandırması svcutil.exe veya Visual Studio'dan bir hizmet başvurusu ekleme gibi bir araç tarafından oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="3e7a6-139">Bir WCF istemcisi el ile yapılandırıyorsanız eklemeniz gerekir bir \<istemci > yapılandırma öğesine ve istediğiniz çağırmak için uç nokta belirtin.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7a6-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e7a6-140">See Also</span></span>  
 [<span data-ttu-id="3e7a6-141">Yapılandırma dosyalarını kullanarak hizmetleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="3e7a6-142">Hizmetler için bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="3e7a6-143">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3e7a6-144">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 [<span data-ttu-id="3e7a6-145">Windows Communication Foundation uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-145">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="3e7a6-146">WCF hizmetlerini kodda yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e7a6-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
