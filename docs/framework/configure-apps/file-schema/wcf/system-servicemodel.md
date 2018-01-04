---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02bf740794b1551d3b130922939dbb27e572578e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="24143-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="24143-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="24143-103">Bu yapılandırma bölümü tüm içeren [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel yapılandırma öğeleri.</span><span class="sxs-lookup"><span data-stu-id="24143-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24143-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24143-104">Syntax</span></span>  
  
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
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24143-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="24143-105">Attributes and Elements</span></span>  
 <span data-ttu-id="24143-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="24143-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24143-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="24143-107">Attributes</span></span>  
 <span data-ttu-id="24143-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="24143-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="24143-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="24143-109">Child Elements</span></span>  
  
|<span data-ttu-id="24143-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="24143-110">Element</span></span>|<span data-ttu-id="24143-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24143-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24143-112">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="24143-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="24143-113">Bu bölümde adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="24143-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="24143-114">Her koleksiyon sırasıyla uç noktaları ve hizmetler tarafından tüketilen davranışı öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="24143-115">Her davranış öğesi kendi benzersiz tanımlanır `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="24143-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="24143-116">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="24143-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="24143-117">Bu bölümde, standart ve özel bağlamaları koleksiyonu tutar.</span><span class="sxs-lookup"><span data-stu-id="24143-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="24143-118">Her giriş kendi benzersiz tarafından tanımlanan `name`.</span><span class="sxs-lookup"><span data-stu-id="24143-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="24143-119">Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.</span><span class="sxs-lookup"><span data-stu-id="24143-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="24143-120">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="24143-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="24143-121">Bu bölüm, bir istemcinin bir hizmete bağlanmak için kullandığı bitiş noktaları listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="24143-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="24143-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="24143-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="24143-123">Bu bölümde, WCF ve COM birlikte çalışma için etkin COM sözleşmeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="24143-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="24143-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="24143-125">Bu bölümü yalnızca machine.config dosyasındaki tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="24143-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="24143-126">Adlı iki alt koleksiyonlar tanımlar `endpointBehaviors` ve `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="24143-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="24143-127">Her bir koleksiyon tarafından tüketilen davranışı öğeleri tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uç noktaları ve hizmetler makinedeki sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="24143-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="24143-128">Bir davranış ikisi de tanımlanmışsa `<commonBehaviors>` ve `<behaviors>` bölümlerinde, davranış \<davranışları > bölümü tercih verilen.</span><span class="sxs-lookup"><span data-stu-id="24143-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="24143-129">\<Uzantıları ></span><span class="sxs-lookup"><span data-stu-id="24143-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="24143-130">Bu bölüm, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="24143-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="24143-131">\<Tanılama ></span><span class="sxs-lookup"><span data-stu-id="24143-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="24143-132">Bu bölümde WCF'nin tanılama özelliklerine yönelik ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="24143-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="24143-133">Kullanıcı etkinleştirebilir/izleme, performans sayaçları ve WMI sağlayıcısı devre dışı bırakabilir ve özel ileti filtreleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24143-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="24143-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="24143-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="24143-135">Bu bölümde Aktarım Protokolü düzenleri (örn., http, net.tcp, net.pipe, vb.) ve WCF bağlamaları arasında varsayılan protokolü eşleme kümesini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="24143-136">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="24143-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="24143-137">Bu bölümde türünü belirleme yönlendirme bir filtre kümesi tanımlar [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> yönlendirme yanı sıra gelen iletileri değerlendirmek için ne zaman bir filtre ile eşleşen iletileri göndermek için hedef uç nokta tanımlayan tabloları yapılırken kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="24143-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="24143-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="24143-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="24143-139">Bu bölümde, ne tür bir barındırma ortamı için özel bir taşıma başlatır hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="24143-140">Bu bölümde boşsa, varsayılan türü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24143-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="24143-141">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="24143-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="24143-142">Bölüm hizmetler koleksiyonu içerir.</span><span class="sxs-lookup"><span data-stu-id="24143-142">The section contains a collection of services.</span></span> <span data-ttu-id="24143-143">Derlemede tanımlanan her hizmet için bu öğeyi içeren bir `service` öğesi hizmeti ayarlarını belirtme.</span><span class="sxs-lookup"><span data-stu-id="24143-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="24143-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="24143-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="24143-145">Bu bölümde, yeniden kullanılabilir önceden yapılandırılmış uç nokta standart uç noktaları koleksiyonu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="24143-146">Standart bir uç noktası bir erişebilir veya adresi, bağlama ve sözleşme öznitelikleri daha fazla sabit bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="24143-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="24143-147">Örneğin, bulma uç sözleşme sabittir.</span><span class="sxs-lookup"><span data-stu-id="24143-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="24143-148">Standart uç noktaları, özel bağlamaları tanımlamak için benzer yeni özelliklerle Hizmeti uç noktası genişletmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24143-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="24143-149">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="24143-149">Parent Elements</span></span>  
  
|<span data-ttu-id="24143-150">Öğe</span><span class="sxs-lookup"><span data-stu-id="24143-150">Element</span></span>|<span data-ttu-id="24143-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24143-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24143-152">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="24143-152">\<configuration></span></span>|<span data-ttu-id="24143-153">Bir .NET yapılandırma dosyasındaki tüm yapılandırma öğeleri için kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="24143-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24143-154">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24143-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="24143-155">öğeleri diğer ürünleri yapılandırma bölümlerini eklemez.</span><span class="sxs-lookup"><span data-stu-id="24143-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="24143-156">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="24143-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="24143-157">Bir derlemeyi Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="24143-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="24143-158">Her hizmetin kendi vardır `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="24143-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="24143-159">Bölüm ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktalarına tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="24143-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="24143-160">Yalnızca bir hizmetin `name` özniteliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="24143-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="24143-161">Varsayılan olarak, bir hizmetin adı bir hizmet uygulamak için kullanılan temel CLR türü açıklanır; Ancak, üzerinde ConfigurationName özelliği değişebilir bir <xref:System.ServiceModel.ServiceContractAttribute> CLR türü gereksinimini geçersiz kılmak için.</span><span class="sxs-lookup"><span data-stu-id="24143-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="24143-162">`behaviorConfiguration` Özniteliği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="24143-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="24143-163">Bir hizmeti tarafından kullanılan hizmet davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="24143-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="24143-164">Bu özniteliği tarafından belirtilen davranışı aynı yapılandırma dosyasının (yani aynı dosya veya bir üst dosyası) kapsamda tanımlı bir hizmet davranışı bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24143-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="24143-165">Her hizmet bir gösterir ya da daha fazla uç noktaları tanımlanan bir `endpoint` öğesi.</span><span class="sxs-lookup"><span data-stu-id="24143-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="24143-166">Her uç nokta kendi adres ve bağlama vardır.</span><span class="sxs-lookup"><span data-stu-id="24143-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="24143-167">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24143-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="24143-168">Bağlamaları uç noktaları özniteliklerini birleşimi yoluyla bağlı `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="24143-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="24143-169">`binding` Öznitelik tanımlar bağlama hangi bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="24143-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="24143-170">`bindingConfiguration` Öznitelik tanımlar bağlama bölüm içinde yapılandırılmış hangi bağlama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24143-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="24143-171">Bir bağlama bölümü birkaç yapılandırılmış bağlamaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24143-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24143-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="24143-172">Example</span></span>  
 <span data-ttu-id="24143-173">Bu, WCF yapılandırma dosyasına örneğidir.</span><span class="sxs-lookup"><span data-stu-id="24143-173">This is an example of a WCF configuration file.</span></span>  
  
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
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
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
  
## <a name="see-also"></a><span data-ttu-id="24143-174">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24143-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
