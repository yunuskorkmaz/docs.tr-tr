---
title: <endpoint> öğesi
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 94b6cc6225171d90164e6d6880e1095513f16ece
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354744"
---
# <a name="endpoint-element"></a><span data-ttu-id="43f37-102">\<uç noktası > öğesi</span><span class="sxs-lookup"><span data-stu-id="43f37-102">\<endpoint> element</span></span>
<span data-ttu-id="43f37-103">Bağlama, anlaşma ve Hizmetleri kullanıma sunmak için kullanılan bir hizmet uç noktası için adres özelliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="43f37-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="43f37-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43f37-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43f37-105">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="43f37-105">\<service></span></span>  
<span data-ttu-id="43f37-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="43f37-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f37-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43f37-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43f37-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43f37-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43f37-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43f37-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43f37-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43f37-110">Attributes</span></span>  
  
|<span data-ttu-id="43f37-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43f37-111">Attribute</span></span>|<span data-ttu-id="43f37-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43f37-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43f37-113">adres</span><span class="sxs-lookup"><span data-stu-id="43f37-113">address</span></span>|<span data-ttu-id="43f37-114">Bitiş noktasının adresini içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="43f37-115">Adres mutlak veya göreli adres olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="43f37-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="43f37-116">Göreli adres sağlanırsa, konak bağlamasında kullanılan aktarım düzeni için uygun bir temel adres sağlamak için bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="43f37-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="43f37-117">Bir adresi yapılandırılmamışsa, temel adresini Bu uç nokta adresi olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="43f37-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="43f37-118">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="43f37-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="43f37-119">behaviorConfiguration</span></span>|<span data-ttu-id="43f37-120">Bitiş noktasında kullanılacak davranış adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="43f37-121">bağlama</span><span class="sxs-lookup"><span data-stu-id="43f37-121">binding</span></span>|<span data-ttu-id="43f37-122">Kullanılacak bağlama türünü belirten bir dize özniteliği gerekli.</span><span class="sxs-lookup"><span data-stu-id="43f37-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="43f37-123">Türü, başvurulabilmesi için kayıtlı yapılandırma bölümü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43f37-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="43f37-124">Türü kayıtlı bölüm adı yerine bağlama türü adı değil.</span><span class="sxs-lookup"><span data-stu-id="43f37-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="43f37-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="43f37-125">bindingConfiguration</span></span>|<span data-ttu-id="43f37-126">Bitiş noktası başlatıldığında kullanılacak bağlamanın bağlama adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="43f37-127">Bağlama adını, uç nokta tanımlanan bir noktada kapsam içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="43f37-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="43f37-128">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="43f37-129">Bu öznitelik ile birlikte kullanılan `binding` yapılandırma dosyasındaki belirli bağlama yapılandırması başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="43f37-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="43f37-130">Özel bağlama kullanmaya çalışıyorsunuz. Bu özniteliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43f37-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="43f37-131">Aksi takdirde, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="43f37-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="43f37-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="43f37-132">bindingName</span></span>|<span data-ttu-id="43f37-133">WSDL dışa aktarım tanımı için bağlamanın benzersiz nitelenmiş adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="43f37-134">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="43f37-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="43f37-135">bindingNamespace</span></span>|<span data-ttu-id="43f37-136">WSDL dışarı tam tanımı için bağlamanın ad alanı adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="43f37-137">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="43f37-138">Sözleşme</span><span class="sxs-lookup"><span data-stu-id="43f37-138">contract</span></span>|<span data-ttu-id="43f37-139">Hangi anlaşmanın gösteren bir dize bu koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="43f37-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="43f37-140">Derleme sözleşme türünü uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="43f37-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="43f37-141">Bir hizmet uygulaması tek bir anlaşma türü uyguluyorsa, bu özellik atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="43f37-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="43f37-142">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="43f37-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="43f37-143">endpointConfiguration</span></span>|<span data-ttu-id="43f37-144">Tarafından ayarlanan standart bitiş noktası adını belirten bir dize `kind` bu standart bitiş noktası ek yapılandırma bilgilerinie başvuran öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43f37-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="43f37-145">Aynı ada tanımlanmalıdır `<standardEndpoints>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="43f37-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="43f37-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="43f37-146">isSystemEndpoint</span></span>|<span data-ttu-id="43f37-147">Bir uç nokta altyapı uç noktası olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="43f37-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="43f37-148">tür</span><span class="sxs-lookup"><span data-stu-id="43f37-148">kind</span></span>|<span data-ttu-id="43f37-149">Uygulanan standart bitiş noktası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="43f37-150">Türü kayıtlı olmalıdır `<extensions>` bölüm veya machine.config. Hiçbir şey belirtilmezse, ortak bir hizmet uç noktası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="43f37-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="43f37-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="43f37-151">listenUriMode</span></span>|<span data-ttu-id="43f37-152">Taşıma nasıl işler belirtir `ListenUri` hizmetin dinlemesi sağlanan.</span><span class="sxs-lookup"><span data-stu-id="43f37-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="43f37-153">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="43f37-153">Valid values are</span></span><br /><br /> <span data-ttu-id="43f37-154">-Açık</span><span class="sxs-lookup"><span data-stu-id="43f37-154">-   Explicit</span></span><br /><span data-ttu-id="43f37-155">-Benzersiz</span><span class="sxs-lookup"><span data-stu-id="43f37-155">-   Unique</span></span><br /><br /> <span data-ttu-id="43f37-156">Explicit varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="43f37-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="43f37-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="43f37-157">listenUri</span></span>|<span data-ttu-id="43f37-158">Hizmet uç noktasını dinleyen URI belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="43f37-159">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="43f37-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="43f37-160">name</span><span class="sxs-lookup"><span data-stu-id="43f37-160">name</span></span>|<span data-ttu-id="43f37-161">İsteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="43f37-161">Optional attribute.</span></span> <span data-ttu-id="43f37-162">Hizmet uç noktası adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="43f37-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="43f37-163">Bağlama adı ve sözleşme tanımı adı birleşimi varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="43f37-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="43f37-164">Hizmetleri olabilir birden fazla uç nokta, bu nedenle uç noktanın `name` özniteliktir hizmet adından farklı.</span><span class="sxs-lookup"><span data-stu-id="43f37-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43f37-165">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43f37-165">Child Elements</span></span>  
  
|<span data-ttu-id="43f37-166">Öğe</span><span class="sxs-lookup"><span data-stu-id="43f37-166">Element</span></span>|<span data-ttu-id="43f37-167">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43f37-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43f37-168">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="43f37-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="43f37-169">Adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="43f37-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="43f37-170">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="43f37-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="43f37-171">Onunla mesaj alışverişleri diğer uç noktalar tarafından bir uç nokta kimlik doğrulaması sağlayan bir kimlik.</span><span class="sxs-lookup"><span data-stu-id="43f37-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43f37-172">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43f37-172">Parent Elements</span></span>  
  
|<span data-ttu-id="43f37-173">Öğe</span><span class="sxs-lookup"><span data-stu-id="43f37-173">Element</span></span>|<span data-ttu-id="43f37-174">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43f37-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43f37-175">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="43f37-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="43f37-176">Bir istemcinin bağlanabileceği uç noktaları listesi tanımlayan bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="43f37-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43f37-177">Örnek</span><span class="sxs-lookup"><span data-stu-id="43f37-177">Example</span></span>  
 <span data-ttu-id="43f37-178">Bu, bir hizmet uç noktası yapılandırması örneğidir.</span><span class="sxs-lookup"><span data-stu-id="43f37-178">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43f37-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43f37-179">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="43f37-180">Uç noktalar: Adresleri, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="43f37-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="43f37-181">Nasıl yapılır: Yapılandırma içinde hizmet uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="43f37-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
