---
title: '&lt;hizmeti&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61c8d8451e271e756fce6f83a4f8b8fd4c8b9f77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicegt"></a><span data-ttu-id="9f584-102">&lt;hizmeti&gt;</span><span class="sxs-lookup"><span data-stu-id="9f584-102">&lt;service&gt;</span></span>
<span data-ttu-id="9f584-103">`service` Öğesi bir Windows Communication Foundation (WCF) hizmet ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f584-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9f584-104">Ayrıca, hizmeti kullanıma uç noktaları içerir.</span><span class="sxs-lookup"><span data-stu-id="9f584-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="9f584-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9f584-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f584-106">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="9f584-106">\<services></span></span>  
<span data-ttu-id="9f584-107">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="9f584-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f584-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f584-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f584-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f584-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9f584-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f584-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f584-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f584-111">Attributes</span></span>  
  
|<span data-ttu-id="9f584-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f584-112">Attribute</span></span>|<span data-ttu-id="9f584-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f584-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f584-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="9f584-114">behaviorConfiguration</span></span>|<span data-ttu-id="9f584-115">Hizmet örneği oluşturmak için kullanılacak davranış davranışı adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="9f584-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="9f584-116">Davranış adı Hizmet tanımlı bir noktada kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f584-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="9f584-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="9f584-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="9f584-118">name</span><span class="sxs-lookup"><span data-stu-id="9f584-118">name</span></span>|<span data-ttu-id="9f584-119">Örneğinin oluşturulması için hizmet türünü belirten dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="9f584-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="9f584-120">Bu ayar için geçerli bir tür eşitlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f584-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="9f584-121">Biçiminde olmalıdır`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="9f584-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f584-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f584-122">Child Elements</span></span>  
  
|<span data-ttu-id="9f584-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f584-123">Element</span></span>|<span data-ttu-id="9f584-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f584-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f584-125">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="9f584-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="9f584-126">Bir koleksiyonu `endpoint` bu hizmeti kullanıma öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9f584-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="9f584-127">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="9f584-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="9f584-128">Bu hizmet örneği ana belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f584-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="9f584-129">Bu öğe türünde <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="9f584-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9f584-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f584-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9f584-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f584-131">Element</span></span>|<span data-ttu-id="9f584-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f584-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f584-133">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="9f584-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="9f584-134">Tüm WCF yapılandırma öğelerinin kök öğesi.</span><span class="sxs-lookup"><span data-stu-id="9f584-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f584-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f584-135">Remarks</span></span>  
 <span data-ttu-id="9f584-136">Hizmetleri tanımlanmış `services` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="9f584-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="9f584-137">Bir derlemeyi Hizmetleri herhangi bir sayıda içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9f584-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="9f584-138">Her hizmetin kendi vardır `service` yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="9f584-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="9f584-139">Bu bölümde ve içeriğini hizmet sözleşmesini, davranış ve belirli bir hizmet uç noktalarına tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9f584-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="9f584-140">`behaviorConfiguration` Öğesidir Ayrıca isteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9f584-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="9f584-141">Hizmet davranışını tanımlayan kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f584-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="9f584-142">Bu öznitelikte belirtilen davranışı aynı yapılandırma dosyası kapsamındaki bir davranış bağlanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f584-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="9f584-143">Her hizmet bir veya daha fazla uç noktalar, kendi adres ve bağlama olan kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="9f584-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="9f584-144">Yapılandırma dosyasının içinde kullanılan tüm bağlamaları dosya kapsamında tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f584-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="9f584-145">Bağlama uç noktaları özniteliklerini birleşimi yoluyla bağlı `name` ve `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="9f584-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="9f584-146">`name` Özniteliğini bağlama tanımlanmış bölüm açıklar.</span><span class="sxs-lookup"><span data-stu-id="9f584-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="9f584-147">`bindingConfiguration` Öznitelik tanımlar bağlama bölüm içindeki hangi yapılandırma kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f584-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="9f584-148">Bir bağlama bölümü birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f584-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f584-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f584-149">Example</span></span>  
 <span data-ttu-id="9f584-150">Bu, bir hizmet yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9f584-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f584-151">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f584-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="9f584-152">Hizmetleri Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f584-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
