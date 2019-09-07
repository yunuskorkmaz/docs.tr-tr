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
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399451"
---
# <a name="systemservicemodel"></a><span data-ttu-id="87e3c-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="87e3c-102">\<system.serviceModel></span></span>
<span data-ttu-id="87e3c-103">Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

<span data-ttu-id="87e3c-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87e3c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87e3c-105">&nbsp;&nbsp; **\<System. serviceModel >**</span><span class="sxs-lookup"><span data-stu-id="87e3c-105">&nbsp;&nbsp;**\<system.serviceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e3c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87e3c-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87e3c-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e3c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="87e3c-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87e3c-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87e3c-109">Attributes</span></span>  
 <span data-ttu-id="87e3c-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="87e3c-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87e3c-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e3c-111">Child Elements</span></span>  
  
|<span data-ttu-id="87e3c-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="87e3c-112">Element</span></span>|<span data-ttu-id="87e3c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87e3c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87e3c-114">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="87e3c-114">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="87e3c-115">Bu bölüm, ve `endpointBehaviors` `serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-115">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="87e3c-116">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-116">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="87e3c-117">Her davranış öğesi, benzersiz `name` özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-117">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="87e3c-118">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="87e3c-118">\<bindings></span></span>](bindings.md)|<span data-ttu-id="87e3c-119">Bu bölüm, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-119">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="87e3c-120">Her giriş, benzersiz `name`olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-120">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="87e3c-121">Hizmetler, `name`kullanarak bağlama yoluyla bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-121">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="87e3c-122">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="87e3c-122">\<client></span></span>](client.md)|<span data-ttu-id="87e3c-123">Bu bölüm, bir istemcinin hizmete bağlanmak için kullandığı uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-123">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="87e3c-124">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="87e3c-124">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="87e3c-125">Bu bölümde, WCF ve COM birlikte çalışma için etkinleştirilen COM sözleşmeleri tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-125">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="87e3c-126">\<Commondavranışlar ></span><span class="sxs-lookup"><span data-stu-id="87e3c-126">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="87e3c-127">Bu bölüm yalnızca Machine. config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-127">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="87e3c-128">`endpointBehaviors` Ve`serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-128">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="87e3c-129">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-129">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="87e3c-130">Bir davranış hem `<commonBehaviors>` `<behaviors>` hem de bölümlerinde tanımlanmışsa \<, davranışlar > bölümündeki davranışa verilen tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-130">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="87e3c-131">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="87e3c-131">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="87e3c-132">Bu bölüm, WCF 'nin tanılama özelliklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="87e3c-133">Kullanıcı izlemeyi, performans sayaçlarını ve WMI sağlayıcısını etkinleştirebilir/devre dışı bırakabilir ve özel ileti filtreleri ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="87e3c-134">\<uzantılar ></span><span class="sxs-lookup"><span data-stu-id="87e3c-134">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="87e3c-135">Bu bölüm, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantı yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-135">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="87e3c-136">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="87e3c-136">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="87e3c-137">Bu bölüm, Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vb.) ve WCF bağlamaları arasında bir varsayılan protokol eşlemesi kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-137">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="87e3c-138">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="87e3c-138">\<routing></span></span>](routing.md)|<span data-ttu-id="87e3c-139">Bu bölüm, gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtreleri kümesi tanımlar ve bu sırada ileti göndermek için hedef bitiş noktalarını tanımlayan yönlendirme tablolarının yanı sıra bir Filtre eşleşmeleri.</span><span class="sxs-lookup"><span data-stu-id="87e3c-139">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="87e3c-140">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="87e3c-140">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="87e3c-141">Bu bölüm, belirli bir aktarım için hizmet barındırma ortamının ne tür bir örneklenme olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-141">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="87e3c-142">Bu bölüm boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-142">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="87e3c-143">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="87e3c-143">\<services></span></span>](services.md)|<span data-ttu-id="87e3c-144">Bölüm bir hizmetler koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-144">The section contains a collection of services.</span></span> <span data-ttu-id="87e3c-145">Derlemede tanımlanan her hizmet için bu öğe, hizmetin ayarlarını belirten bir `service` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-145">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="87e3c-146">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="87e3c-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="87e3c-147">Bu bölüm bir standart uç nokta koleksiyonunu tanımlar, bu, önceden yapılandırılmış son nokta olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-147">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="87e3c-148">Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="87e3c-148">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="87e3c-149">Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi.</span><span class="sxs-lookup"><span data-stu-id="87e3c-149">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="87e3c-150">Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87e3c-150">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="87e3c-151">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="87e3c-151">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="87e3c-152">Bu bölüm, bir iş akışı hizmeti için izleme ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-152">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87e3c-153">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87e3c-153">Parent Elements</span></span>  
  
|<span data-ttu-id="87e3c-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="87e3c-154">Element</span></span>|<span data-ttu-id="87e3c-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87e3c-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87e3c-156">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="87e3c-156">\<configuration></span></span>|<span data-ttu-id="87e3c-157">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="87e3c-157">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e3c-158">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87e3c-158">Remarks</span></span>  
 <span data-ttu-id="87e3c-159">WCF, diğer ürünlerin yapılandırma bölümlerine öğe eklemez.</span><span class="sxs-lookup"><span data-stu-id="87e3c-159">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="87e3c-160">WCF Hizmetleri, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-160">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="87e3c-161">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-161">An assembly can contain any number of services.</span></span> <span data-ttu-id="87e3c-162">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-162">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="87e3c-163">Bölümü ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-163">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="87e3c-164">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-164">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="87e3c-165">Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel CLR türünü tanımlar; Ancak, clr türü gereksinimini geçersiz kılmak için bir <xref:System.ServiceModel.ServiceContractAttribute> üzerinde ConfigurationName özelliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87e3c-165">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="87e3c-166">`behaviorConfiguration` Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-166">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="87e3c-167">Bir hizmet tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-167">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="87e3c-168">Bu öznitelik tarafından belirtilen davranışın aynı yapılandırma dosyası kapsamında (yani aynı dosya veya bir üst dosya) tanımlanmış bir hizmet davranışına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-168">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="87e3c-169">Her hizmet bir `endpoint` öğede tanımlanan bir veya daha fazla uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-169">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="87e3c-170">Her uç noktanın kendi adresi ve bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-170">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="87e3c-171">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-171">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="87e3c-172">Bağlamalar, ve `name` `bindingConfiguration`öznitelikleri birleşimi aracılığıyla uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="87e3c-172">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="87e3c-173">`binding` Özniteliği, bağlamanın hangi bölümünde tanımlandığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-173">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="87e3c-174">`bindingConfiguration` Özniteliği, bağlama bölümünde hangi yapılandırılan bağlamanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="87e3c-174">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="87e3c-175">Bağlama bölümü, yapılandırılmış çeşitli bağlamaları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-175">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87e3c-176">Örnek</span><span class="sxs-lookup"><span data-stu-id="87e3c-176">Example</span></span>  
 <span data-ttu-id="87e3c-177">Bu, WCF yapılandırma dosyasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="87e3c-177">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="87e3c-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87e3c-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
