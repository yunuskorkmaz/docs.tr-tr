---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936518"
---
# <a name="service"></a><span data-ttu-id="dfc75-101">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="dfc75-101">\<service></span></span>
<span data-ttu-id="dfc75-102">`service` Öğesi bir Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="dfc75-103">Ayrıca hizmeti kullanıma sunan uç noktaları da içerir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="dfc75-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dfc75-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dfc75-105">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="dfc75-105">\<services></span></span>  
<span data-ttu-id="dfc75-106">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="dfc75-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc75-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfc75-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfc75-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc75-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dfc75-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfc75-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dfc75-110">Attributes</span></span>  
  
|<span data-ttu-id="dfc75-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dfc75-111">Attribute</span></span>|<span data-ttu-id="dfc75-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfc75-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfc75-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="dfc75-113">behaviorConfiguration</span></span>|<span data-ttu-id="dfc75-114">Hizmeti başlatmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="dfc75-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="dfc75-115">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="dfc75-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="dfc75-117">name</span><span class="sxs-lookup"><span data-stu-id="dfc75-117">name</span></span>|<span data-ttu-id="dfc75-118">Oluşturulacak hizmetin türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dfc75-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="dfc75-119">Bu ayar geçerli bir türe eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="dfc75-120">Biçim şu şekilde olmalıdır`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="dfc75-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfc75-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc75-121">Child Elements</span></span>  
  
|<span data-ttu-id="dfc75-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfc75-122">Element</span></span>|<span data-ttu-id="dfc75-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfc75-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc75-124">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="dfc75-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="dfc75-125">Bu hizmeti kullanıma `endpoint` sunan öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="dfc75-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="dfc75-126">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="dfc75-126">\<host></span></span>](host.md)|<span data-ttu-id="dfc75-127">Bu hizmet örneğinin konağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="dfc75-128">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="dfc75-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dfc75-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dfc75-129">Parent Elements</span></span>  
  
|<span data-ttu-id="dfc75-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="dfc75-130">Element</span></span>|<span data-ttu-id="dfc75-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfc75-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfc75-132">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="dfc75-132">\<services></span></span>](services.md)|<span data-ttu-id="dfc75-133">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="dfc75-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc75-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfc75-134">Remarks</span></span>  
 <span data-ttu-id="dfc75-135">Hizmetler, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="dfc75-136">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="dfc75-137">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="dfc75-138">Bu bölüm ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfc75-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="dfc75-139">`behaviorConfiguration` Öğesi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="dfc75-140">Hizmetin kullandığı davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfc75-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="dfc75-141">Bu öznitelikte belirtilen davranışın, aynı yapılandırma dosyasındaki kapsamdaki bir davranışa bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="dfc75-142">Her hizmet kendi adresine ve bağlamaya sahip bir veya daha fazla bitiş noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="dfc75-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="dfc75-143">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="dfc75-144">Bağlama, özniteliklerin `name` ve `bindingConfiguration`öğelerinin birleşimi aracılığıyla uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="dfc75-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="dfc75-145">`name` Özniteliği, bağlamanın tanımlandığı bölümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfc75-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="dfc75-146">`bindingConfiguration` Özniteliği, bağlama bölümünde hangi yapılandırmanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dfc75-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="dfc75-147">Bağlama bölümü, birkaç yapılandırma tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfc75-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="dfc75-148">Example</span></span>  
 <span data-ttu-id="dfc75-149">Bu, hizmet yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="dfc75-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dfc75-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc75-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="dfc75-151">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dfc75-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
