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
ms.openlocfilehash: 4fa6916437bb569029efe270ba8296703d89c539
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938912"
---
# <a name="systemservicemodel"></a><span data-ttu-id="f6c2c-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6c2c-102">\<system.serviceModel></span></span>
<span data-ttu-id="f6c2c-103">Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6c2c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6c2c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6c2c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6c2c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f6c2c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6c2c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6c2c-107">Attributes</span></span>  
 <span data-ttu-id="f6c2c-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f6c2c-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6c2c-109">Child Elements</span></span>  
  
|<span data-ttu-id="f6c2c-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6c2c-110">Element</span></span>|<span data-ttu-id="f6c2c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6c2c-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6c2c-112">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-112">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="f6c2c-113">Bu bölüm, ve `endpointBehaviors` `serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="f6c2c-114">Her koleksiyon, sırasıyla bitiş noktaları ve hizmetler tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="f6c2c-115">Her davranış öğesi, benzersiz `name` özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="f6c2c-116">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-116">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f6c2c-117">Bu bölüm, standart ve özel bağlamaların bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="f6c2c-118">Her giriş, benzersiz `name`olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="f6c2c-119">Hizmetler, `name`kullanarak bağlama yoluyla bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="f6c2c-120">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-120">\<client></span></span>](client.md)|<span data-ttu-id="f6c2c-121">Bu bölüm, bir istemcinin hizmete bağlanmak için kullandığı uç noktaların listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="f6c2c-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="f6c2c-122">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="f6c2c-123">Bu bölümde, WCF ve COM birlikte çalışma için etkinleştirilen COM sözleşmeleri tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="f6c2c-124">\<Commondavranışlar ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-124">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="f6c2c-125">Bu bölüm yalnızca Machine. config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="f6c2c-126">`endpointBehaviors` Ve`serviceBehaviors`adlı iki alt koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="f6c2c-127">Her koleksiyon, sırasıyla makinedeki tüm WCF uç noktaları ve Hizmetleri tarafından tüketilen davranış öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="f6c2c-128">Bir davranış hem `<commonBehaviors>` `<behaviors>` hem de bölümlerinde tanımlanmışsa \<, davranışlar > bölümündeki davranışa verilen tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="f6c2c-129">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-129">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="f6c2c-130">Bu bölüm, WCF 'nin tanılama özelliklerinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="f6c2c-131">Kullanıcı izlemeyi, performans sayaçlarını ve WMI sağlayıcısını etkinleştirebilir/devre dışı bırakabilir ve özel ileti filtreleri ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="f6c2c-132">\<uzantılar ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-132">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="f6c2c-133">Bu bölüm, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantı yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="f6c2c-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-134">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="f6c2c-135">Bu bölüm, Aktarım Protokolü şemaları (örn. http, net. TCP, net. pipe, vb.) ve WCF bağlamaları arasında bir varsayılan protokol eşlemesi kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="f6c2c-136">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-136">\<routing></span></span>](routing.md)|<span data-ttu-id="f6c2c-137">Bu bölüm, gelen iletileri değerlendirirken kullanılacak Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> türünü belirleyen bir yönlendirme filtreleri kümesi tanımlar ve bu sırada ileti göndermek için hedef bitiş noktalarını tanımlayan yönlendirme tablolarının yanı sıra bir Filtre eşleşmeleri.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="f6c2c-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-138">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="f6c2c-139">Bu bölüm, belirli bir aktarım için hizmet barındırma ortamının ne tür bir örneklenme olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="f6c2c-140">Bu bölüm boşsa, varsayılan tür kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="f6c2c-141">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-141">\<services></span></span>](services.md)|<span data-ttu-id="f6c2c-142">Bölüm bir hizmetler koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-142">The section contains a collection of services.</span></span> <span data-ttu-id="f6c2c-143">Derlemede tanımlanan her hizmet için bu öğe, hizmetin ayarlarını belirten bir `service` öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="f6c2c-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-144">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="f6c2c-145">Bu bölüm bir standart uç nokta koleksiyonunu tanımlar, bu, önceden yapılandırılmış son nokta olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="f6c2c-146">Standart bir uç noktada bir veya daha fazla adres, bağlama ve anlaşma özniteliği sabit bir değere ayarlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="f6c2c-147">Örneğin, bulma uç noktasında sözleşmenin düzeltilmesi.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="f6c2c-148">Ayrıca, özel bağlamaları tanımlamaya benzer yeni özelliklerle hizmet uç noktasını genişletmek için standart uç noktaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="f6c2c-149">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-149">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="f6c2c-150">Bu bölüm, bir iş akışı hizmeti için izleme ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6c2c-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6c2c-151">Parent Elements</span></span>  
  
|<span data-ttu-id="f6c2c-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6c2c-152">Element</span></span>|<span data-ttu-id="f6c2c-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6c2c-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6c2c-154">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f6c2c-154">\<configuration></span></span>|<span data-ttu-id="f6c2c-155">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6c2c-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6c2c-156">Remarks</span></span>  
 <span data-ttu-id="f6c2c-157">WCF, diğer ürünlerin yapılandırma bölümlerine öğe eklemez.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="f6c2c-158">WCF Hizmetleri, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="f6c2c-159">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="f6c2c-160">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="f6c2c-161">Bölümü ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="f6c2c-162">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="f6c2c-163">Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel CLR türünü tanımlar; Ancak, clr türü gereksinimini geçersiz kılmak için bir <xref:System.ServiceModel.ServiceContractAttribute> üzerinde ConfigurationName özelliğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="f6c2c-164">`behaviorConfiguration` Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="f6c2c-165">Bir hizmet tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="f6c2c-166">Bu öznitelik tarafından belirtilen davranışın aynı yapılandırma dosyası kapsamında (yani aynı dosya veya bir üst dosya) tanımlanmış bir hizmet davranışına bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="f6c2c-167">Her hizmet bir `endpoint` öğede tanımlanan bir veya daha fazla uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="f6c2c-168">Her uç noktanın kendi adresi ve bağlaması vardır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="f6c2c-169">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="f6c2c-170">Bağlamalar, ve `name` `bindingConfiguration`öznitelikleri birleşimi aracılığıyla uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="f6c2c-171">`binding` Özniteliği, bağlamanın hangi bölümünde tanımlandığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="f6c2c-172">`bindingConfiguration` Özniteliği, bağlama bölümünde hangi yapılandırılan bağlamanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="f6c2c-173">Bağlama bölümü, yapılandırılmış çeşitli bağlamaları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6c2c-174">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6c2c-174">Example</span></span>  
 <span data-ttu-id="f6c2c-175">Bu, WCF yapılandırma dosyasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-175">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6c2c-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6c2c-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
