---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931735"
---
# <a name="localissuer"></a><span data-ttu-id="49037-101">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="49037-101">\<localIssuer></span></span>
<span data-ttu-id="49037-102">Bir güvenlik belirteci elde etmek için kullanılacak yerel verenin adresini ve bağlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49037-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="49037-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49037-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="49037-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="49037-104">\<behaviors></span></span>  
<span data-ttu-id="49037-105">Endpointdavranışlar bölümü</span><span class="sxs-lookup"><span data-stu-id="49037-105">endpointBehaviors section</span></span>  
<span data-ttu-id="49037-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="49037-106">\<behavior></span></span>  
<span data-ttu-id="49037-107">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="49037-107">\<clientCredentials></span></span>  
<span data-ttu-id="49037-108">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="49037-108">\<issuedToken></span></span>  
<span data-ttu-id="49037-109">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="49037-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49037-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49037-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49037-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49037-111">Attributes and Elements</span></span>  
 <span data-ttu-id="49037-112">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="49037-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49037-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49037-113">Attributes</span></span>  
  
|<span data-ttu-id="49037-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49037-114">Attribute</span></span>|<span data-ttu-id="49037-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49037-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49037-116">adres</span><span class="sxs-lookup"><span data-stu-id="49037-116">address</span></span>|<span data-ttu-id="49037-117">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="49037-117">Required string.</span></span> <span data-ttu-id="49037-118">Yerel veren 'in URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="49037-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="49037-119">bağlama</span><span class="sxs-lookup"><span data-stu-id="49037-119">binding</span></span>|<span data-ttu-id="49037-120">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="49037-120">Optional string.</span></span> <span data-ttu-id="49037-121">Sistem tarafından belirtilen bağlamalardan biri.</span><span class="sxs-lookup"><span data-stu-id="49037-121">One of the system-provided bindings.</span></span> <span data-ttu-id="49037-122">Bir liste için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="49037-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="49037-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="49037-123">bindingConfiguration</span></span>|<span data-ttu-id="49037-124">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="49037-124">Optional string.</span></span> <span data-ttu-id="49037-125">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="49037-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49037-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49037-126">Child Elements</span></span>  
  
|<span data-ttu-id="49037-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="49037-127">Element</span></span>|<span data-ttu-id="49037-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49037-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49037-129">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="49037-129">\<identity></span></span>](identity.md)|<span data-ttu-id="49037-130">Yerel veren için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="49037-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="49037-131">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="49037-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="49037-132">Yerel sertifikayı vereni doğru bir şekilde ele almak için gerekli olan bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="49037-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="49037-133">Bu koleksiyona bir üst `add` bilgi eklemek için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="49037-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49037-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49037-134">Parent Elements</span></span>  
  
|<span data-ttu-id="49037-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="49037-135">Element</span></span>|<span data-ttu-id="49037-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49037-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49037-137">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="49037-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="49037-138">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="49037-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49037-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49037-139">Remarks</span></span>  
 <span data-ttu-id="49037-140">Bir güvenlik belirteci hizmetinden (STS) verilen bir belirteç edinirken, istemci uygulamanın STS ile iletişim kurmak için kullanılacak adresle ve bağlamaya yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="49037-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="49037-141">Güvenlik belirteci hizmeti için bir URL sağlamadığınızda veya bir Federasyon `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` bağlamasının veren adresi veya `null`olduğunda, istemcinin Windows Communication Foundation (WCF) kanalı tarafından belirtilen değerleri kullanır. <xref:System.ServiceModel.WSFederationHttpBinding> `address` ve`binding` verilen belirteci almak için STS ile iletişim kurun.</span><span class="sxs-lookup"><span data-stu-id="49037-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="49037-142">Yerel veren yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="49037-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49037-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="49037-143">Example</span></span>  
 <span data-ttu-id="49037-144">Aşağıdaki örnek bir `address` `bindingConfiguration` `binding` öğesinin,veöznitelikleriniayarlar`localIssuer` .</span><span class="sxs-lookup"><span data-stu-id="49037-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49037-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49037-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="49037-146">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="49037-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="49037-147">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="49037-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="49037-148">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="49037-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="49037-149">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="49037-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="49037-150">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="49037-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="49037-151">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="49037-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="49037-152">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="49037-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="49037-153">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="49037-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="49037-154">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="49037-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
