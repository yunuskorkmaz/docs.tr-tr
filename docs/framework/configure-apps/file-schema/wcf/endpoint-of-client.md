---
description: 'Hakkında daha fazla bilgi <endpoint> edinin: <client>'
title: <endpoint> / <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 4ace6d49ba18524729925b20cf08e5d57bcc40c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725791"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="dc79d-103">\<endpoint> / \<client></span><span class="sxs-lookup"><span data-stu-id="dc79d-103">\<endpoint> of \<client></span></span>

<span data-ttu-id="dc79d-104">İstemciler tarafından sunucudaki hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktasının sözleşme, bağlama ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-104">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="dc79d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc79d-105">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc79d-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc79d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dc79d-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc79d-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc79d-108">Attributes</span></span>  
  
|<span data-ttu-id="dc79d-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dc79d-109">Attribute</span></span>|<span data-ttu-id="dc79d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc79d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dc79d-111">adres</span><span class="sxs-lookup"><span data-stu-id="dc79d-111">address</span></span>|<span data-ttu-id="dc79d-112">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc79d-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="dc79d-113">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-113">Specifies the address of the endpoint.</span></span> <span data-ttu-id="dc79d-114">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-114">The default is an empty string.</span></span> <span data-ttu-id="dc79d-115">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-115">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="dc79d-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc79d-116">behaviorConfiguration</span></span>|<span data-ttu-id="dc79d-117">Uç noktanın örneğini oluşturmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-117">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="dc79d-118">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-118">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="dc79d-119">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-119">The default is an empty string.</span></span>|  
|<span data-ttu-id="dc79d-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="dc79d-120">binding</span></span>|<span data-ttu-id="dc79d-121">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc79d-121">Required string attribute.</span></span><br /><br /> <span data-ttu-id="dc79d-122">Kullanılacak bağlamanın türünü gösteren bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-122">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="dc79d-123">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="dc79d-124">Tür, bağlamanın tür adı yerine bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-124">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="dc79d-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc79d-125">bindingConfiguration</span></span>|<span data-ttu-id="dc79d-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="dc79d-126">Optional.</span></span> <span data-ttu-id="dc79d-127">Uç nokta örneği oluşturulurken kullanılacak bağlama yapılandırmasının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-127">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="dc79d-128">Bağlama yapılandırması, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-128">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="dc79d-129">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-129">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="dc79d-130">Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-130">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="dc79d-131">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc79d-131">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="dc79d-132">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-132">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="dc79d-133">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="dc79d-133">contract</span></span>|<span data-ttu-id="dc79d-134">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc79d-134">Required string attribute.</span></span><br /><br /> <span data-ttu-id="dc79d-135">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-135">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="dc79d-136">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-136">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="dc79d-137">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="dc79d-137">endpointConfiguration</span></span>|<span data-ttu-id="dc79d-138">`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-138">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="dc79d-139">Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="dc79d-139">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="dc79d-140">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="dc79d-140">kind</span></span>|<span data-ttu-id="dc79d-141">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="dc79d-141">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="dc79d-142">Tür, `<extensions>` bölümünde veya machine.config kayıtlı olmalıdır. Hiçbir şey belirtilmemişse, ortak bir kanal uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dc79d-142">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="dc79d-143">name</span><span class="sxs-lookup"><span data-stu-id="dc79d-143">name</span></span>|<span data-ttu-id="dc79d-144">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="dc79d-144">Optional string attribute.</span></span> <span data-ttu-id="dc79d-145">Bu öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dc79d-145">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="dc79d-146">Belirli bir sözleşme türü için birden çok istemci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc79d-146">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="dc79d-147">Her tanım benzersiz bir yapılandırma adıyla farklılaştıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-147">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="dc79d-148">Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-148">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="dc79d-149">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-149">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="dc79d-150">`name`Bir bağlamanın ÖZNITELIĞI WSDL aracılığıyla tanım dışarı aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc79d-150">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc79d-151">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc79d-151">Child Elements</span></span>  
  
|<span data-ttu-id="dc79d-152">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc79d-152">Element</span></span>|<span data-ttu-id="dc79d-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc79d-153">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="dc79d-154">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="dc79d-154">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="dc79d-155">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="dc79d-155">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dc79d-156">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc79d-156">Parent Elements</span></span>  
  
|<span data-ttu-id="dc79d-157">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc79d-157">Element</span></span>|<span data-ttu-id="dc79d-158">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc79d-158">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="dc79d-159">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="dc79d-159">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dc79d-160">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc79d-160">Example</span></span>  

 <span data-ttu-id="dc79d-161">Bu bir kanal uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="dc79d-161">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="dc79d-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc79d-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="dc79d-163">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="dc79d-163">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="dc79d-164">İstemciler</span><span class="sxs-lookup"><span data-stu-id="dc79d-164">Clients</span></span>](../../../wcf/feature-details/clients.md)
