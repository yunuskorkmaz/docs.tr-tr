---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 68bddc01b02d9885b3f0fc4c2cbc5c3249de03f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197964"
---
# <a name="service"></a><span data-ttu-id="67837-101">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="67837-101">\<service></span></span>
<span data-ttu-id="67837-102">`service` Öğesi Windows Communication Foundation (WCF) hizmetinin ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="67837-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="67837-103">Ayrıca, açığa çıkaran hizmet uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="67837-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="67837-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67837-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="67837-105">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="67837-105">\<services></span></span>  
<span data-ttu-id="67837-106">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="67837-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67837-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67837-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67837-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="67837-108">Attributes and Elements</span></span>  
 <span data-ttu-id="67837-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67837-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67837-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="67837-110">Attributes</span></span>  
  
|<span data-ttu-id="67837-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="67837-111">Attribute</span></span>|<span data-ttu-id="67837-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67837-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67837-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="67837-113">behaviorConfiguration</span></span>|<span data-ttu-id="67837-114">Hizmeti örneklemek için kullanılacak davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="67837-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="67837-115">Davranış adı, hizmet tanımlı bir noktada kapsam içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67837-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="67837-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="67837-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="67837-117">name</span><span class="sxs-lookup"><span data-stu-id="67837-117">name</span></span>|<span data-ttu-id="67837-118">Oluşturulacak hizmet türünü belirten bir dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="67837-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="67837-119">Bu ayar, geçerli bir tür için değer gerekir.</span><span class="sxs-lookup"><span data-stu-id="67837-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="67837-120">Biçiminde olmalıdır `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="67837-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67837-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="67837-121">Child Elements</span></span>  
  
|<span data-ttu-id="67837-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="67837-122">Element</span></span>|<span data-ttu-id="67837-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67837-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67837-124">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="67837-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="67837-125">Bir koleksiyonu `endpoint` kullanıma sunan bu hizmet öğeleri.</span><span class="sxs-lookup"><span data-stu-id="67837-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="67837-126">\<konak ></span><span class="sxs-lookup"><span data-stu-id="67837-126">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="67837-127">Bu hizmet örneğinin konak belirtir.</span><span class="sxs-lookup"><span data-stu-id="67837-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="67837-128">Bu öğe türünde <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="67837-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67837-129">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="67837-129">Parent Elements</span></span>  
  
|<span data-ttu-id="67837-130">Öğe</span><span class="sxs-lookup"><span data-stu-id="67837-130">Element</span></span>|<span data-ttu-id="67837-131">Açıklama</span><span class="sxs-lookup"><span data-stu-id="67837-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67837-132">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="67837-132">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="67837-133">Tüm WCF yapılandırma öğelerinin kök öğe.</span><span class="sxs-lookup"><span data-stu-id="67837-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67837-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67837-134">Remarks</span></span>  
 <span data-ttu-id="67837-135">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="67837-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="67837-136">Derleme Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="67837-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="67837-137">Her hizmet kendi sahip `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="67837-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="67837-138">Bu bölümde ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktaları tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="67837-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="67837-139">`behaviorConfiguration` Öğesi, aynı zamanda isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="67837-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="67837-140">Bu hizmetin davranışı tanımlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="67837-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="67837-141">Bu öznitelikte belirtilen davranışı kapsamında aynı yapılandırma dosyasında bir davranış bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="67837-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="67837-142">Her hizmet kendi adres ve bağlama sahip olduğu bir veya daha fazla uç nokta kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="67837-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="67837-143">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67837-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="67837-144">Bağlama özniteliklerinin birleşimiyle uç noktalarına bağlı olan `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="67837-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="67837-145">`name` Özniteliği bağlama tanımlanmış bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="67837-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="67837-146">`bindingConfiguration` Özniteliği, bağlama bölüm içindeki hangi yapılandırma kullanıldığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="67837-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="67837-147">Bir bağlama bölümü birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67837-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67837-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="67837-148">Example</span></span>  
 <span data-ttu-id="67837-149">Bu, bir hizmet yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="67837-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67837-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67837-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="67837-151">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67837-151">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
