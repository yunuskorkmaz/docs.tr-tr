---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855384"
---
# <a name="endpoint-element"></a><span data-ttu-id="4a7d0-102">\<endpoint> öğesi</span><span class="sxs-lookup"><span data-stu-id="4a7d0-102">\<endpoint> element</span></span>
<span data-ttu-id="4a7d0-103">Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="4a7d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a7d0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a7d0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a7d0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4a7d0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a7d0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a7d0-107">Attributes</span></span>  
  
|<span data-ttu-id="4a7d0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a7d0-108">Attribute</span></span>|<span data-ttu-id="4a7d0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a7d0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a7d0-110">adres</span><span class="sxs-lookup"><span data-stu-id="4a7d0-110">address</span></span>|<span data-ttu-id="4a7d0-111">Bitiş noktasının adresini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-111">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="4a7d0-112">Adres mutlak veya göreli bir adres olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-112">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="4a7d0-113">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-113">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="4a7d0-114">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-114">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="4a7d0-115">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-115">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a7d0-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a7d0-116">behaviorConfiguration</span></span>|<span data-ttu-id="4a7d0-117">Uç noktada kullanılacak davranışın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-117">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="4a7d0-118">bağlama</span><span class="sxs-lookup"><span data-stu-id="4a7d0-118">binding</span></span>|<span data-ttu-id="4a7d0-119">Kullanılacak bağlamanın türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-119">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="4a7d0-120">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-120">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="4a7d0-121">Tür, bağlamanın tür adı değil, Bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-121">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="4a7d0-122">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a7d0-122">bindingConfiguration</span></span>|<span data-ttu-id="4a7d0-123">Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-123">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="4a7d0-124">Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-124">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="4a7d0-125">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-125">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4a7d0-126">Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-126">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="4a7d0-127">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-127">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="4a7d0-128">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-128">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="4a7d0-129">bindingName</span><span class="sxs-lookup"><span data-stu-id="4a7d0-129">bindingName</span></span>|<span data-ttu-id="4a7d0-130">WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-130">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="4a7d0-131">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a7d0-132">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="4a7d0-132">bindingNamespace</span></span>|<span data-ttu-id="4a7d0-133">WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-133">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="4a7d0-134">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a7d0-135">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="4a7d0-135">contract</span></span>|<span data-ttu-id="4a7d0-136">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-136">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="4a7d0-137">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-137">The assembly must implement the contract type.</span></span> <span data-ttu-id="4a7d0-138">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="4a7d0-139">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a7d0-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="4a7d0-140">endpointConfiguration</span></span>|<span data-ttu-id="4a7d0-141">`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="4a7d0-142">Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="4a7d0-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="4a7d0-143">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="4a7d0-143">isSystemEndpoint</span></span>|<span data-ttu-id="4a7d0-144">Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-144">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="4a7d0-145">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="4a7d0-145">kind</span></span>|<span data-ttu-id="4a7d0-146">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-146">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="4a7d0-147">Tür, `<extensions>` bölümüne veya Machine. config dosyasında kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-147">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="4a7d0-148">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="4a7d0-148">listenUriMode</span></span>|<span data-ttu-id="4a7d0-149">Taşımanın `ListenUri` hizmetin dinlemesi için belirtilen şekilde nasıl davrandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-149">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="4a7d0-150">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="4a7d0-150">Valid values are</span></span><br /><br /> <span data-ttu-id="4a7d0-151">-Explicit</span><span class="sxs-lookup"><span data-stu-id="4a7d0-151">-   Explicit</span></span><br /><span data-ttu-id="4a7d0-152">-Benzersiz</span><span class="sxs-lookup"><span data-stu-id="4a7d0-152">-   Unique</span></span><br /><br /> <span data-ttu-id="4a7d0-153">Varsayılan değer açıktır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-153">The default value is Explicit.</span></span>|  
|<span data-ttu-id="4a7d0-154">Öğesini</span><span class="sxs-lookup"><span data-stu-id="4a7d0-154">listenUri</span></span>|<span data-ttu-id="4a7d0-155">Hizmet uç noktasının dinlediği URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-155">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="4a7d0-156">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-156">The default is an empty string.</span></span>|  
|<span data-ttu-id="4a7d0-157">name</span><span class="sxs-lookup"><span data-stu-id="4a7d0-157">name</span></span>|<span data-ttu-id="4a7d0-158">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-158">Optional attribute.</span></span> <span data-ttu-id="4a7d0-159">Hizmet uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-159">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="4a7d0-160">Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-160">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="4a7d0-161">Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç noktanın `name` özniteliği hizmetin adından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-161">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a7d0-162">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a7d0-162">Child Elements</span></span>  
  
|<span data-ttu-id="4a7d0-163">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a7d0-163">Element</span></span>|<span data-ttu-id="4a7d0-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a7d0-164">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="4a7d0-165">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-165">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="4a7d0-166">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-166">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a7d0-167">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a7d0-167">Parent Elements</span></span>  
  
|<span data-ttu-id="4a7d0-168">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a7d0-168">Element</span></span>|<span data-ttu-id="4a7d0-169">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a7d0-169">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="4a7d0-170">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-170">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4a7d0-171">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a7d0-171">Example</span></span>  
 <span data-ttu-id="4a7d0-172">Bu, hizmet uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-172">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a7d0-173">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a7d0-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="4a7d0-174">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="4a7d0-174">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="4a7d0-175">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4a7d0-175">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
