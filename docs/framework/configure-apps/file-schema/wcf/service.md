---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: dcc32f5aa055942408a3f01d37b5aa27ac0f51ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173776"
---
# \<service>

<span data-ttu-id="89f2b-101">`service`Öğesi bir Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="89f2b-102">Ayrıca hizmeti kullanıma sunan uç noktaları da içerir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="89f2b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="89f2b-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89f2b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f2b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="89f2b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89f2b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89f2b-106">Attributes</span></span>  
  
|<span data-ttu-id="89f2b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89f2b-107">Attribute</span></span>|<span data-ttu-id="89f2b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f2b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89f2b-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="89f2b-109">behaviorConfiguration</span></span>|<span data-ttu-id="89f2b-110">Hizmeti başlatmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="89f2b-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="89f2b-111">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="89f2b-112">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="89f2b-113">name</span><span class="sxs-lookup"><span data-stu-id="89f2b-113">name</span></span>|<span data-ttu-id="89f2b-114">Oluşturulacak hizmetin türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="89f2b-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="89f2b-115">Bu ayar geçerli bir türe eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="89f2b-116">Biçim şu şekilde olmalıdır `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="89f2b-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89f2b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f2b-117">Child Elements</span></span>  
  
|<span data-ttu-id="89f2b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="89f2b-118">Element</span></span>|<span data-ttu-id="89f2b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f2b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="89f2b-120">`endpoint`Bu hizmeti kullanıma sunan öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="89f2b-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="89f2b-121">Bu hizmet örneğinin konağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="89f2b-122">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HostElement> .</span><span class="sxs-lookup"><span data-stu-id="89f2b-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89f2b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f2b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="89f2b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="89f2b-124">Element</span></span>|<span data-ttu-id="89f2b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f2b-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="89f2b-126">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="89f2b-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89f2b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89f2b-127">Remarks</span></span>  

 <span data-ttu-id="89f2b-128">Hizmetler, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="89f2b-129">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="89f2b-130">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="89f2b-131">Bu bölüm ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="89f2b-132">`behaviorConfiguration`Öğesi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="89f2b-133">Hizmetin kullandığı davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="89f2b-134">Bu öznitelikte belirtilen davranışın, aynı yapılandırma dosyasındaki kapsamdaki bir davranışa bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="89f2b-135">Her hizmet kendi adresine ve bağlamaya sahip bir veya daha fazla bitiş noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="89f2b-136">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89f2b-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="89f2b-137">Bağlama, özniteliklerin ve öğelerinin birleşimi aracılığıyla uç noktalara bağlanır `name` `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="89f2b-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="89f2b-138">`name`Özniteliği, bağlamanın tanımlandığı bölümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="89f2b-139">`bindingConfiguration`Özniteliği, bağlama bölümünde hangi yapılandırmanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89f2b-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="89f2b-140">Bağlama bölümü, birkaç yapılandırma tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89f2b-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="89f2b-141">Example</span></span>  

 <span data-ttu-id="89f2b-142">Bu, hizmet yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="89f2b-142">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89f2b-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89f2b-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="89f2b-144">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89f2b-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
