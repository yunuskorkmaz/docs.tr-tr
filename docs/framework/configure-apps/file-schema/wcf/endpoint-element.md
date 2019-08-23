---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 71ddb3b860870ee8feeeb36c3f64fa7bfebb0f10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925820"
---
# <a name="endpoint-element"></a><span data-ttu-id="2b863-102">\<uç nokta > öğesi</span><span class="sxs-lookup"><span data-stu-id="2b863-102">\<endpoint> element</span></span>
<span data-ttu-id="2b863-103">Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b863-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="2b863-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2b863-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2b863-105">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="2b863-105">\<service></span></span>  
<span data-ttu-id="2b863-106">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="2b863-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b863-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b863-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b863-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b863-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2b863-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2b863-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b863-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b863-110">Attributes</span></span>  
  
|<span data-ttu-id="2b863-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2b863-111">Attribute</span></span>|<span data-ttu-id="2b863-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b863-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b863-113">adres</span><span class="sxs-lookup"><span data-stu-id="2b863-113">address</span></span>|<span data-ttu-id="2b863-114">Bitiş noktasının adresini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="2b863-115">Adres mutlak veya göreli bir adres olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b863-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="2b863-116">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="2b863-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="2b863-117">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="2b863-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="2b863-118">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="2b863-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b863-119">behaviorConfiguration</span></span>|<span data-ttu-id="2b863-120">Uç noktada kullanılacak davranışın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="2b863-121">bağlama</span><span class="sxs-lookup"><span data-stu-id="2b863-121">binding</span></span>|<span data-ttu-id="2b863-122">Kullanılacak bağlamanın türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2b863-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="2b863-123">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b863-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="2b863-124">Tür, bağlamanın tür adı değil, Bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="2b863-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="2b863-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b863-125">bindingConfiguration</span></span>|<span data-ttu-id="2b863-126">Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="2b863-127">Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b863-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="2b863-128">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2b863-129">Bu öznitelik, yapılandırma dosyasındaki belirli bir `binding` bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b863-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="2b863-130">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2b863-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="2b863-131">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2b863-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="2b863-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="2b863-132">bindingName</span></span>|<span data-ttu-id="2b863-133">WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="2b863-134">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="2b863-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="2b863-135">bindingNamespace</span></span>|<span data-ttu-id="2b863-136">WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="2b863-137">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="2b863-138">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="2b863-138">contract</span></span>|<span data-ttu-id="2b863-139">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="2b863-140">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b863-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="2b863-141">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b863-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="2b863-142">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="2b863-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="2b863-143">endpointConfiguration</span></span>|<span data-ttu-id="2b863-144">Bu standart uç noktanın ek yapılandırma bilgilerine başvuran `kind` özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="2b863-145">`<standardEndpoints>` Bölümünde aynı ad tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b863-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="2b863-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="2b863-146">isSystemEndpoint</span></span>|<span data-ttu-id="2b863-147">Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="2b863-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="2b863-148">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="2b863-148">kind</span></span>|<span data-ttu-id="2b863-149">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="2b863-150">Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b863-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="2b863-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="2b863-151">listenUriMode</span></span>|<span data-ttu-id="2b863-152">Taşımanın hizmetin dinlemesi için `ListenUri` belirtilen şekilde nasıl davrandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b863-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="2b863-153">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="2b863-153">Valid values are</span></span><br /><br /> <span data-ttu-id="2b863-154">-Explicit</span><span class="sxs-lookup"><span data-stu-id="2b863-154">-   Explicit</span></span><br /><span data-ttu-id="2b863-155">-Benzersiz</span><span class="sxs-lookup"><span data-stu-id="2b863-155">-   Unique</span></span><br /><br /> <span data-ttu-id="2b863-156">Varsayılan değer açıktır.</span><span class="sxs-lookup"><span data-stu-id="2b863-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="2b863-157">Öğesini</span><span class="sxs-lookup"><span data-stu-id="2b863-157">listenUri</span></span>|<span data-ttu-id="2b863-158">Hizmet uç noktasının dinlediği URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="2b863-159">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="2b863-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="2b863-160">name</span><span class="sxs-lookup"><span data-stu-id="2b863-160">name</span></span>|<span data-ttu-id="2b863-161">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="2b863-161">Optional attribute.</span></span> <span data-ttu-id="2b863-162">Hizmet uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2b863-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="2b863-163">Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="2b863-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="2b863-164">Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç `name` noktanın özniteliği hizmetin adından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2b863-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b863-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b863-165">Child Elements</span></span>  
  
|<span data-ttu-id="2b863-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b863-166">Element</span></span>|<span data-ttu-id="2b863-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b863-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b863-168">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="2b863-168">\<headers></span></span>](headers.md)|<span data-ttu-id="2b863-169">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="2b863-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="2b863-170">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="2b863-170">\<identity></span></span>](identity.md)|<span data-ttu-id="2b863-171">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="2b863-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b863-172">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2b863-172">Parent Elements</span></span>  
  
|<span data-ttu-id="2b863-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="2b863-173">Element</span></span>|<span data-ttu-id="2b863-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b863-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b863-175">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="2b863-175">\<service></span></span>](service.md)|<span data-ttu-id="2b863-176">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="2b863-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b863-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b863-177">Example</span></span>  
 <span data-ttu-id="2b863-178">Bu, hizmet uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2b863-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="2b863-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b863-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="2b863-180">Noktalarının Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="2b863-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="2b863-181">Nasıl yapılır: Yapılandırmada bir hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b863-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
