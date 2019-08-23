---
title: <endpoint> / <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 2bf59972ff2f75995e94a3c1934e88944d65fcc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919107"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="ef9b5-102">\<\<istemci > uç noktası ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="ef9b5-103">İstemciler tarafından sunucudaki hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktasının sözleşme, bağlama ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="ef9b5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef9b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef9b5-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-105">\<client></span></span>  
<span data-ttu-id="ef9b5-106">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef9b5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef9b5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef9b5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef9b5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ef9b5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef9b5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef9b5-110">Attributes</span></span>  
  
|<span data-ttu-id="ef9b5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef9b5-111">Attribute</span></span>|<span data-ttu-id="ef9b5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef9b5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef9b5-113">adres</span><span class="sxs-lookup"><span data-stu-id="ef9b5-113">address</span></span>|<span data-ttu-id="ef9b5-114">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef9b5-115">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="ef9b5-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-116">The default is an empty string.</span></span> <span data-ttu-id="ef9b5-117">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="ef9b5-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef9b5-118">behaviorConfiguration</span></span>|<span data-ttu-id="ef9b5-119">Uç noktanın örneğini oluşturmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="ef9b5-120">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="ef9b5-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="ef9b5-122">bağlama</span><span class="sxs-lookup"><span data-stu-id="ef9b5-122">binding</span></span>|<span data-ttu-id="ef9b5-123">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef9b5-124">Kullanılacak bağlamanın türünü gösteren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="ef9b5-125">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="ef9b5-126">Tür, bağlamanın tür adı yerine bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="ef9b5-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef9b5-127">bindingConfiguration</span></span>|<span data-ttu-id="ef9b5-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-128">Optional.</span></span> <span data-ttu-id="ef9b5-129">Uç nokta örneği oluşturulurken kullanılacak bağlama yapılandırmasının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="ef9b5-130">Bağlama yapılandırması, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="ef9b5-131">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ef9b5-132">Bu öznitelik, yapılandırma dosyasındaki belirli bir `binding` bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="ef9b5-133">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="ef9b5-134">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="ef9b5-135">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="ef9b5-135">contract</span></span>|<span data-ttu-id="ef9b5-136">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef9b5-137">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="ef9b5-138">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="ef9b5-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef9b5-139">endpointConfiguration</span></span>|<span data-ttu-id="ef9b5-140">Bu standart uç noktanın ek yapılandırma bilgilerine başvuran `kind` özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="ef9b5-141">`<standardEndpoints>` Bölümünde aynı ad tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="ef9b5-142">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="ef9b5-142">kind</span></span>|<span data-ttu-id="ef9b5-143">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="ef9b5-144">Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse, ortak bir kanal uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="ef9b5-145">name</span><span class="sxs-lookup"><span data-stu-id="ef9b5-145">name</span></span>|<span data-ttu-id="ef9b5-146">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-146">Optional string attribute.</span></span> <span data-ttu-id="ef9b5-147">Bu öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="ef9b5-148">Belirli bir sözleşme türü için birden çok istemci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="ef9b5-149">Her tanım benzersiz bir yapılandırma adıyla farklılaştıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="ef9b5-150">Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="ef9b5-151">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ef9b5-152">Bir `name` bağlamanın özniteliği WSDL aracılığıyla tanım dışarı aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef9b5-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef9b5-153">Child Elements</span></span>  
  
|<span data-ttu-id="ef9b5-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef9b5-154">Element</span></span>|<span data-ttu-id="ef9b5-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef9b5-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef9b5-156">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-156">\<headers></span></span>](headers.md)|<span data-ttu-id="ef9b5-157">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ef9b5-158">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-158">\<identity></span></span>](identity.md)|<span data-ttu-id="ef9b5-159">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef9b5-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef9b5-160">Parent Elements</span></span>  
  
|<span data-ttu-id="ef9b5-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef9b5-161">Element</span></span>|<span data-ttu-id="ef9b5-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef9b5-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef9b5-163">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ef9b5-163">\<client></span></span>](client.md)|<span data-ttu-id="ef9b5-164">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef9b5-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef9b5-165">Example</span></span>  
 <span data-ttu-id="ef9b5-166">Bu bir kanal uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="ef9b5-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef9b5-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="ef9b5-168">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ef9b5-168">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="ef9b5-169">İstemciler</span><span class="sxs-lookup"><span data-stu-id="ef9b5-169">Clients</span></span>](../../../wcf/feature-details/clients.md)
