---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855384"
---
# <a name="endpoint-element"></a><span data-ttu-id="f55e5-102">\<uç nokta > öğesi</span><span class="sxs-lookup"><span data-stu-id="f55e5-102">\<endpoint> element</span></span>
<span data-ttu-id="f55e5-103">Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
<span data-ttu-id="f55e5-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f55e5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f55e5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f55e5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f55e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="f55e5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="f55e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="f55e5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="f55e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<uç nokta >**</span><span class="sxs-lookup"><span data-stu-id="f55e5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f55e5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f55e5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f55e5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55e5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f55e5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f55e5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f55e5-112">Attributes</span></span>  
  
|<span data-ttu-id="f55e5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f55e5-113">Attribute</span></span>|<span data-ttu-id="f55e5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55e5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f55e5-115">adres</span><span class="sxs-lookup"><span data-stu-id="f55e5-115">address</span></span>|<span data-ttu-id="f55e5-116">Bitiş noktasının adresini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-116">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="f55e5-117">Adres mutlak veya göreli bir adres olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-117">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="f55e5-118">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-118">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="f55e5-119">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-119">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="f55e5-120">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="f55e5-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="f55e5-121">behaviorConfiguration</span></span>|<span data-ttu-id="f55e5-122">Uç noktada kullanılacak davranışın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-122">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="f55e5-123">bağlama</span><span class="sxs-lookup"><span data-stu-id="f55e5-123">binding</span></span>|<span data-ttu-id="f55e5-124">Kullanılacak bağlamanın türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="f55e5-124">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="f55e5-125">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="f55e5-126">Tür, bağlamanın tür adı değil, Bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-126">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="f55e5-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="f55e5-127">bindingConfiguration</span></span>|<span data-ttu-id="f55e5-128">Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-128">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="f55e5-129">Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-129">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="f55e5-130">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-130">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="f55e5-131">Bu öznitelik, yapılandırma dosyasındaki belirli bir `binding` bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-131">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="f55e5-132">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f55e5-132">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="f55e5-133">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-133">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="f55e5-134">bindingName</span><span class="sxs-lookup"><span data-stu-id="f55e5-134">bindingName</span></span>|<span data-ttu-id="f55e5-135">WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-135">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="f55e5-136">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-136">The default is an empty string.</span></span>|  
|<span data-ttu-id="f55e5-137">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="f55e5-137">bindingNamespace</span></span>|<span data-ttu-id="f55e5-138">WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-138">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="f55e5-139">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="f55e5-140">contract</span><span class="sxs-lookup"><span data-stu-id="f55e5-140">contract</span></span>|<span data-ttu-id="f55e5-141">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-141">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="f55e5-142">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-142">The assembly must implement the contract type.</span></span> <span data-ttu-id="f55e5-143">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-143">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="f55e5-144">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-144">The default is an empty string.</span></span>|  
|<span data-ttu-id="f55e5-145">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="f55e5-145">endpointConfiguration</span></span>|<span data-ttu-id="f55e5-146">Bu standart uç noktanın ek yapılandırma bilgilerine başvuran `kind` özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-146">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="f55e5-147">`<standardEndpoints>` Bölümünde aynı ad tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-147">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="f55e5-148">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="f55e5-148">isSystemEndpoint</span></span>|<span data-ttu-id="f55e5-149">Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="f55e5-149">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="f55e5-150">kind</span><span class="sxs-lookup"><span data-stu-id="f55e5-150">kind</span></span>|<span data-ttu-id="f55e5-151">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-151">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="f55e5-152">Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f55e5-152">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="f55e5-153">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="f55e5-153">listenUriMode</span></span>|<span data-ttu-id="f55e5-154">Taşımanın hizmetin dinlemesi için `ListenUri` belirtilen şekilde nasıl davrandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-154">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="f55e5-155">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="f55e5-155">Valid values are</span></span><br /><br /> <span data-ttu-id="f55e5-156">-Explicit</span><span class="sxs-lookup"><span data-stu-id="f55e5-156">-   Explicit</span></span><br /><span data-ttu-id="f55e5-157">-Benzersiz</span><span class="sxs-lookup"><span data-stu-id="f55e5-157">-   Unique</span></span><br /><br /> <span data-ttu-id="f55e5-158">Varsayılan değer açıktır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-158">The default value is Explicit.</span></span>|  
|<span data-ttu-id="f55e5-159">Öğesini</span><span class="sxs-lookup"><span data-stu-id="f55e5-159">listenUri</span></span>|<span data-ttu-id="f55e5-160">Hizmet uç noktasının dinlediği URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-160">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="f55e5-161">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-161">The default is an empty string.</span></span>|  
|<span data-ttu-id="f55e5-162">name</span><span class="sxs-lookup"><span data-stu-id="f55e5-162">name</span></span>|<span data-ttu-id="f55e5-163">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f55e5-163">Optional attribute.</span></span> <span data-ttu-id="f55e5-164">Hizmet uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f55e5-164">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="f55e5-165">Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="f55e5-165">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="f55e5-166">Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç `name` noktanın özniteliği hizmetin adından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f55e5-166">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f55e5-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55e5-167">Child Elements</span></span>  
  
|<span data-ttu-id="f55e5-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="f55e5-168">Element</span></span>|<span data-ttu-id="f55e5-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55e5-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f55e5-170">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="f55e5-170">\<headers></span></span>](headers.md)|<span data-ttu-id="f55e5-171">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f55e5-171">A collection of address headers.</span></span>|  
|[<span data-ttu-id="f55e5-172">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="f55e5-172">\<identity></span></span>](identity.md)|<span data-ttu-id="f55e5-173">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="f55e5-173">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f55e5-174">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f55e5-174">Parent Elements</span></span>  
  
|<span data-ttu-id="f55e5-175">Öğe</span><span class="sxs-lookup"><span data-stu-id="f55e5-175">Element</span></span>|<span data-ttu-id="f55e5-176">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f55e5-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f55e5-177">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="f55e5-177">\<service></span></span>](service.md)|<span data-ttu-id="f55e5-178">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="f55e5-178">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f55e5-179">Örnek</span><span class="sxs-lookup"><span data-stu-id="f55e5-179">Example</span></span>  
 <span data-ttu-id="f55e5-180">Bu, hizmet uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="f55e5-180">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f55e5-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f55e5-181">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="f55e5-182">Noktalarının Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="f55e5-182">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="f55e5-183">Nasıl yapılır: Yapılandırmada bir hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="f55e5-183">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
