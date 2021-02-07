---
description: 'Hakkında daha fazla bilgi edinin: <localIssuer>'
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 38928f1bfd7740aa902de46958740a1e8fe63e5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725486"
---
# \<localIssuer>

<span data-ttu-id="5ddd9-102">Bir güvenlik belirteci elde etmek için kullanılacak yerel verenin adresini ve bağlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="5ddd9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ddd9-103">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ddd9-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5ddd9-105">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="5ddd9-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ddd9-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-106">Attributes</span></span>  
  
|<span data-ttu-id="5ddd9-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ddd9-107">Attribute</span></span>|<span data-ttu-id="5ddd9-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddd9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ddd9-109">adres</span><span class="sxs-lookup"><span data-stu-id="5ddd9-109">address</span></span>|<span data-ttu-id="5ddd9-110">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-110">Required string.</span></span> <span data-ttu-id="5ddd9-111">Yerel veren 'in URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-111">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="5ddd9-112">bağlama</span><span class="sxs-lookup"><span data-stu-id="5ddd9-112">binding</span></span>|<span data-ttu-id="5ddd9-113">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-113">Optional string.</span></span> <span data-ttu-id="5ddd9-114">Sistem tarafından belirtilen bağlamalardan biri.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-114">One of the system-provided bindings.</span></span> <span data-ttu-id="5ddd9-115">Bir liste için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="5ddd9-115">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="5ddd9-116">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ddd9-116">bindingConfiguration</span></span>|<span data-ttu-id="5ddd9-117">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-117">Optional string.</span></span> <span data-ttu-id="5ddd9-118">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-118">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ddd9-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-119">Child Elements</span></span>  
  
|<span data-ttu-id="5ddd9-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ddd9-120">Element</span></span>|<span data-ttu-id="5ddd9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddd9-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="5ddd9-122">Yerel veren için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-122">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="5ddd9-123">Yerel sertifikayı vereni doğru bir şekilde ele almak için gerekli olan bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-123">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="5ddd9-124">`add`Bu koleksiyona bir üst bilgi eklemek için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-124">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ddd9-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5ddd9-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ddd9-126">Element</span></span>|<span data-ttu-id="5ddd9-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ddd9-127">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="5ddd9-128">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-128">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ddd9-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ddd9-129">Remarks</span></span>  

 <span data-ttu-id="5ddd9-130">Bir güvenlik belirteci hizmetinden (STS) verilen bir belirteç edinirken, istemci uygulamanın STS ile iletişim kurmak için kullanılacak adresle ve bağlamaya yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-130">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="5ddd9-131"><xref:System.ServiceModel.WSFederationHttpBinding>Güvenlik belirteci hizmeti için BIR URL sağlamadığında veya bir Federasyon bağlamasının veren adresi ya da olduğunda `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` , ISTEMCININ Windows Communication Foundation (WCF) kanalı tarafından belirtilen değerleri kullanır `address` ve `binding` verilen belirteci almak için STS ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-131">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="5ddd9-132">Yerel veren yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5ddd9-132">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ddd9-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ddd9-133">Example</span></span>  

 <span data-ttu-id="5ddd9-134">Aşağıdaki örnek `address` `binding` bir öğesinin, ve özniteliklerini ayarlar `bindingConfiguration` `localIssuer` .</span><span class="sxs-lookup"><span data-stu-id="5ddd9-134">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ddd9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ddd9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="5ddd9-136">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="5ddd9-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5ddd9-137">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ddd9-137">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="5ddd9-138">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="5ddd9-138">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="5ddd9-139">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="5ddd9-139">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5ddd9-140">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="5ddd9-141">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5ddd9-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5ddd9-142">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="5ddd9-142">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5ddd9-143">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ddd9-143">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="5ddd9-144">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="5ddd9-144">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
