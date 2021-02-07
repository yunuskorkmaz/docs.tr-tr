---
description: 'Daha fazla bilgi edinin: <endpoint> öğesi'
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: d5555ae895e6655d1ce6e3dcb026ddec3ff8cf44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725811"
---
# <a name="endpoint-element"></a><span data-ttu-id="5ac8a-103">\<endpoint> öğesi</span><span class="sxs-lookup"><span data-stu-id="5ac8a-103">\<endpoint> element</span></span>

<span data-ttu-id="5ac8a-104">Hizmetleri açığa çıkarmak için kullanılan bir hizmet uç noktası için bağlama, anlaşma ve adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-104">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="5ac8a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ac8a-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ac8a-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac8a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5ac8a-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ac8a-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ac8a-108">Attributes</span></span>  
  
|<span data-ttu-id="5ac8a-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ac8a-109">Attribute</span></span>|<span data-ttu-id="5ac8a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac8a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ac8a-111">adres</span><span class="sxs-lookup"><span data-stu-id="5ac8a-111">address</span></span>|<span data-ttu-id="5ac8a-112">Bitiş noktasının adresini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-112">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="5ac8a-113">Adres mutlak veya göreli bir adres olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-113">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="5ac8a-114">Göreli bir adres sağlanmışsa, konağın bağlamada kullanılan aktarım şemasına uygun bir temel adres sağlaması beklenir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-114">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="5ac8a-115">Bir adres yapılandırılmamışsa, taban adresin bu uç noktanın adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-115">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="5ac8a-116">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-116">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ac8a-117">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ac8a-117">behaviorConfiguration</span></span>|<span data-ttu-id="5ac8a-118">Uç noktada kullanılacak davranışın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-118">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="5ac8a-119">bağlama</span><span class="sxs-lookup"><span data-stu-id="5ac8a-119">binding</span></span>|<span data-ttu-id="5ac8a-120">Kullanılacak bağlamanın türünü belirten gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-120">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="5ac8a-121">Bu tür, başvurulmak üzere kayıtlı bir yapılandırma bölümüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-121">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="5ac8a-122">Tür, bağlamanın tür adı değil, Bölüm adı tarafından kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-122">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="5ac8a-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ac8a-123">bindingConfiguration</span></span>|<span data-ttu-id="5ac8a-124">Uç nokta örneği oluşturulurken kullanılacak bağlamanın bağlama adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-124">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="5ac8a-125">Bağlama adı, bitiş noktasının tanımlandığı noktada kapsam içinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-125">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="5ac8a-126">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-126">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5ac8a-127">Bu öznitelik, `binding` yapılandırma dosyasındaki belirli bir bağlama yapılandırmasına başvurmak için ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-127">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="5ac8a-128">Özel bir bağlama kullanmaya çalışıyorsanız bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-128">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="5ac8a-129">Aksi takdirde, bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-129">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="5ac8a-130">bindingName</span><span class="sxs-lookup"><span data-stu-id="5ac8a-130">bindingName</span></span>|<span data-ttu-id="5ac8a-131">WSDL ile tanım dışarı aktarma için bağlamanın benzersiz nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-131">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="5ac8a-132">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ac8a-133">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="5ac8a-133">bindingNamespace</span></span>|<span data-ttu-id="5ac8a-134">WSDL ile tanım dışarı aktarma için bağlama ad alanının nitelenmiş adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-134">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="5ac8a-135">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-135">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ac8a-136">Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="5ac8a-136">contract</span></span>|<span data-ttu-id="5ac8a-137">Bu uç noktanın hangi sözleşmeyi açığa çıkardığını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="5ac8a-138">Derlemenin anlaşma türünü uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-138">The assembly must implement the contract type.</span></span> <span data-ttu-id="5ac8a-139">Bir hizmet uygulamasının tek bir anlaşma türü uygularsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-139">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="5ac8a-140">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-140">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ac8a-141">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ac8a-141">endpointConfiguration</span></span>|<span data-ttu-id="5ac8a-142">`kind`Bu standart uç noktanın ek yapılandırma bilgilerine başvuran özniteliği tarafından ayarlanan standart uç nokta adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-142">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="5ac8a-143">Bölümünde aynı ad tanımlanmalıdır `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="5ac8a-143">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="5ac8a-144">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="5ac8a-144">isSystemEndpoint</span></span>|<span data-ttu-id="5ac8a-145">Bir uç noktanın altyapı uç noktası olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-145">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="5ac8a-146">denetlenmesi</span><span class="sxs-lookup"><span data-stu-id="5ac8a-146">kind</span></span>|<span data-ttu-id="5ac8a-147">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-147">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="5ac8a-148">Tür, `<extensions>` bölümünde veya machine.config kayıtlı olmalıdır. Hiçbir şey belirtilmemişse ortak bir hizmet uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-148">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="5ac8a-149">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="5ac8a-149">listenUriMode</span></span>|<span data-ttu-id="5ac8a-150">Taşımanın `ListenUri` hizmetin dinlemesi için belirtilen şekilde nasıl davrandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-150">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="5ac8a-151">Geçerli değerler şunlardır</span><span class="sxs-lookup"><span data-stu-id="5ac8a-151">Valid values are</span></span><br /><br /> <span data-ttu-id="5ac8a-152">-Explicit</span><span class="sxs-lookup"><span data-stu-id="5ac8a-152">-   Explicit</span></span><br /><span data-ttu-id="5ac8a-153">-Benzersiz</span><span class="sxs-lookup"><span data-stu-id="5ac8a-153">-   Unique</span></span><br /><br /> <span data-ttu-id="5ac8a-154">Varsayılan değer açıktır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-154">The default value is Explicit.</span></span>|  
|<span data-ttu-id="5ac8a-155">Öğesini</span><span class="sxs-lookup"><span data-stu-id="5ac8a-155">listenUri</span></span>|<span data-ttu-id="5ac8a-156">Hizmet uç noktasının dinlediği URI 'yi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-156">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="5ac8a-157">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-157">The default is an empty string.</span></span>|  
|<span data-ttu-id="5ac8a-158">name</span><span class="sxs-lookup"><span data-stu-id="5ac8a-158">name</span></span>|<span data-ttu-id="5ac8a-159">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-159">Optional attribute.</span></span> <span data-ttu-id="5ac8a-160">Hizmet uç noktasının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-160">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="5ac8a-161">Varsayılan değer, bağlama adı ve anlaşma açıklaması adının bitiştirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-161">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="5ac8a-162">Hizmetlerin birden fazla uç noktası olabilir, bu nedenle uç noktanın `name` özniteliği hizmetin adından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-162">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ac8a-163">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac8a-163">Child Elements</span></span>  
  
|<span data-ttu-id="5ac8a-164">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ac8a-164">Element</span></span>|<span data-ttu-id="5ac8a-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac8a-165">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="5ac8a-166">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-166">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="5ac8a-167">Diğer uç noktalar tarafından ileti alışverişi yapan bir uç noktanın kimlik doğrulamasını sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-167">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ac8a-168">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac8a-168">Parent Elements</span></span>  
  
|<span data-ttu-id="5ac8a-169">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ac8a-169">Element</span></span>|<span data-ttu-id="5ac8a-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac8a-170">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="5ac8a-171">Bir istemcinin bağlanabileceği uç noktaların listesini tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-171">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5ac8a-172">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac8a-172">Example</span></span>  

 <span data-ttu-id="5ac8a-173">Bu, hizmet uç noktası yapılandırmasına bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-173">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ac8a-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac8a-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="5ac8a-175">Uç Noktalar: Adresler, Bağlamalar ve Sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="5ac8a-175">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="5ac8a-176">Nasıl yapılır: Yapılandırma İçinde Hizmet Uç Noktası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ac8a-176">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
