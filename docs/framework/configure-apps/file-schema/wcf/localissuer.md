---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9a51387cd75d57a6828ecde1dcd788b056f7e27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122882"
---
# <a name="localissuer"></a><span data-ttu-id="d46ff-101">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="d46ff-101">\<localIssuer></span></span>
<span data-ttu-id="d46ff-102">Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlamasını ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ff-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="d46ff-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d46ff-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d46ff-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d46ff-104">\<behaviors></span></span>  
<span data-ttu-id="d46ff-105">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="d46ff-105">endpointBehaviors section</span></span>  
<span data-ttu-id="d46ff-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d46ff-106">\<behavior></span></span>  
<span data-ttu-id="d46ff-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d46ff-107">\<clientCredentials></span></span>  
<span data-ttu-id="d46ff-108">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="d46ff-108">\<issuedToken></span></span>  
<span data-ttu-id="d46ff-109">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="d46ff-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d46ff-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d46ff-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d46ff-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d46ff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d46ff-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d46ff-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d46ff-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d46ff-113">Attributes</span></span>  
  
|<span data-ttu-id="d46ff-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d46ff-114">Attribute</span></span>|<span data-ttu-id="d46ff-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d46ff-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d46ff-116">adres</span><span class="sxs-lookup"><span data-stu-id="d46ff-116">address</span></span>|<span data-ttu-id="d46ff-117">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="d46ff-117">Required string.</span></span> <span data-ttu-id="d46ff-118">Yerel dağıtımcının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ff-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="d46ff-119">bağlama</span><span class="sxs-lookup"><span data-stu-id="d46ff-119">binding</span></span>|<span data-ttu-id="d46ff-120">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="d46ff-120">Optional string.</span></span> <span data-ttu-id="d46ff-121">Sistem tarafından sağlanan bağlamalar biri.</span><span class="sxs-lookup"><span data-stu-id="d46ff-121">One of the system-provided bindings.</span></span> <span data-ttu-id="d46ff-122">Bir liste için bkz. [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="d46ff-122">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="d46ff-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="d46ff-123">bindingConfiguration</span></span>|<span data-ttu-id="d46ff-124">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="d46ff-124">Optional string.</span></span> <span data-ttu-id="d46ff-125">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ff-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d46ff-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d46ff-126">Child Elements</span></span>  
  
|<span data-ttu-id="d46ff-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="d46ff-127">Element</span></span>|<span data-ttu-id="d46ff-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d46ff-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d46ff-129">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="d46ff-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d46ff-130">Yerel verici kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ff-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="d46ff-131">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="d46ff-131">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d46ff-132">Yerel verici doğru bir şekilde çözmek için gerekli adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d46ff-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="d46ff-133">Kullanabileceğiniz `add` anahtar sözcüğü, bir üst bilgisi bu koleksiyona eklenecek.</span><span class="sxs-lookup"><span data-stu-id="d46ff-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d46ff-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d46ff-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d46ff-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="d46ff-135">Element</span></span>|<span data-ttu-id="d46ff-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d46ff-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d46ff-137">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="d46ff-137">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="d46ff-138">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d46ff-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d46ff-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d46ff-139">Remarks</span></span>  
 <span data-ttu-id="d46ff-140">Verilen bir belirteç bir güvenlik belirteci hizmeti (STS) öğesinden alırken, istemci uygulaması yapılandırılmalıdır adresi ve bir STS ile iletişim kurmak için kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="d46ff-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="d46ff-141">Zaman <xref:System.ServiceModel.WSFederationHttpBinding> URL veya güvenlik belirteci hizmeti için bir federe bağlama veren adresini olduğunda sağlamaz `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`, istemcinin Windows Communication Foundation (WCF) kanal tarafındanbelirtilendeğerlerikullanan`address`ve `binding` verilen belirteç almak için bir STS ile iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="d46ff-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="d46ff-142">Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="d46ff-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d46ff-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="d46ff-143">Example</span></span>  
 <span data-ttu-id="d46ff-144">Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerinin bir `localIssuer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d46ff-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="d46ff-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d46ff-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="d46ff-146">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="d46ff-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d46ff-147">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d46ff-147">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d46ff-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="d46ff-148">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d46ff-149">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="d46ff-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d46ff-150">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d46ff-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d46ff-151">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d46ff-151">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d46ff-152">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d46ff-152">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="d46ff-153">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="d46ff-153">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d46ff-154">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="d46ff-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
