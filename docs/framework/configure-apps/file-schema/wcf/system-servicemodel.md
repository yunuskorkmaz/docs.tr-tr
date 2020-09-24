---
title: <system.serviceModel>
description: WCF hizmetini ve istemci uygulamalarını yapılandırmanızı sağlayan WCF ServiceModel yapılandırma öğeleri hakkında bilgi edinin.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 44966ed9ee3abb3d1babdf09dd44f087376ada55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158688"
---
# \<system.serviceModel>

<span data-ttu-id="361c2-103">Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="361c2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="361c2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="361c2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="361c2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="361c2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="361c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="361c2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="361c2-107">Attributes</span></span>  

 <span data-ttu-id="361c2-108">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="361c2-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="361c2-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="361c2-109">Child Elements</span></span>  
  
|<span data-ttu-id="361c2-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="361c2-110">Element</span></span>|<span data-ttu-id="361c2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361c2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="361c2-112">Bu bölüm, ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="361c2-112">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="361c2-113">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-113">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="361c2-114">Her davranış öğesi, benzersiz özniteliği tarafından tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="361c2-114">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="361c2-115">Bu bölüm, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-115">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="361c2-116">Her giriş, benzersiz olarak tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="361c2-116">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="361c2-117">Hizmetler, kullanarak bağlama yoluyla bağlamaları kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="361c2-117">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="361c2-118">Bu bölüm, bir istemcinin hizmete bağlanmak için kullandığı uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-118">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="361c2-119">Bu bölümde, WCF ve COM birlikte çalışma için etkinleştirilen COM sözleşmeleri tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="361c2-119">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="361c2-120">Bu bölüm yalnızca machine.config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-120">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="361c2-121">Ve adlı iki alt koleksiyonu tanımlar `endpointBehaviors` `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="361c2-121">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="361c2-122">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-122">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="361c2-123">Bir davranış hem hem de bölümlerinde tanımlanmışsa `<commonBehaviors>` `<behaviors>` , \<behaviors> bölümdeki davranışa tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-123">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="361c2-124">Bu bölüm, WCF 'nin tanılama özelliklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-124">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="361c2-125">Kullanıcı izlemeyi, performans sayaçlarını ve WMI sağlayıcısını etkinleştirebilir/devre dışı bırakabilir ve özel ileti filtreleri ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-125">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="361c2-126">Bu bölüm, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantı yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-126">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="361c2-127">Bu bölüm, Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vb.) ve WCF bağlamaları arasında bir varsayılan protokol eşlemesi kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-127">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="361c2-128">Bu bölüm, gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF) türünü ve <xref:System.ServiceModel.Dispatcher.MessageFilter> bir filtre eşleştiğinde ileti göndermek için hedef uç noktalarını tanımlayan yönlendirme tablolarını belirleyen bir yönlendirme filtreleri kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-128">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="361c2-129">Bu bölüm, belirli bir aktarım için hizmet barındırma ortamının ne tür bir örneklenme olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-129">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="361c2-130">Bu bölüm boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="361c2-130">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="361c2-131">Bölüm bir hizmetler koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-131">The section contains a collection of services.</span></span> <span data-ttu-id="361c2-132">Derlemede tanımlanan her hizmet için bu öğe, `service` hizmetin ayarlarını belirten bir öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="361c2-132">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="361c2-133">Bu bölüm bir standart uç nokta koleksiyonunu tanımlar, bu, önceden yapılandırılmış son nokta olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-133">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="361c2-134">Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="361c2-134">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="361c2-135">Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi.</span><span class="sxs-lookup"><span data-stu-id="361c2-135">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="361c2-136">Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="361c2-136">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="361c2-137">Bu bölüm, bir iş akışı hizmeti için izleme ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-137">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="361c2-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="361c2-138">Parent Elements</span></span>  
  
|<span data-ttu-id="361c2-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="361c2-139">Element</span></span>|<span data-ttu-id="361c2-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="361c2-140">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="361c2-141">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="361c2-141">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="361c2-142">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="361c2-142">Remarks</span></span>  

 <span data-ttu-id="361c2-143">WCF, diğer ürünlerin yapılandırma bölümlerine öğe eklemez.</span><span class="sxs-lookup"><span data-stu-id="361c2-143">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="361c2-144">WCF Hizmetleri, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="361c2-144">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="361c2-145">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-145">An assembly can contain any number of services.</span></span> <span data-ttu-id="361c2-146">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="361c2-146">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="361c2-147">Bölümü ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-147">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="361c2-148">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="361c2-148">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="361c2-149">Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel CLR türünü tanımlar; Ancak, <xref:System.ServiceModel.ServiceContractAttribute> clr türü gereksinimini geçersiz kılmak için bir üzerinde ConfigurationName özelliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="361c2-149">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="361c2-150">`behaviorConfiguration`Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="361c2-150">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="361c2-151">Bir hizmet tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-151">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="361c2-152">Bu öznitelik tarafından belirtilen davranışın aynı yapılandırma dosyası kapsamında (yani aynı dosya veya bir üst dosya) tanımlanmış bir hizmet davranışına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="361c2-152">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="361c2-153">Her hizmet bir öğede tanımlanan bir veya daha fazla uç noktayı kullanıma sunar `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="361c2-153">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="361c2-154">Her uç noktanın kendi adresi ve bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="361c2-154">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="361c2-155">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="361c2-155">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="361c2-156">Bağlamalar, ve öznitelikleri birleşimi aracılığıyla uç noktalara bağlanır `name` `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="361c2-156">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="361c2-157">`binding`Özniteliği, bağlamanın hangi bölümünde tanımlandığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-157">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="361c2-158">`bindingConfiguration`Özniteliği, bağlama bölümünde hangi yapılandırılan bağlamanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="361c2-158">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="361c2-159">Bağlama bölümü, yapılandırılmış çeşitli bağlamaları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="361c2-159">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="361c2-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="361c2-160">Example</span></span>  

 <span data-ttu-id="361c2-161">Bu, WCF yapılandırma dosyasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="361c2-161">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="361c2-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="361c2-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
