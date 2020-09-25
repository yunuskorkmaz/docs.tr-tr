---
title: <endpoint> / <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 79d827691ec3898ad94af9835077c61ea35990ab
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185853"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="231f1-102">\<endpoint> / \<client></span><span class="sxs-lookup"><span data-stu-id="231f1-102">\<endpoint> of \<client></span></span>

<span data-ttu-id="231f1-103">İstemciler tarafından sunucudaki hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktasının sözleşme, bağlama ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="231f1-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="231f1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="231f1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="231f1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="231f1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="231f1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="231f1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="231f1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="231f1-107">Attributes</span></span>  
  
|<span data-ttu-id="231f1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="231f1-108">Attribute</span></span>|<span data-ttu-id="231f1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="231f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="231f1-110">adres</span><span class="sxs-lookup"><span data-stu-id="231f1-110">address</span></span>|<span data-ttu-id="231f1-111">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="231f1-111">Required string attribute.</span></span><br /><br /> <span data-ttu-id="231f1-112">Uç noktanın adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="231f1-112">Specifies the address of the endpoint.</span></span> <span data-ttu-id="231f1-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="231f1-113">The default is an empty string.</span></span> <span data-ttu-id="231f1-114">Adres, mutlak bir URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231f1-114">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="231f1-115">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="231f1-115">behaviorConfiguration</span></span>|<span data-ttu-id="231f1-116">Uç noktanın örneğini oluşturmak için kullanılacak davranışın davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-116">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="231f1-117">Davranış adı, hizmetin tanımlandığı noktada kapsamda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231f1-117">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="231f1-118">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="231f1-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="231f1-119">bağlama</span><span class="sxs-lookup"><span data-stu-id="231f1-119">binding</span></span>|<span data-ttu-id="231f1-120">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="231f1-120">Required string attribute.</span></span><br /><br /> <span data-ttu-id="231f1-121">Kullanılacak bağlamanın türünü gösteren bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-121">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="231f1-122">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231f1-122">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="231f1-123">Tür, bağlamanın tür adı yerine bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="231f1-123">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="231f1-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="231f1-124">bindingConfiguration</span></span>|<span data-ttu-id="231f1-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="231f1-125">Optional.</span></span> <span data-ttu-id="231f1-126">Uç nokta örneği oluşturulurken kullanılacak bağlama yapılandırmasının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-126">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="231f1-127">Bağlama yapılandırması, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231f1-127">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="231f1-128">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="231f1-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="231f1-129">Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="231f1-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="231f1-130">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="231f1-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="231f1-131">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="231f1-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="231f1-132">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="231f1-132">contract</span></span>|<span data-ttu-id="231f1-133">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="231f1-133">Required string attribute.</span></span><br /><br /> <span data-ttu-id="231f1-134">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-134">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="231f1-135">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="231f1-135">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="231f1-136">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="231f1-136">endpointConfiguration</span></span>|<span data-ttu-id="231f1-137">`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-137">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="231f1-138">Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="231f1-138">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="231f1-139">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="231f1-139">kind</span></span>|<span data-ttu-id="231f1-140">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="231f1-140">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="231f1-141">Tür, `<extensions>` bölümünde veya machine.config kayıtlı olmalıdır. Hiçbir şey belirtilmemişse, ortak bir kanal uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="231f1-141">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="231f1-142">name</span><span class="sxs-lookup"><span data-stu-id="231f1-142">name</span></span>|<span data-ttu-id="231f1-143">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="231f1-143">Optional string attribute.</span></span> <span data-ttu-id="231f1-144">Bu öznitelik, belirli bir sözleşme için bir uç noktayı benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="231f1-144">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="231f1-145">Belirli bir sözleşme türü için birden çok istemci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="231f1-145">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="231f1-146">Her tanım benzersiz bir yapılandırma adıyla farklılaştıralınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="231f1-146">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="231f1-147">Bu öznitelik atlanırsa, ilgili uç nokta belirtilen anlaşma türüyle ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="231f1-147">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="231f1-148">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="231f1-148">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="231f1-149">`name`Bir bağlamanın ÖZNITELIĞI WSDL aracılığıyla tanım dışarı aktarma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="231f1-149">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="231f1-150">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="231f1-150">Child Elements</span></span>  
  
|<span data-ttu-id="231f1-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="231f1-151">Element</span></span>|<span data-ttu-id="231f1-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="231f1-152">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="231f1-153">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="231f1-153">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="231f1-154">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="231f1-154">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="231f1-155">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="231f1-155">Parent Elements</span></span>  
  
|<span data-ttu-id="231f1-156">Öğe</span><span class="sxs-lookup"><span data-stu-id="231f1-156">Element</span></span>|<span data-ttu-id="231f1-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="231f1-157">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="231f1-158">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="231f1-158">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="231f1-159">Örnek</span><span class="sxs-lookup"><span data-stu-id="231f1-159">Example</span></span>  

 <span data-ttu-id="231f1-160">Bu bir kanal uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="231f1-160">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="231f1-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="231f1-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="231f1-162">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="231f1-162">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="231f1-163">İstemciler</span><span class="sxs-lookup"><span data-stu-id="231f1-163">Clients</span></span>](../../../wcf/feature-details/clients.md)
