---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 7a48cbb3a1e17ac1fc9fa9f43301ef153cdb866c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151889"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="be4e1-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="be4e1-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="be4e1-103">Bir güvenlik belirteci almak için kullanılacak yerel verenin bağlamasını ve adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be4e1-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="be4e1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be4e1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be4e1-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="be4e1-105">\<behaviors></span></span>  
<span data-ttu-id="be4e1-106">endpointBehaviors bölümü</span><span class="sxs-lookup"><span data-stu-id="be4e1-106">endpointBehaviors section</span></span>  
<span data-ttu-id="be4e1-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="be4e1-107">\<behavior></span></span>  
<span data-ttu-id="be4e1-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="be4e1-108">\<clientCredentials></span></span>  
<span data-ttu-id="be4e1-109">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="be4e1-109">\<issuedToken></span></span>  
<span data-ttu-id="be4e1-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="be4e1-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4e1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be4e1-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be4e1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="be4e1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="be4e1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be4e1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be4e1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="be4e1-114">Attributes</span></span>  
  
|<span data-ttu-id="be4e1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="be4e1-115">Attribute</span></span>|<span data-ttu-id="be4e1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be4e1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be4e1-117">adres</span><span class="sxs-lookup"><span data-stu-id="be4e1-117">address</span></span>|<span data-ttu-id="be4e1-118">Zorunlu dize.</span><span class="sxs-lookup"><span data-stu-id="be4e1-118">Required string.</span></span> <span data-ttu-id="be4e1-119">Yerel dağıtımcının URI belirtir.</span><span class="sxs-lookup"><span data-stu-id="be4e1-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="be4e1-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="be4e1-120">binding</span></span>|<span data-ttu-id="be4e1-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="be4e1-121">Optional string.</span></span> <span data-ttu-id="be4e1-122">Sistem tarafından sağlanan bağlamalar biri.</span><span class="sxs-lookup"><span data-stu-id="be4e1-122">One of the system-provided bindings.</span></span> <span data-ttu-id="be4e1-123">Bir liste için bkz. [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="be4e1-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="be4e1-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="be4e1-124">bindingConfiguration</span></span>|<span data-ttu-id="be4e1-125">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="be4e1-125">Optional string.</span></span> <span data-ttu-id="be4e1-126">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be4e1-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be4e1-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="be4e1-127">Child Elements</span></span>  
  
|<span data-ttu-id="be4e1-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="be4e1-128">Element</span></span>|<span data-ttu-id="be4e1-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be4e1-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be4e1-130">\<Kimliği ></span><span class="sxs-lookup"><span data-stu-id="be4e1-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="be4e1-131">Yerel verici kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be4e1-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="be4e1-132">\<üstbilgiler ></span><span class="sxs-lookup"><span data-stu-id="be4e1-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="be4e1-133">Yerel verici doğru bir şekilde çözmek için gerekli adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="be4e1-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="be4e1-134">Kullanabileceğiniz `add` anahtar sözcüğü, bir üst bilgisi bu koleksiyona eklenecek.</span><span class="sxs-lookup"><span data-stu-id="be4e1-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be4e1-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="be4e1-135">Parent Elements</span></span>  
  
|<span data-ttu-id="be4e1-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="be4e1-136">Element</span></span>|<span data-ttu-id="be4e1-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be4e1-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be4e1-138">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="be4e1-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="be4e1-139">Bir hizmete istemcinin kimliğini doğrulamak için kullanılan özel simgeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="be4e1-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be4e1-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be4e1-140">Remarks</span></span>  
 <span data-ttu-id="be4e1-141">Verilen bir belirteç bir güvenlik belirteci hizmeti (STS) öğesinden alırken, istemci uygulaması yapılandırılmalıdır adresi ve bir STS ile iletişim kurmak için kullanılacak bağlama.</span><span class="sxs-lookup"><span data-stu-id="be4e1-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="be4e1-142">Zaman <xref:System.ServiceModel.WSFederationHttpBinding> URL veya güvenlik belirteci hizmeti için bir federe bağlama veren adresini olduğunda sağlamaz `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` veya `null`, istemcinin Windows Communication Foundation (WCF) kanal tarafındanbelirtilendeğerlerikullanan`address`ve `binding` verilen belirteç almak için bir STS ile iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="be4e1-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="be4e1-143">Yerel yayımlayan yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="be4e1-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be4e1-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="be4e1-144">Example</span></span>  
 <span data-ttu-id="be4e1-145">Aşağıdaki örnek kümeleri `address`, `binding`, ve `bindingConfiguration` özniteliklerinin bir `localIssuer` öğesi.</span><span class="sxs-lookup"><span data-stu-id="be4e1-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="be4e1-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be4e1-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="be4e1-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="be4e1-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="be4e1-148">Nasıl yapılır: Yerel yayımlayan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="be4e1-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="be4e1-149">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="be4e1-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="be4e1-150">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="be4e1-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="be4e1-151">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="be4e1-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="be4e1-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="be4e1-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="be4e1-153">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="be4e1-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="be4e1-154">Nasıl yapılır: Federe istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="be4e1-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="be4e1-155">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="be4e1-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
