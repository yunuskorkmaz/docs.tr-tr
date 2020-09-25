---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: e08d2c0b42cfd8e302223915f0256f8cb2d1468b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204963"
---
# \<localIssuer>

<span data-ttu-id="ec42a-101">Bir güvenlik belirteci elde etmek için kullanılacak yerel verenin adresini ve bağlamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-101">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localIssuer>**  
  
## <a name="syntax"></a><span data-ttu-id="ec42a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ec42a-102">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec42a-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec42a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ec42a-104">Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır</span><span class="sxs-lookup"><span data-stu-id="ec42a-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec42a-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec42a-105">Attributes</span></span>  
  
|<span data-ttu-id="ec42a-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ec42a-106">Attribute</span></span>|<span data-ttu-id="ec42a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec42a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec42a-108">adres</span><span class="sxs-lookup"><span data-stu-id="ec42a-108">address</span></span>|<span data-ttu-id="ec42a-109">Gerekli dize.</span><span class="sxs-lookup"><span data-stu-id="ec42a-109">Required string.</span></span> <span data-ttu-id="ec42a-110">Yerel veren 'in URI 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-110">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="ec42a-111">bağlama</span><span class="sxs-lookup"><span data-stu-id="ec42a-111">binding</span></span>|<span data-ttu-id="ec42a-112">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="ec42a-112">Optional string.</span></span> <span data-ttu-id="ec42a-113">Sistem tarafından belirtilen bağlamalardan biri.</span><span class="sxs-lookup"><span data-stu-id="ec42a-113">One of the system-provided bindings.</span></span> <span data-ttu-id="ec42a-114">Bir liste için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ec42a-114">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="ec42a-115">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ec42a-115">bindingConfiguration</span></span>|<span data-ttu-id="ec42a-116">İsteğe bağlı dize.</span><span class="sxs-lookup"><span data-stu-id="ec42a-116">Optional string.</span></span> <span data-ttu-id="ec42a-117">Yapılandırma dosyasında bulunan bir bağlama yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-117">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec42a-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec42a-118">Child Elements</span></span>  
  
|<span data-ttu-id="ec42a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec42a-119">Element</span></span>|<span data-ttu-id="ec42a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec42a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="ec42a-121">Yerel veren için kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-121">Specifies identity information for the local issuer.</span></span>|  
|[\<headers>](headers-element.md)|<span data-ttu-id="ec42a-122">Yerel sertifikayı vereni doğru bir şekilde ele almak için gerekli olan bir adres üst bilgileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ec42a-122">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="ec42a-123">`add`Bu koleksiyona bir üst bilgi eklemek için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec42a-123">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec42a-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec42a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ec42a-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec42a-125">Element</span></span>|<span data-ttu-id="ec42a-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec42a-126">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="ec42a-127">Bir hizmette istemcinin kimliğini doğrulamak için kullanılan özel bir belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-127">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec42a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ec42a-128">Remarks</span></span>  

 <span data-ttu-id="ec42a-129">Bir güvenlik belirteci hizmetinden (STS) verilen bir belirteç edinirken, istemci uygulamanın STS ile iletişim kurmak için kullanılacak adresle ve bağlamaya yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec42a-129">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="ec42a-130"><xref:System.ServiceModel.WSFederationHttpBinding>Güvenlik belirteci hizmeti için BIR URL sağlamadığında veya bir Federasyon bağlamasının veren adresi ya da olduğunda `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` , ISTEMCININ Windows Communication Foundation (WCF) kanalı tarafından belirtilen değerleri kullanır `address` ve `binding` verilen belirteci almak için STS ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ec42a-130">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="ec42a-131">Yerel veren yapılandırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="ec42a-131">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec42a-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec42a-132">Example</span></span>  

 <span data-ttu-id="ec42a-133">Aşağıdaki örnek `address` `binding` bir öğesinin, ve özniteliklerini ayarlar `bindingConfiguration` `localIssuer` .</span><span class="sxs-lookup"><span data-stu-id="ec42a-133">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec42a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec42a-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="ec42a-135">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="ec42a-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ec42a-136">Nasıl yapılır: Yerel Yayımlayan Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec42a-136">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="ec42a-137">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="ec42a-137">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ec42a-138">Güvenlik Davranışları</span><span class="sxs-lookup"><span data-stu-id="ec42a-138">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="ec42a-139">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ec42a-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="ec42a-140">Hizmet ve İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ec42a-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ec42a-141">İstemcileri Güvenli Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="ec42a-141">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="ec42a-142">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec42a-142">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="ec42a-143">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="ec42a-143">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
