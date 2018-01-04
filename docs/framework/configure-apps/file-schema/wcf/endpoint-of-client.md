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
ms.workload: dotnet
ms.openlocfilehash: 351f49c346cb8126cdd9d540a4db382bf5f4e721
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="fa773-102">&lt;istemci&gt; &lt;uç noktası&gt;</span><span class="sxs-lookup"><span data-stu-id="fa773-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="fa773-103">Sözleşme, bağlama ve istemciler tarafından sunucuda hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktası adresi özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa773-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="fa773-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fa773-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa773-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="fa773-105">\<client></span></span>  
<span data-ttu-id="fa773-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="fa773-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa773-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa773-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa773-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa773-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fa773-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa773-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa773-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa773-110">Attributes</span></span>  
  
|<span data-ttu-id="fa773-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa773-111">Attribute</span></span>|<span data-ttu-id="fa773-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa773-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa773-113">adres</span><span class="sxs-lookup"><span data-stu-id="fa773-113">address</span></span>|<span data-ttu-id="fa773-114">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa773-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa773-115">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa773-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="fa773-116">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa773-116">The default is an empty string.</span></span> <span data-ttu-id="fa773-117">Adres bir mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa773-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="fa773-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa773-118">behaviorConfiguration</span></span>|<span data-ttu-id="fa773-119">Uç nokta örneği oluşturmak için kullanılacak davranış davranışı adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="fa773-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="fa773-120">Davranış adı Hizmet tanımlı bir noktada kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa773-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="fa773-121">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa773-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa773-122">bağlama</span><span class="sxs-lookup"><span data-stu-id="fa773-122">binding</span></span>|<span data-ttu-id="fa773-123">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa773-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa773-124">Kullanılacak bağlama türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa773-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="fa773-125">Tür başvuru için kayıtlı yapılandırma bölümü içermelidir.</span><span class="sxs-lookup"><span data-stu-id="fa773-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="fa773-126">Türü bölümü adıyla yerine bağlama tür adıyla kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fa773-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="fa773-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa773-127">bindingConfiguration</span></span>|<span data-ttu-id="fa773-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fa773-128">Optional.</span></span> <span data-ttu-id="fa773-129">Uç nokta örneği oluşturulduğunda kullanılacak bağlama yapılandırması adını içeren dize.</span><span class="sxs-lookup"><span data-stu-id="fa773-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="fa773-130">Bağlama yapılandırması uç noktaları kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa773-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="fa773-131">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa773-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa773-132">Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki özel bağlama yapılandırma başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="fa773-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="fa773-133">Özel bağlama kullanmaya çalıştığınız gerekiyorsa, bu öznitelik ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fa773-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="fa773-134">Aksi halde, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="fa773-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="fa773-135">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="fa773-135">contract</span></span>|<span data-ttu-id="fa773-136">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa773-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa773-137">Bu uç noktaya sunduğu sözleşmeyi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa773-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="fa773-138">Derleme sözleşme türü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa773-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="fa773-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa773-139">endpointConfiguration</span></span>|<span data-ttu-id="fa773-140">Tarafından belirlenen standart uç noktanın adını belirten dize `kind` standart Bu uç noktanın ek yapılandırma bilgilerini başvuran özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa773-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="fa773-141">Aynı adı tanımlanmalıdır `<standardEndpoints>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="fa773-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="fa773-142">türü</span><span class="sxs-lookup"><span data-stu-id="fa773-142">kind</span></span>|<span data-ttu-id="fa773-143">Standart uç nokta uygulanan türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa773-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="fa773-144">Türü kaydedilmelidir `<extensions>` bölüm veya machine.config dosyasındaki. Hiçbir şey belirtilirse, ortak bir kanal uç oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa773-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="fa773-145">name</span><span class="sxs-lookup"><span data-stu-id="fa773-145">name</span></span>|<span data-ttu-id="fa773-146">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa773-146">Optional string attribute.</span></span> <span data-ttu-id="fa773-147">Bu öznitelik bir uç nokta belirli bir sözleşme için benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa773-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="fa773-148">Belirli bir sözleşme türde birden fazla istemciye tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa773-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="fa773-149">Her tanımı bir benzersiz yapılandırma adıyla Ayrıştırılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa773-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="fa773-150">Bu öznitelik atlanırsa, karşılık gelen endpoint belirtilen sözleşme türüyle ilişkili varsayılan uç noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa773-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="fa773-151">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa773-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa773-152">`name` Özniteliği bağlaması WSDL aracılığıyla tanımı dışa aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa773-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa773-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa773-153">Child Elements</span></span>  
  
|<span data-ttu-id="fa773-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa773-154">Element</span></span>|<span data-ttu-id="fa773-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa773-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa773-156">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="fa773-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="fa773-157">Adres üstbilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fa773-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="fa773-158">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="fa773-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="fa773-159">Bir uç nokta onunla ileti değiş tokuşu diğer uç noktaları tarafından kimlik doğrulamasına olanak tanıyan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="fa773-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa773-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa773-160">Parent Elements</span></span>  
  
|<span data-ttu-id="fa773-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa773-161">Element</span></span>|<span data-ttu-id="fa773-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa773-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa773-163">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="fa773-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="fa773-164">Bir istemcinin bağlanabileceği bitiş noktaları listesini tanımlar yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fa773-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa773-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa773-165">Example</span></span>  
 <span data-ttu-id="fa773-166">Bu, bir kanal uç nokta yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="fa773-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa773-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa773-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [<span data-ttu-id="fa773-168">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="fa773-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="fa773-169">İstemciler</span><span class="sxs-lookup"><span data-stu-id="fa773-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
