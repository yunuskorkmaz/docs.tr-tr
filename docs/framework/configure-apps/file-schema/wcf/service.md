---
description: 'Hakkında daha fazla bilgi edinin: <service>'
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c3870a170847d773996625235c75591ced75e315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786791"
---
# \<service>

<span data-ttu-id="a744c-102">`service`Öğesi bir Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a744c-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a744c-103">Ayrıca hizmeti kullanıma sunan uç noktaları da içerir.</span><span class="sxs-lookup"><span data-stu-id="a744c-103">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="a744c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a744c-104">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a744c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a744c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a744c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a744c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a744c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a744c-107">Attributes</span></span>  
  
|<span data-ttu-id="a744c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a744c-108">Attribute</span></span>|<span data-ttu-id="a744c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a744c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a744c-110">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a744c-110">behaviorConfiguration</span></span>|<span data-ttu-id="a744c-111">Hizmeti başlatmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="a744c-111">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="a744c-112">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a744c-112">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="a744c-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="a744c-113">The default value is an empty string.</span></span>|  
|<span data-ttu-id="a744c-114">name</span><span class="sxs-lookup"><span data-stu-id="a744c-114">name</span></span>|<span data-ttu-id="a744c-115">Oluşturulacak hizmetin türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a744c-115">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="a744c-116">Bu ayar geçerli bir türe eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a744c-116">This setting must equate to a valid type.</span></span> <span data-ttu-id="a744c-117">Biçim şu şekilde olmalıdır `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="a744c-117">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a744c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a744c-118">Child Elements</span></span>  
  
|<span data-ttu-id="a744c-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="a744c-119">Element</span></span>|<span data-ttu-id="a744c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a744c-120">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="a744c-121">`endpoint`Bu hizmeti kullanıma sunan öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a744c-121">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="a744c-122">Bu hizmet örneğinin konağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a744c-122">Specifies the host of this service instance.</span></span> <span data-ttu-id="a744c-123">Bu öğe türündedir <xref:System.ServiceModel.Configuration.HostElement> .</span><span class="sxs-lookup"><span data-stu-id="a744c-123">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a744c-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a744c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a744c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a744c-125">Element</span></span>|<span data-ttu-id="a744c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a744c-126">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="a744c-127">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="a744c-127">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a744c-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a744c-128">Remarks</span></span>  

 <span data-ttu-id="a744c-129">Hizmetler, `services` yapılandırma dosyasının bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a744c-129">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a744c-130">Bir derleme, herhangi bir sayıda hizmeti içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a744c-130">An assembly can contain any number of services.</span></span> <span data-ttu-id="a744c-131">Her hizmetin kendi `service` yapılandırma bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="a744c-131">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="a744c-132">Bu bölüm ve içeriği, belirli bir hizmetin hizmet sözleşmesini, davranışını ve uç noktalarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a744c-132">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="a744c-133">`behaviorConfiguration`Öğesi de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a744c-133">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="a744c-134">Hizmetin kullandığı davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a744c-134">It identifies the behavior the service uses.</span></span> <span data-ttu-id="a744c-135">Bu öznitelikte belirtilen davranışın, aynı yapılandırma dosyasındaki kapsamdaki bir davranışa bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a744c-135">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="a744c-136">Her hizmet kendi adresine ve bağlamaya sahip bir veya daha fazla bitiş noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="a744c-136">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="a744c-137">Yapılandırma dosyası içinde kullanılan tüm bağlamalar, dosyanın kapsamında tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a744c-137">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="a744c-138">Bağlama, özniteliklerin ve öğelerinin birleşimi aracılığıyla uç noktalara bağlanır `name` `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="a744c-138">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="a744c-139">`name`Özniteliği, bağlamanın tanımlandığı bölümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a744c-139">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="a744c-140">`bindingConfiguration`Özniteliği, bağlama bölümünde hangi yapılandırmanın kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a744c-140">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="a744c-141">Bağlama bölümü, birkaç yapılandırma tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a744c-141">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a744c-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="a744c-142">Example</span></span>  

 <span data-ttu-id="a744c-143">Bu, hizmet yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="a744c-143">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a744c-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a744c-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="a744c-145">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a744c-145">Configuring Services</span></span>](../../../wcf/configuring-services.md)
