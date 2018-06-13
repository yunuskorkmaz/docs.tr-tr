---
title: '&lt;Hizmeti&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 6e83e988920d24c6fe7615e40334919caf21652e
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2018
ms.locfileid: "34059036"
---
# <a name="ltservicegt"></a><span data-ttu-id="b8e6d-102">&lt;Hizmeti&gt;</span><span class="sxs-lookup"><span data-stu-id="b8e6d-102">&lt;service&gt;</span></span>
<span data-ttu-id="b8e6d-103">`service` Öğesi bir Windows Communication Foundation (WCF) hizmet ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="b8e6d-104">Ayrıca, hizmeti kullanıma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="b8e6d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8e6d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8e6d-106">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="b8e6d-106">\<services></span></span>  
<span data-ttu-id="b8e6d-107">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="b8e6d-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8e6d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8e6d-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String">  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8e6d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8e6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8e6d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8e6d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8e6d-111">Attributes</span></span>  
  
|<span data-ttu-id="b8e6d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8e6d-112">Attribute</span></span>|<span data-ttu-id="b8e6d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8e6d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8e6d-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="b8e6d-114">behaviorConfiguration</span></span>|<span data-ttu-id="b8e6d-115">Hizmet örneği oluşturmak için kullanılacak davranış davranışı adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="b8e6d-116">Davranış adı Hizmet tanımlı bir noktada kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="b8e6d-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="b8e6d-118">name</span><span class="sxs-lookup"><span data-stu-id="b8e6d-118">name</span></span>|<span data-ttu-id="b8e6d-119">Örneğinin oluşturulması için hizmet türünü belirten dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="b8e6d-120">Bu ayar için geçerli bir tür eşitlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="b8e6d-121">Biçiminde olmalıdır `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="b8e6d-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8e6d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8e6d-122">Child Elements</span></span>  
  
|<span data-ttu-id="b8e6d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8e6d-123">Element</span></span>|<span data-ttu-id="b8e6d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8e6d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e6d-125">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="b8e6d-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="b8e6d-126">Bir koleksiyonu `endpoint` bu hizmeti kullanıma öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="b8e6d-127">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="b8e6d-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="b8e6d-128">Bu hizmet örneği ana belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="b8e6d-129">Bu öğe türünde <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8e6d-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8e6d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="b8e6d-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8e6d-131">Element</span></span>|<span data-ttu-id="b8e6d-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8e6d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8e6d-133">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="b8e6d-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="b8e6d-134">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8e6d-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8e6d-135">Remarks</span></span>  
 <span data-ttu-id="b8e6d-136">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="b8e6d-137">Bir derlemeyi Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="b8e6d-138">Her hizmetin kendi vardır `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="b8e6d-139">Bu bölümde ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktalarına tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="b8e6d-140">`behaviorConfiguration` Öğesidir Ayrıca isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="b8e6d-141">Hizmet davranışını tanımlayan kullanır.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="b8e6d-142">Bu öznitelikte belirtilen davranışı aynı yapılandırma dosyası kapsamındaki bir davranış bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="b8e6d-143">Her hizmet bir veya daha fazla uç noktalar, kendi adres ve bağlama olan kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="b8e6d-144">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="b8e6d-145">Bağlama uç noktaları özniteliklerini birleşimi yoluyla bağlı `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="b8e6d-146">`name` Özniteliğini bağlama tanımlanmış bölüm açıklar.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="b8e6d-147">`bindingConfiguration` Öznitelik tanımlar bağlama bölüm içindeki hangi yapılandırma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="b8e6d-148">Bir bağlama bölümü birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e6d-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8e6d-149">Example</span></span>  
 <span data-ttu-id="b8e6d-150">Bu, bir hizmet yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8e6d-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e6d-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="b8e6d-152">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b8e6d-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
