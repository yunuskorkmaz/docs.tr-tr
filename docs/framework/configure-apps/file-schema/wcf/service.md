---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855025"
---
# <a name="service"></a><span data-ttu-id="43081-101">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="43081-101">\<service></span></span>
<span data-ttu-id="43081-102">`service` Öğesi bir Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="43081-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="43081-103">Ayrıca hizmeti kullanıma sunan uç noktaları da içerir.</span><span class="sxs-lookup"><span data-stu-id="43081-103">It also contains endpoints that expose the service.</span></span>  
  
<span data-ttu-id="43081-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43081-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43081-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="43081-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="43081-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="43081-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="43081-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<hizmet >**</span><span class="sxs-lookup"><span data-stu-id="43081-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43081-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43081-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43081-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43081-109">Attributes and Elements</span></span>  
 <span data-ttu-id="43081-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43081-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43081-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43081-111">Attributes</span></span>  
  
|<span data-ttu-id="43081-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43081-112">Attribute</span></span>|<span data-ttu-id="43081-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43081-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43081-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="43081-114">behaviorConfiguration</span></span>|<span data-ttu-id="43081-115">Hizmeti başlatmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="43081-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="43081-116">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43081-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="43081-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43081-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="43081-118">name</span><span class="sxs-lookup"><span data-stu-id="43081-118">name</span></span>|<span data-ttu-id="43081-119">Oluşturulacak hizmetin türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="43081-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="43081-120">Bu ayar geçerli bir türe eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43081-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="43081-121">Biçim şu şekilde olmalıdır`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="43081-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43081-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43081-122">Child Elements</span></span>  
  
|<span data-ttu-id="43081-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="43081-123">Element</span></span>|<span data-ttu-id="43081-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43081-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43081-125">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="43081-125">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="43081-126">Bu hizmeti kullanıma `endpoint` sunan öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="43081-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="43081-127">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="43081-127">\<host></span></span>](host.md)|<span data-ttu-id="43081-128">Bu hizmet örneğinin konağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="43081-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="43081-129">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="43081-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43081-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43081-130">Parent Elements</span></span>  
  
|<span data-ttu-id="43081-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="43081-131">Element</span></span>|<span data-ttu-id="43081-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43081-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43081-133">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="43081-133">\<services></span></span>](services.md)|<span data-ttu-id="43081-134">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="43081-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43081-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43081-135">Remarks</span></span>  
 <span data-ttu-id="43081-136">Hizmetler, yapılandırma dosyasının `services` bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="43081-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="43081-137">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="43081-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="43081-138">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="43081-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="43081-139">Bu bölüm ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43081-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="43081-140">`behaviorConfiguration` Öğesi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="43081-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="43081-141">Hizmetin kullandığı davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43081-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="43081-142">Bu öznitelikte belirtilen davranışın, aynı yapılandırma dosyasındaki kapsamdaki bir davranışa bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="43081-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="43081-143">Her hizmet kendi adresine ve bağlamaya sahip bir veya daha fazla bitiş noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="43081-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="43081-144">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43081-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="43081-145">Bağlama, özniteliklerin `name` ve `bindingConfiguration`öğelerinin birleşimi aracılığıyla uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="43081-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="43081-146">`name` Özniteliği, bağlamanın tanımlandığı bölümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43081-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="43081-147">`bindingConfiguration` Özniteliği, bağlama bölümünde hangi yapılandırmanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="43081-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="43081-148">Bağlama bölümü, birkaç yapılandırma tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="43081-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43081-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="43081-149">Example</span></span>  
 <span data-ttu-id="43081-150">Bu, hizmet yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="43081-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43081-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43081-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="43081-152">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="43081-152">Configuring Services</span></span>](../../../wcf/configuring-services.md)
