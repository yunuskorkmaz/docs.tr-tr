---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399451"
---
# \<system.serviceModel>
<span data-ttu-id="a7630-102">Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-102">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="a7630-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7630-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7630-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7630-104">Attributes and Elements</span></span>  
 <span data-ttu-id="a7630-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7630-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7630-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a7630-106">Attributes</span></span>  
 <span data-ttu-id="a7630-107">Yok</span><span class="sxs-lookup"><span data-stu-id="a7630-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7630-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7630-108">Child Elements</span></span>  
  
|<span data-ttu-id="a7630-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7630-109">Element</span></span>|<span data-ttu-id="a7630-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7630-110">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="a7630-111">Bu bölüm, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="a7630-111">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a7630-112">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-112">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="a7630-113">Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="a7630-113">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="a7630-114">Bu bölüm, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-114">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="a7630-115">Her giriş, benzersiz olarak tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="a7630-115">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="a7630-116">Hizmetler, kullanarak bağlama yoluyla bağlamaları kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="a7630-116">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="a7630-117">Bu bölüm, bir istemcinin hizmete bağlanmak için kullandığı uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-117">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="a7630-118">Bu bölümde, WCF ve COM birlikte çalışma için etkinleştirilen COM sözleşmeleri tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a7630-118">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="a7630-119">Bu bölüm yalnızca Machine. config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-119">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="a7630-120">Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="a7630-120">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="a7630-121">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-121">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="a7630-122">Bir davranış hem hem de bölümlerinde tanımlanmışsa `<commonBehaviors>` `<behaviors>` , \<behaviors> bölümdeki davranışa tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-122">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="a7630-123">Bu bölüm, WCF 'nin tanılama özelliklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-123">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="a7630-124">Kullanıcı izlemeyi, performans sayaçlarını ve WMI sağlayıcısını etkinleştirebilir/devre dışı bırakabilir ve özel ileti filtreleri ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-124">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="a7630-125">Bu bölüm, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantı yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-125">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="a7630-126">Bu bölüm, Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vb.) ve WCF bağlamaları arasında bir varsayılan protokol eşlemesi kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-126">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="a7630-127">Bu bölüm, gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü ve <xref:System.ServiceModel.Dispatcher.MessageFilter> bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-127">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="a7630-128">Bu bölüm, belirli bir aktarım için hizmet barındırma ortamının ne tür bir örneklenme olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-128">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="a7630-129">Bu bölüm boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7630-129">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="a7630-130">Bölüm bir hizmetler koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-130">The section contains a collection of services.</span></span> <span data-ttu-id="a7630-131">Derlemede tanımlanan her hizmet için bu öğe, `service` hizmetin ayarlarını belirten bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="a7630-131">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="a7630-132">Bu bölüm bir standart uç nokta koleksiyonunu tanımlar, bu, önceden yapılandırılmış son nokta olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-132">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="a7630-133">Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="a7630-133">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="a7630-134">Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi.</span><span class="sxs-lookup"><span data-stu-id="a7630-134">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="a7630-135">Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7630-135">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="a7630-136">Bu bölüm, bir iş akışı hizmeti için izleme ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-136">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7630-137">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a7630-137">Parent Elements</span></span>  
  
|<span data-ttu-id="a7630-138">Öğe</span><span class="sxs-lookup"><span data-stu-id="a7630-138">Element</span></span>|<span data-ttu-id="a7630-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7630-139">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="a7630-140">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a7630-140">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7630-141">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7630-141">Remarks</span></span>  
 <span data-ttu-id="a7630-142">WCF, diğer ürünlerin yapılandırma bölümlerine öğe eklemez.</span><span class="sxs-lookup"><span data-stu-id="a7630-142">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="a7630-143">WCF Hizmetleri, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a7630-143">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a7630-144">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-144">An assembly can contain any number of services.</span></span> <span data-ttu-id="a7630-145">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="a7630-145">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="a7630-146">Bölümü ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-146">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="a7630-147">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a7630-147">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="a7630-148">Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel CLR türünü tanımlar; Ancak, <xref:System.ServiceModel.ServiceContractAttribute> clr türü gereksinimini geçersiz kılmak için bir üzerinde ConfigurationName özelliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7630-148">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="a7630-149">`behaviorConfiguration`Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7630-149">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="a7630-150">Bir hizmet tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-150">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="a7630-151">Bu öznitelik tarafından belirtilen davranışın aynı yapılandırma dosyası kapsamında (yani aynı dosya veya bir üst dosya) tanımlanmış bir hizmet davranışına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7630-151">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="a7630-152">Her hizmet bir öğede tanımlanan bir veya daha fazla uç noktayı kullanıma sunar `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="a7630-152">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="a7630-153">Her uç noktanın kendi adresi ve bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="a7630-153">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="a7630-154">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a7630-154">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="a7630-155">Bağlamalar, ve öznitelikleri birleşimi aracılığıyla uç noktalara bağlanır `name` `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="a7630-155">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="a7630-156">`binding`Özniteliği, bağlamanın hangi bölümünde tanımlandığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-156">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="a7630-157">`bindingConfiguration`Özniteliği, bağlama bölümünde hangi yapılandırılan bağlamanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a7630-157">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="a7630-158">Bağlama bölümü, yapılandırılmış çeşitli bağlamaları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a7630-158">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7630-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7630-159">Example</span></span>  
 <span data-ttu-id="a7630-160">Bu, WCF yapılandırma dosyasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a7630-160">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="a7630-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7630-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
