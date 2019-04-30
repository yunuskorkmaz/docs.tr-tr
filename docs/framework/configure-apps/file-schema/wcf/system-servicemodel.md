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
ms.openlocfilehash: c176f7f470cc65bb135e5f92935102e09c7e8485
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758450"
---
# <a name="systemservicemodel"></a><span data-ttu-id="3a8d6-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3a8d6-102">\<system.serviceModel></span></span>
<span data-ttu-id="3a8d6-103">Bu yapılandırma bölümü, tüm Windows Communication Foundation (WCF) ServiceModel yapılandırma öğelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a8d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a8d6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a8d6-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a8d6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3a8d6-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a8d6-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3a8d6-107">Attributes</span></span>  
 <span data-ttu-id="3a8d6-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a8d6-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a8d6-109">Child Elements</span></span>  
  
|<span data-ttu-id="3a8d6-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a8d6-110">Element</span></span>|<span data-ttu-id="3a8d6-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a8d6-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a8d6-112">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="3a8d6-113">Bu bölümde adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3a8d6-114">Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3a8d6-115">Her davranışı öğesi kendi benzersiz tarafından tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="3a8d6-116">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="3a8d6-117">Bu bölümde, standart ve özel bağlamalar koleksiyonunu tutar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="3a8d6-118">Her giriş kendi benzersiz tarafından tanımlanır `name`.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="3a8d6-119">Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="3a8d6-120">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="3a8d6-121">Bu bölüm, bir istemcinin bir hizmete bağlanmak için kullandığı uç noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="3a8d6-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3a8d6-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="3a8d6-123">Bu bölümde, WCF ve COM birlikte çalışması için etkin COM sözleşmeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="3a8d6-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="3a8d6-125">Bu bölümü sadece machine.config dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="3a8d6-126">Adlı iki alt öğe koleksiyonlarını tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3a8d6-127">Her koleksiyon, sırasıyla tüm WCF uç noktaları ve makinede hizmetler tarafından kullanılan davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="3a8d6-128">Hem de bir davranış tanımlanmışsa `<commonBehaviors>` ve `<behaviors>` bölümler, davranış \<davranışları > bölüm tercih verilir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="3a8d6-129">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-129">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="3a8d6-130">Bu bölümde, WCF tanılama özelliklerini ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="3a8d6-131">Kullanıcı etkinleştirebilir/izleme, performans sayaçları ve WMI sağlayıcısı devre dışı bırakabilir ve özel ileti filtreleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="3a8d6-132">\<Uzantıları ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-132">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="3a8d6-133">Bu bölüm, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönleri uzantıları oluşturmak kullanıcı olanak tanıyan uzantılar koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="3a8d6-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="3a8d6-135">Bu bölümde, taşıma protokol şemaları (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokol eşleşmelerinin bir kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="3a8d6-136">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="3a8d6-137">Bu bölümde, Windows Communication Foundation (WCF) türünü belirleyen ve yönlendirme süzgeçleri kümesini tanımlayan<xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek ne zaman ileti göndermek için hedef bitiş noktalarını tanımlayan tabloları yapılırken kullanılacak bir Filtre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="3a8d6-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="3a8d6-139">Bu bölümde, hizmet barındırma ortamı için belirli bir örneğini oluşturur. ne tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="3a8d6-140">Bu bölümde boşsa, varsayılan türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="3a8d6-141">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="3a8d6-142">Bölüm Hizmetleri koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-142">The section contains a collection of services.</span></span> <span data-ttu-id="3a8d6-143">Derlemede tanımlanan her hizmet için bu öğeyi içeren bir `service` hizmeti ayarlarını belirten öğe.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="3a8d6-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="3a8d6-145">Bu bölümde, yeniden kullanılabilen önceden yapılandırılmış uç noktalar olan standart uç noktaları koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="3a8d6-146">Bir standart uç nokta gerekir veya daha fazla adresi, bağlama ve sözleşme öznitelikleri için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="3a8d6-147">Örneğin, bulma uç noktası sözleşme sabittir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="3a8d6-148">Standart uç noktaları, yeni özellikleri benzer özel bağlamaları tanımlamak için olan hizmet uç noktası genişletmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="3a8d6-149">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-149">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|<span data-ttu-id="3a8d6-150">Bu bölümde, bir iş akışı hizmeti için izleme ayarlarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3a8d6-151">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3a8d6-151">Parent Elements</span></span>  
  
|<span data-ttu-id="3a8d6-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="3a8d6-152">Element</span></span>|<span data-ttu-id="3a8d6-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a8d6-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a8d6-154">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3a8d6-154">\<configuration></span></span>|<span data-ttu-id="3a8d6-155">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a8d6-156">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a8d6-156">Remarks</span></span>  
 <span data-ttu-id="3a8d6-157">WCF öğeleri diğer ürünleri yapılandırma bölümlerini eklemez.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="3a8d6-158">WCF hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3a8d6-159">Derleme Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="3a8d6-160">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3a8d6-161">Bölümü ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3a8d6-162">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="3a8d6-163">Varsayılan olarak, bir hizmetin adı bir hizmeti uygulamak için kullanılan temel alınan CLR türü açıklar; Ancak, üzerinde ConfigurationName özelliği değişebilir bir <xref:System.ServiceModel.ServiceContractAttribute> CLR türü gereksinimi geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="3a8d6-164">`behaviorConfiguration` İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="3a8d6-165">Bu, bir hizmet tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="3a8d6-166">Bu özniteliği tarafından belirtilen davranışı aynı yapılandırma dosyasının (yani, aynı dosya veya üst dosyası) kapsamında tanımlanan bir hizmet davranışını bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="3a8d6-167">Hizmet her bir sunar veya daha fazla uç noktaları tanımlanan bir `endpoint` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="3a8d6-168">Her uç nokta, kendi adres ve bağlama vardır.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="3a8d6-169">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="3a8d6-170">Bağlamaları özniteliklerinin birleşimiyle uç noktalarına bağlı olan `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3a8d6-171">`binding` Öznitelik tanımlar bağlama hangi bölümde tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="3a8d6-172">`bindingConfiguration` Özniteliği, hangi yapılandırılmış bağlama bağlama bölümü içinde kullanılan tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="3a8d6-173">Bir bağlama bölümü birkaç yapılandırılmış bağlama tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a8d6-174">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a8d6-174">Example</span></span>  
 <span data-ttu-id="3a8d6-175">Bu, WCF yapılandırma dosyasına örneğidir.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-175">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a8d6-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a8d6-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
