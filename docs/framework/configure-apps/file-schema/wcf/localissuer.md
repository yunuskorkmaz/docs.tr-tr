---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 055b7b49d1f775d49ac20de18c18ca0433716a23
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397857"
---
# <a name="localissuer"></a><span data-ttu-id="36ee8-101">\<LocalIssuer ></span><span class="sxs-lookup"><span data-stu-id="36ee8-101">\<localIssuer></span></span>
<span data-ttu-id="36ee8-102">Bir güvenlik belirteci elde etmek için kullanılacak yerel verenin adresini ve bağlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
<span data-ttu-id="36ee8-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="36ee8-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="36ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="36ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="36ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="36ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="36ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="36ee8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="36ee8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<LocalIssuer >**</span><span class="sxs-lookup"><span data-stu-id="36ee8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ee8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36ee8-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36ee8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ee8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="36ee8-113">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="36ee8-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36ee8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="36ee8-114">Attributes</span></span>  
  
|<span data-ttu-id="36ee8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="36ee8-115">Attribute</span></span>|<span data-ttu-id="36ee8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ee8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36ee8-117">adres</span><span class="sxs-lookup"><span data-stu-id="36ee8-117">address</span></span>|<span data-ttu-id="36ee8-118">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="36ee8-118">Required string.</span></span> <span data-ttu-id="36ee8-119">Yerel veren 'in URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="36ee8-120">bağlama</span><span class="sxs-lookup"><span data-stu-id="36ee8-120">binding</span></span>|<span data-ttu-id="36ee8-121">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="36ee8-121">Optional string.</span></span> <span data-ttu-id="36ee8-122">Sistem tarafından belirtilen bağlamalardan biri.</span><span class="sxs-lookup"><span data-stu-id="36ee8-122">One of the system-provided bindings.</span></span> <span data-ttu-id="36ee8-123">Bir liste için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="36ee8-123">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="36ee8-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="36ee8-124">bindingConfiguration</span></span>|<span data-ttu-id="36ee8-125">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="36ee8-125">Optional string.</span></span> <span data-ttu-id="36ee8-126">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36ee8-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ee8-127">Child Elements</span></span>  
  
|<span data-ttu-id="36ee8-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ee8-128">Element</span></span>|<span data-ttu-id="36ee8-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ee8-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36ee8-130">\<kimlik ></span><span class="sxs-lookup"><span data-stu-id="36ee8-130">\<identity></span></span>](identity.md)|<span data-ttu-id="36ee8-131">Yerel veren için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="36ee8-132">\<üst bilgiler ></span><span class="sxs-lookup"><span data-stu-id="36ee8-132">\<headers></span></span>](headers-element.md)|<span data-ttu-id="36ee8-133">Yerel sertifikayı vereni doğru bir şekilde ele almak için gerekli olan bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="36ee8-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="36ee8-134">Bu koleksiyona bir üst `add` bilgi eklemek için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36ee8-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="36ee8-135">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="36ee8-135">Parent Elements</span></span>  
  
|<span data-ttu-id="36ee8-136">Öğe</span><span class="sxs-lookup"><span data-stu-id="36ee8-136">Element</span></span>|<span data-ttu-id="36ee8-137">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36ee8-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36ee8-138">\<IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="36ee8-138">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="36ee8-139">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36ee8-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36ee8-140">Remarks</span></span>  
 <span data-ttu-id="36ee8-141">Bir güvenlik belirteci hizmetinden (STS) verilen bir belirteç edinirken, istemci uygulamanın STS ile iletişim kurmak için kullanılacak adresle ve bağlamaya yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36ee8-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="36ee8-142">Güvenlik belirteci hizmeti için bir URL sağlamadığınızda veya bir Federasyon `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` bağlamasının veren adresi veya `null`olduğunda, istemcinin Windows Communication Foundation (WCF) kanalı tarafından belirtilen değerleri kullanır. <xref:System.ServiceModel.WSFederationHttpBinding> `address` ve`binding` verilen belirteci almak için STS ile iletişim kurun.</span><span class="sxs-lookup"><span data-stu-id="36ee8-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="36ee8-143">Yerel veren yapılandırma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yerel bir veren](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="36ee8-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36ee8-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="36ee8-144">Example</span></span>  
 <span data-ttu-id="36ee8-145">Aşağıdaki örnek bir `address` `bindingConfiguration` `binding` öğesinin,veöznitelikleriniayarlar`localIssuer` .</span><span class="sxs-lookup"><span data-stu-id="36ee8-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36ee8-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36ee8-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="36ee8-147">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="36ee8-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="36ee8-148">Nasıl yapılır: Yerel veren yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36ee8-148">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="36ee8-149">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="36ee8-149">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="36ee8-150">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="36ee8-150">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="36ee8-151">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="36ee8-151">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="36ee8-152">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="36ee8-152">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="36ee8-153">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="36ee8-153">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="36ee8-154">Nasıl yapılır: Federe Istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="36ee8-154">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="36ee8-155">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="36ee8-155">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
