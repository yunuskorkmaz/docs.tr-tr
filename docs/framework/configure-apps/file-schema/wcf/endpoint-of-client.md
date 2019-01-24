---
title: '&lt;istemci&gt; &lt;uç noktası&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: a7d95ee819c911d80178e38a37aeaccc5b1f1764
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598311"
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="ae6bc-102">&lt;istemci&gt; &lt;uç noktası&gt;</span><span class="sxs-lookup"><span data-stu-id="ae6bc-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="ae6bc-103">Sözleşmeyi, bağlamayı ve istemciler tarafından sunucu üzerinde hizmet uç noktalarına bağlanmak için kullanılan kanal uç noktalarının adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="ae6bc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae6bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae6bc-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ae6bc-105">\<client></span></span>  
<span data-ttu-id="ae6bc-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="ae6bc-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae6bc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae6bc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae6bc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae6bc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ae6bc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae6bc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae6bc-110">Attributes</span></span>  
  
|<span data-ttu-id="ae6bc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae6bc-111">Attribute</span></span>|<span data-ttu-id="ae6bc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae6bc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae6bc-113">adres</span><span class="sxs-lookup"><span data-stu-id="ae6bc-113">address</span></span>|<span data-ttu-id="ae6bc-114">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ae6bc-115">Uç nokta adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="ae6bc-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-116">The default is an empty string.</span></span> <span data-ttu-id="ae6bc-117">Adres mutlak URI olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="ae6bc-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae6bc-118">behaviorConfiguration</span></span>|<span data-ttu-id="ae6bc-119">Uç noktayı örneklemek için kullanılacak davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="ae6bc-120">Davranış adı, hizmet tanımlı bir noktada kapsam içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="ae6bc-121">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="ae6bc-122">bağlama</span><span class="sxs-lookup"><span data-stu-id="ae6bc-122">binding</span></span>|<span data-ttu-id="ae6bc-123">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ae6bc-124">Kullanılacak bağlamanın türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="ae6bc-125">Türü, başvurulabilmesi için kayıtlı yapılandırma bölümü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="ae6bc-126">Türü bölüm adına göre yerine bağlama türü adına göre kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="ae6bc-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae6bc-127">bindingConfiguration</span></span>|<span data-ttu-id="ae6bc-128">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-128">Optional.</span></span> <span data-ttu-id="ae6bc-129">Uç nokta örneklendiğinde kullanılan bağlama yapılandırmasının adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="ae6bc-130">Bağlama yapılandırma uç noktaları kapsamında olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="ae6bc-131">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ae6bc-132">Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki belirli bağlama yapılandırması başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="ae6bc-133">Özel bağlama kullanmaya çalışıyorsunuz. Bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="ae6bc-134">Aksi takdirde, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="ae6bc-135">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="ae6bc-135">contract</span></span>|<span data-ttu-id="ae6bc-136">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ae6bc-137">Hangi anlaşmanın gösteren bir dize bu koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="ae6bc-138">Derleme sözleşme türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="ae6bc-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae6bc-139">endpointConfiguration</span></span>|<span data-ttu-id="ae6bc-140">Tarafından ayarlanan standart bitiş noktası adını belirten bir dize `kind` bu standart bitiş noktası ek yapılandırma bilgilerinie başvuran öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="ae6bc-141">Aynı ada tanımlanmalıdır `<standardEndpoints>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="ae6bc-142">tür</span><span class="sxs-lookup"><span data-stu-id="ae6bc-142">kind</span></span>|<span data-ttu-id="ae6bc-143">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="ae6bc-144">Türü kayıtlı olmalıdır `<extensions>` bölüm veya machine.config. Hiçbir şey belirtilmezse, ortak bir kanal uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="ae6bc-145">name</span><span class="sxs-lookup"><span data-stu-id="ae6bc-145">name</span></span>|<span data-ttu-id="ae6bc-146">İsteğe bağlı dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-146">Optional string attribute.</span></span> <span data-ttu-id="ae6bc-147">Bu öznitelik, bir uç nokta verilen bir sözleşme için benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="ae6bc-148">Verilen bir sözleşme türü için birden çok istemci tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="ae6bc-149">Her tanımı bir benzersiz yapılandırma adına göre ayırt edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="ae6bc-150">Bu öznitelik belirtilmezse, karşılık gelen uç noktası belirtilen sözleşme türü ile ilişkili varsayılan uç nokta olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="ae6bc-151">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ae6bc-152">`name` Bağlama özniteliği WSDL dışa aktarım tanımı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae6bc-153">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae6bc-153">Child Elements</span></span>  
  
|<span data-ttu-id="ae6bc-154">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae6bc-154">Element</span></span>|<span data-ttu-id="ae6bc-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae6bc-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae6bc-156">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="ae6bc-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="ae6bc-157">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ae6bc-158">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="ae6bc-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ae6bc-159">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae6bc-160">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae6bc-160">Parent Elements</span></span>  
  
|<span data-ttu-id="ae6bc-161">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae6bc-161">Element</span></span>|<span data-ttu-id="ae6bc-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae6bc-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae6bc-163">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="ae6bc-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="ae6bc-164">Bir istemcinin bağlanabileceği uç noktaları listesi tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae6bc-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae6bc-165">Example</span></span>  
 <span data-ttu-id="ae6bc-166">Bu, bir kanal uç nokta yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="ae6bc-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae6bc-167">See also</span></span>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="ae6bc-168">WCF İstemci Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ae6bc-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="ae6bc-169">İstemciler</span><span class="sxs-lookup"><span data-stu-id="ae6bc-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
