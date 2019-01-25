---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 893ac2cb0e6c54beae68e2607c31564baafd95fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527555"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="3aadd-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="3aadd-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="3aadd-103">Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlamasını ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aadd-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="3aadd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3aadd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3aadd-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="3aadd-105">\<behaviors></span></span>  
<span data-ttu-id="3aadd-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="3aadd-106">endpointBehaviors section</span></span>  
<span data-ttu-id="3aadd-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="3aadd-107">\<behavior></span></span>  
<span data-ttu-id="3aadd-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="3aadd-108">\<clientCredentials></span></span>  
<span data-ttu-id="3aadd-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="3aadd-109">\<issuedToken></span></span>  
<span data-ttu-id="3aadd-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="3aadd-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aadd-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3aadd-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3aadd-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aadd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3aadd-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3aadd-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3aadd-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3aadd-114">Attributes</span></span>  
  
|<span data-ttu-id="3aadd-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3aadd-115">Attribute</span></span>|<span data-ttu-id="3aadd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aadd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3aadd-117">adres</span><span class="sxs-lookup"><span data-stu-id="3aadd-117">address</span></span>|<span data-ttu-id="3aadd-118">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="3aadd-118">Required string.</span></span> <span data-ttu-id="3aadd-119">Yerel dağıtımcının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aadd-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="3aadd-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="3aadd-120">binding</span></span>|<span data-ttu-id="3aadd-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="3aadd-121">Optional string.</span></span> <span data-ttu-id="3aadd-122">Sistem tarafından sağlanan bağlamalar biri.</span><span class="sxs-lookup"><span data-stu-id="3aadd-122">One of the system-provided bindings.</span></span> <span data-ttu-id="3aadd-123">Bir liste için bkz. [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3aadd-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="3aadd-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="3aadd-124">bindingConfiguration</span></span>|<span data-ttu-id="3aadd-125">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="3aadd-125">Optional string.</span></span> <span data-ttu-id="3aadd-126">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aadd-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3aadd-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aadd-127">Child Elements</span></span>  
  
|<span data-ttu-id="3aadd-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aadd-128">Element</span></span>|<span data-ttu-id="3aadd-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aadd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aadd-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="3aadd-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="3aadd-131">Yerel verici kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aadd-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="3aadd-132">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="3aadd-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="3aadd-133">Yerel verici doğru bir şekilde çözmek için gerekli adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="3aadd-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="3aadd-134">Kullanabileceğiniz `add` anahtar sözcüğü, bir üst bilgisi bu koleksiyona eklenecek.</span><span class="sxs-lookup"><span data-stu-id="3aadd-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3aadd-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3aadd-135">Parent Elements</span></span>  
  
|<span data-ttu-id="3aadd-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="3aadd-136">Element</span></span>|<span data-ttu-id="3aadd-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3aadd-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aadd-138">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="3aadd-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="3aadd-139">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3aadd-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aadd-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3aadd-140">Remarks</span></span>  
 <span data-ttu-id="3aadd-141">Verilen bir belirteç bir güvenlik belirteci hizmeti (STS) öğesinden alırken, istemci uygulaması yapılandırılmalıdır adresi ve bir STS ile iletişim kurmak için kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="3aadd-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="3aadd-142">Zaman <xref:System.ServiceModel.WSFederationHttpBinding> URL veya güvenlik belirteci hizmeti için bir federe bağlama veren adresini olduğunda sağlamaz `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`, istemcinin Windows Communication Foundation (WCF) kanal tarafındanbelirtilendeğerlerikullanan`address`ve `binding` verilen belirteç almak için bir STS ile iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="3aadd-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="3aadd-143">Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="3aadd-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aadd-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="3aadd-144">Example</span></span>  
 <span data-ttu-id="3aadd-145">Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerinin bir `localIssuer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3aadd-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3aadd-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aadd-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="3aadd-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="3aadd-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3aadd-148">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3aadd-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="3aadd-149">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="3aadd-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3aadd-150">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="3aadd-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3aadd-151">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="3aadd-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3aadd-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3aadd-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3aadd-153">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="3aadd-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="3aadd-154">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="3aadd-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="3aadd-155">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="3aadd-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
