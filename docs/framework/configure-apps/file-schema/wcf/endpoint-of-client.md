---
title: "&lt;istemci&gt; &lt;uç noktası&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec959a9eeea82c56d6a2ae5ec3a7befce67676e3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="af11d-102">&lt;istemci&gt; &lt;uç noktası&gt;</span><span class="sxs-lookup"><span data-stu-id="af11d-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="af11d-103">Sözleşme, bağlama ve istemciler tarafından sunucuda hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktası adresi özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="af11d-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="af11d-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="af11d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="af11d-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="af11d-105">\<client></span></span>  
<span data-ttu-id="af11d-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="af11d-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af11d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af11d-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af11d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="af11d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="af11d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af11d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af11d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af11d-110">Attributes</span></span>  
  
|<span data-ttu-id="af11d-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af11d-111">Attribute</span></span>|<span data-ttu-id="af11d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af11d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af11d-113">adres</span><span class="sxs-lookup"><span data-stu-id="af11d-113">address</span></span>|<span data-ttu-id="af11d-114">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="af11d-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="af11d-115">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="af11d-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="af11d-116">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="af11d-116">The default is an empty string.</span></span> <span data-ttu-id="af11d-117">Adres bir mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af11d-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="af11d-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="af11d-118">behaviorConfiguration</span></span>|<span data-ttu-id="af11d-119">Uç nokta örneği oluşturmak için kullanılacak davranış davranışı adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="af11d-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="af11d-120">Davranış adı Hizmet tanımlı bir noktada kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af11d-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="af11d-121">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="af11d-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="af11d-122">bağlama</span><span class="sxs-lookup"><span data-stu-id="af11d-122">binding</span></span>|<span data-ttu-id="af11d-123">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="af11d-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="af11d-124">Kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="af11d-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="af11d-125">Tür başvuru için kayıtlı yapılandırma bölümü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="af11d-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="af11d-126">Türü bölümü adıyla yerine bağlama tür adıyla kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="af11d-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="af11d-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="af11d-127">bindingConfiguration</span></span>|<span data-ttu-id="af11d-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="af11d-128">Optional.</span></span> <span data-ttu-id="af11d-129">Uç nokta örneği oluşturulduğunda kullanılacak bağlama yapılandırması adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="af11d-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="af11d-130">Bağlama yapılandırması uç noktaları kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af11d-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="af11d-131">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="af11d-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="af11d-132">Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki özel bağlama yapılandırma başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="af11d-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="af11d-133">Özel bağlama kullanmaya çalıştığınız gerekiyorsa, bu öznitelik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="af11d-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="af11d-134">Aksi halde, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="af11d-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="af11d-135">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="af11d-135">contract</span></span>|<span data-ttu-id="af11d-136">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="af11d-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="af11d-137">Bu uç noktaya sunduğu sözleşmeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="af11d-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="af11d-138">Derleme sözleşme türü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="af11d-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="af11d-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="af11d-139">endpointConfiguration</span></span>|<span data-ttu-id="af11d-140">Tarafından belirlenen standart uç noktanın adını belirten dize `kind` standart Bu uç noktanın ek yapılandırma bilgilerini başvuran özniteliği.</span><span class="sxs-lookup"><span data-stu-id="af11d-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="af11d-141">Aynı adı tanımlanmalıdır `<standardEndpoints>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="af11d-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="af11d-142">türü</span><span class="sxs-lookup"><span data-stu-id="af11d-142">kind</span></span>|<span data-ttu-id="af11d-143">Standart uç nokta uygulanan türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="af11d-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="af11d-144">Türü kaydedilmelidir `<extensions>` bölüm veya machine.config dosyasındaki. Hiçbir şey belirtilirse, ortak bir kanal uç oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af11d-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="af11d-145">name</span><span class="sxs-lookup"><span data-stu-id="af11d-145">name</span></span>|<span data-ttu-id="af11d-146">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="af11d-146">Optional string attribute.</span></span> <span data-ttu-id="af11d-147">Bu öznitelik bir uç nokta belirli bir sözleşme için benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af11d-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="af11d-148">Belirli bir sözleşme türde birden fazla istemciye tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af11d-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="af11d-149">Her tanımı bir benzersiz yapılandırma adıyla Ayrıştırılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="af11d-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="af11d-150">Bu öznitelik atlanırsa, karşılık gelen endpoint belirtilen sözleşme türüyle ilişkili varsayılan uç noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af11d-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="af11d-151">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="af11d-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="af11d-152">`name` Özniteliği bağlaması WSDL aracılığıyla tanımı dışa aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="af11d-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af11d-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="af11d-153">Child Elements</span></span>  
  
|<span data-ttu-id="af11d-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="af11d-154">Element</span></span>|<span data-ttu-id="af11d-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af11d-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af11d-156">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="af11d-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="af11d-157">Adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="af11d-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="af11d-158">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="af11d-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="af11d-159">Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="af11d-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af11d-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="af11d-160">Parent Elements</span></span>  
  
|<span data-ttu-id="af11d-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="af11d-161">Element</span></span>|<span data-ttu-id="af11d-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af11d-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af11d-163">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="af11d-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="af11d-164">Bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="af11d-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af11d-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="af11d-165">Example</span></span>  
 <span data-ttu-id="af11d-166">Bu, bir kanal uç nokta yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="af11d-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af11d-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af11d-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [<span data-ttu-id="af11d-168">WCF istemci yapılandırması</span><span class="sxs-lookup"><span data-stu-id="af11d-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="af11d-169">İstemciler</span><span class="sxs-lookup"><span data-stu-id="af11d-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
