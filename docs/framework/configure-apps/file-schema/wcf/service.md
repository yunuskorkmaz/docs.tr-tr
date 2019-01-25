---
title: '&lt;Hizmet&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: e91e04c602fd867e329477015fc0a8354ae26a05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535014"
---
# <a name="ltservicegt"></a><span data-ttu-id="a459c-102">&lt;Hizmet&gt;</span><span class="sxs-lookup"><span data-stu-id="a459c-102">&lt;service&gt;</span></span>
<span data-ttu-id="a459c-103">`service` Öğesi Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a459c-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a459c-104">Ayrıca, açığa çıkaran hizmet uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="a459c-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="a459c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a459c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a459c-106">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="a459c-106">\<services></span></span>  
<span data-ttu-id="a459c-107">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="a459c-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a459c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a459c-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a459c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a459c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a459c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a459c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a459c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a459c-111">Attributes</span></span>  
  
|<span data-ttu-id="a459c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a459c-112">Attribute</span></span>|<span data-ttu-id="a459c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a459c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a459c-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a459c-114">behaviorConfiguration</span></span>|<span data-ttu-id="a459c-115">Hizmeti örneklemek için kullanılacak davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="a459c-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="a459c-116">Davranış adı, hizmet tanımlı bir noktada kapsam içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a459c-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="a459c-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a459c-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="a459c-118">name</span><span class="sxs-lookup"><span data-stu-id="a459c-118">name</span></span>|<span data-ttu-id="a459c-119">Oluşturulacak hizmet türünü belirten bir dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="a459c-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="a459c-120">Bu ayar, geçerli bir tür için değer gerekir.</span><span class="sxs-lookup"><span data-stu-id="a459c-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="a459c-121">Biçiminde olmalıdır `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="a459c-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a459c-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a459c-122">Child Elements</span></span>  
  
|<span data-ttu-id="a459c-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a459c-123">Element</span></span>|<span data-ttu-id="a459c-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a459c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a459c-125">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="a459c-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="a459c-126">Bir koleksiyonu `endpoint` kullanıma sunan bu hizmet öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a459c-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="a459c-127">\<konak ></span><span class="sxs-lookup"><span data-stu-id="a459c-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="a459c-128">Bu hizmet örneğinin konak belirtir.</span><span class="sxs-lookup"><span data-stu-id="a459c-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="a459c-129">Bu öğe türünde <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="a459c-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a459c-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a459c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="a459c-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="a459c-131">Element</span></span>|<span data-ttu-id="a459c-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a459c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a459c-133">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="a459c-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="a459c-134">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a459c-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a459c-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a459c-135">Remarks</span></span>  
 <span data-ttu-id="a459c-136">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="a459c-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a459c-137">Derleme Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a459c-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="a459c-138">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="a459c-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="a459c-139">Bu bölümde ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a459c-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="a459c-140">`behaviorConfiguration` Öğesi, aynı zamanda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a459c-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="a459c-141">Bu hizmetin davranışı tanımlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="a459c-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="a459c-142">Bu öznitelikte belirtilen davranışı kapsamında aynı yapılandırma dosyasında bir davranış bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a459c-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="a459c-143">Her hizmet kendi adres ve bağlama sahip olduğu bir veya daha fazla uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a459c-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="a459c-144">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a459c-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="a459c-145">Bağlama özniteliklerinin birleşimiyle uç noktalarına bağlı olan `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a459c-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="a459c-146">`name` Özniteliği bağlama tanımlanmış bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a459c-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="a459c-147">`bindingConfiguration` Özniteliği, bağlama bölüm içindeki hangi yapılandırma kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a459c-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="a459c-148">Bir bağlama bölümü birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a459c-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a459c-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="a459c-149">Example</span></span>  
 <span data-ttu-id="a459c-150">Bu, bir hizmet yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="a459c-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="a459c-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a459c-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="a459c-152">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a459c-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
