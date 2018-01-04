---
title: "&lt;İssuermetadata&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bac725e0c4fe590623ac82ec45bcf669a2e57179
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="9a5d3-102">&lt;İssuermetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="9a5d3-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="9a5d3-103">Bir federe güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="9a5d3-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9a5d3-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-105">\<bindings></span></span>  
<span data-ttu-id="9a5d3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-106">\<customBinding></span></span>  
<span data-ttu-id="9a5d3-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-107">\<binding></span></span>  
<span data-ttu-id="9a5d3-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-108">\<security></span></span>  
<span data-ttu-id="9a5d3-109">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a5d3-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a5d3-110">Syntax</span></span>  
  
```xml  
<issuedTokenParameters   
      DefaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"  
      inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"  
      keySize="Integer"  
   keyType="AsymmetricKey/BearerKey/SymmetricKey"  
      tokenType="String" >  
   <additionalRequestParameters />  
      <claimTypeRequirements>  
            <add claimType="URI"  
           isOptional="Boolean" />  
      </claimTypeRequirements>  
      <issuer address="String"   
                      binding=" " />  
      <issuerMetadata address="String" />   
</issuedTokenParameters>  
```  
  
## <a name="type"></a><span data-ttu-id="9a5d3-111">Tür</span><span class="sxs-lookup"><span data-stu-id="9a5d3-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a5d3-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9a5d3-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a5d3-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-114">Attributes</span></span>  
  
|<span data-ttu-id="9a5d3-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9a5d3-115">Attribute</span></span>|<span data-ttu-id="9a5d3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5d3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a5d3-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="9a5d3-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="9a5d3-118">Güvenlik belirtimleri sürümlerinin belirtir (WS-Security, WS-Trust, WS-güvenli konuşma ve WS-Güvenlik İlkesi), gerekir desteklenir bağlama tarafından.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="9a5d3-119">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="9a5d3-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="9a5d3-120">inclusionMode</span></span>|<span data-ttu-id="9a5d3-121">Belirteç ekleme gereksinimleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="9a5d3-122">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="9a5d3-123">Anahtar boyutu</span><span class="sxs-lookup"><span data-stu-id="9a5d3-123">keySize</span></span>|<span data-ttu-id="9a5d3-124">Belirteç anahtar boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="9a5d3-125">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-125">The default value is 256.</span></span>|  
|<span data-ttu-id="9a5d3-126">keyType</span><span class="sxs-lookup"><span data-stu-id="9a5d3-126">keyType</span></span>|<span data-ttu-id="9a5d3-127">Geçerli bir değeri <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="9a5d3-128">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="9a5d3-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="9a5d3-129">tokenType</span></span>|<span data-ttu-id="9a5d3-130">Belirteç türü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-130">A string that specifies the token type.</span></span> <span data-ttu-id="9a5d3-131">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML" dir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a5d3-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-132">Child Elements</span></span>  
  
|<span data-ttu-id="9a5d3-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a5d3-133">Element</span></span>|<span data-ttu-id="9a5d3-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5d3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a5d3-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="9a5d3-136">Ek istek parametrelerini belirtin yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="9a5d3-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="9a5d3-138">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="9a5d3-139">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="9a5d3-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="9a5d3-141">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="9a5d3-142">\<veren ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="9a5d3-143">Uç nokta belirtir bir yapılandırma öğesi, geçerli belirteci yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="9a5d3-144">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="9a5d3-145">Belirteç Verenin meta veri uç noktası adresi belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a5d3-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-146">Parent Elements</span></span>  
  
|<span data-ttu-id="9a5d3-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="9a5d3-147">Element</span></span>|<span data-ttu-id="9a5d3-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a5d3-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a5d3-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="9a5d3-150">Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="9a5d3-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="9a5d3-152">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a5d3-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a5d3-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9a5d3-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9a5d3-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9a5d3-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="9a5d3-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9a5d3-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9a5d3-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9a5d3-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9a5d3-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="9a5d3-158">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a5d3-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="9a5d3-159">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="9a5d3-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="9a5d3-160">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="9a5d3-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9a5d3-161">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9a5d3-162">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="9a5d3-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="9a5d3-163">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="9a5d3-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
