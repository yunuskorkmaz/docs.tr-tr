---
title: <endpoint> / <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855325"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="fa833-102">\<\<istemci > uç noktası ></span><span class="sxs-lookup"><span data-stu-id="fa833-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="fa833-103">İstemciler tarafından sunucudaki hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktasının sözleşme, bağlama ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa833-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
<span data-ttu-id="fa833-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fa833-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fa833-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fa833-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fa833-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İstemci >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="fa833-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="fa833-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<uç nokta >**</span><span class="sxs-lookup"><span data-stu-id="fa833-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa833-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa833-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa833-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa833-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fa833-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fa833-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa833-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fa833-111">Attributes</span></span>  
  
|<span data-ttu-id="fa833-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fa833-112">Attribute</span></span>|<span data-ttu-id="fa833-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa833-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa833-114">adres</span><span class="sxs-lookup"><span data-stu-id="fa833-114">address</span></span>|<span data-ttu-id="fa833-115">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa833-115">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa833-116">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa833-116">Specifies the address of the endpoint.</span></span> <span data-ttu-id="fa833-117">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa833-117">The default is an empty string.</span></span> <span data-ttu-id="fa833-118">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-118">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="fa833-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa833-119">behaviorConfiguration</span></span>|<span data-ttu-id="fa833-120">Uç noktanın örneğini oluşturmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-120">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="fa833-121">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-121">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="fa833-122">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa833-122">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa833-123">bağlama</span><span class="sxs-lookup"><span data-stu-id="fa833-123">binding</span></span>|<span data-ttu-id="fa833-124">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa833-124">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa833-125">Kullanılacak bağlamanın türünü gösteren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-125">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="fa833-126">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-126">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="fa833-127">Tür, bağlamanın tür adı yerine bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="fa833-127">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="fa833-128">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa833-128">bindingConfiguration</span></span>|<span data-ttu-id="fa833-129">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="fa833-129">Optional.</span></span> <span data-ttu-id="fa833-130">Uç nokta örneği oluşturulurken kullanılacak bağlama yapılandırmasının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-130">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="fa833-131">Bağlama yapılandırması, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-131">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="fa833-132">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa833-132">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa833-133">Bu öznitelik, yapılandırma dosyasındaki belirli bir `binding` bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa833-133">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="fa833-134">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa833-134">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="fa833-135">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="fa833-135">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="fa833-136">contract</span><span class="sxs-lookup"><span data-stu-id="fa833-136">contract</span></span>|<span data-ttu-id="fa833-137">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa833-137">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fa833-138">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-138">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="fa833-139">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa833-139">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="fa833-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa833-140">endpointConfiguration</span></span>|<span data-ttu-id="fa833-141">Bu standart uç noktanın ek yapılandırma bilgilerine başvuran `kind` özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="fa833-142">`<standardEndpoints>` Bölümünde aynı ad tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="fa833-143">kind</span><span class="sxs-lookup"><span data-stu-id="fa833-143">kind</span></span>|<span data-ttu-id="fa833-144">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fa833-144">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="fa833-145">Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse, ortak bir kanal uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fa833-145">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="fa833-146">name</span><span class="sxs-lookup"><span data-stu-id="fa833-146">name</span></span>|<span data-ttu-id="fa833-147">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fa833-147">Optional string attribute.</span></span> <span data-ttu-id="fa833-148">Bu öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa833-148">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="fa833-149">Belirli bir sözleşme türü için birden çok istemci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa833-149">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="fa833-150">Her tanım benzersiz bir yapılandırma adıyla farklılaştıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa833-150">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="fa833-151">Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa833-151">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="fa833-152">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="fa833-152">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa833-153">Bir `name` bağlamanın özniteliği WSDL aracılığıyla tanım dışarı aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fa833-153">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa833-154">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa833-154">Child Elements</span></span>  
  
|<span data-ttu-id="fa833-155">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa833-155">Element</span></span>|<span data-ttu-id="fa833-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa833-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa833-157">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="fa833-157">\<headers></span></span>](headers.md)|<span data-ttu-id="fa833-158">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="fa833-158">A collection of address headers.</span></span>|  
|[<span data-ttu-id="fa833-159">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="fa833-159">\<identity></span></span>](identity.md)|<span data-ttu-id="fa833-160">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="fa833-160">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa833-161">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fa833-161">Parent Elements</span></span>  
  
|<span data-ttu-id="fa833-162">Öğe</span><span class="sxs-lookup"><span data-stu-id="fa833-162">Element</span></span>|<span data-ttu-id="fa833-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa833-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa833-164">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="fa833-164">\<client></span></span>](client.md)|<span data-ttu-id="fa833-165">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fa833-165">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa833-166">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa833-166">Example</span></span>  
 <span data-ttu-id="fa833-167">Bu bir kanal uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="fa833-167">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="fa833-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa833-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="fa833-169">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="fa833-169">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="fa833-170">İstemciler</span><span class="sxs-lookup"><span data-stu-id="fa833-170">Clients</span></span>](../../../wcf/feature-details/clients.md)
