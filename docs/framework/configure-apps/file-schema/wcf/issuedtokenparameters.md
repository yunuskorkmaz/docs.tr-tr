---
title: '&lt;İssuermetadata&gt;'
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: 550b3412b193b996b8de800856d6833369fc4bc7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749393"
---
# <a name="ltissuedtokenparametersgt"></a><span data-ttu-id="a18d9-102">&lt;İssuermetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="a18d9-102">&lt;issuedTokenParameters&gt;</span></span>
<span data-ttu-id="a18d9-103">Bir federe güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-103">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
 <span data-ttu-id="a18d9-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a18d9-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a18d9-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="a18d9-105">\<bindings></span></span>  
<span data-ttu-id="a18d9-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a18d9-106">\<customBinding></span></span>  
<span data-ttu-id="a18d9-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="a18d9-107">\<binding></span></span>  
<span data-ttu-id="a18d9-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a18d9-108">\<security></span></span>  
<span data-ttu-id="a18d9-109">\<İssuermetadata ></span><span class="sxs-lookup"><span data-stu-id="a18d9-109">\<issuedTokenParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18d9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a18d9-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="a18d9-111">Tür</span><span class="sxs-lookup"><span data-stu-id="a18d9-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a18d9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a18d9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a18d9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a18d9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a18d9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a18d9-114">Attributes</span></span>  
  
|<span data-ttu-id="a18d9-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a18d9-115">Attribute</span></span>|<span data-ttu-id="a18d9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a18d9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a18d9-117">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="a18d9-117">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="a18d9-118">Güvenlik belirtimleri sürümlerinin belirtir (WS-Security, WS-Trust, WS-güvenli konuşma ve WS-Güvenlik İlkesi), gerekir desteklenir bağlama tarafından.</span><span class="sxs-lookup"><span data-stu-id="a18d9-118">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="a18d9-119">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="a18d9-119">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="a18d9-120">inclusionMode</span><span class="sxs-lookup"><span data-stu-id="a18d9-120">inclusionMode</span></span>|<span data-ttu-id="a18d9-121">Belirteç ekleme gereksinimleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-121">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="a18d9-122">Bu öznitelik türünde <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span><span class="sxs-lookup"><span data-stu-id="a18d9-122">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="a18d9-123">Anahtar boyutu</span><span class="sxs-lookup"><span data-stu-id="a18d9-123">keySize</span></span>|<span data-ttu-id="a18d9-124">Belirteç anahtar boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="a18d9-124">An integer that specifies the token key size.</span></span> <span data-ttu-id="a18d9-125">Varsayılan değer 256'dır.</span><span class="sxs-lookup"><span data-stu-id="a18d9-125">The default value is 256.</span></span>|  
|<span data-ttu-id="a18d9-126">keyType</span><span class="sxs-lookup"><span data-stu-id="a18d9-126">keyType</span></span>|<span data-ttu-id="a18d9-127">Geçerli bir değeri <xref:System.IdentityModel.Tokens.SecurityKeyType> anahtar türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-127">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="a18d9-128">Varsayılan, `SymmetricKey` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-128">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="a18d9-129">tokenType</span><span class="sxs-lookup"><span data-stu-id="a18d9-129">tokenType</span></span>|<span data-ttu-id="a18d9-130">Belirteç türü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a18d9-130">A string that specifies the token type.</span></span> <span data-ttu-id="a18d9-131">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="a18d9-131">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a18d9-132">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a18d9-132">Child Elements</span></span>  
  
|<span data-ttu-id="a18d9-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="a18d9-133">Element</span></span>|<span data-ttu-id="a18d9-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a18d9-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a18d9-135">\<additionalRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a18d9-135">\<additionalRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/additionalrequestparameters-element.md)|<span data-ttu-id="a18d9-136">Ek istek parametrelerini belirtin yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a18d9-136">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[<span data-ttu-id="a18d9-137">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="a18d9-137">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="a18d9-138">Gerekli talep türleri koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-138">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="a18d9-139">Federe senaryolarda hizmetleri gelen kimlik bilgilerini gereksinimleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="a18d9-139">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="a18d9-140">Örneğin, gelen kimlik bilgileri, belirli bir talep türleri kümesini sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-140">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="a18d9-141">Bu koleksiyondaki her öğe bir federe kimlik bilgisi görünmesi beklenen gerekli ve isteğe bağlı talep türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-141">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[<span data-ttu-id="a18d9-142">\<veren ></span><span class="sxs-lookup"><span data-stu-id="a18d9-142">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer-of-issuedtokenparameters.md)|<span data-ttu-id="a18d9-143">Uç nokta belirtir bir yapılandırma öğesi, geçerli belirteci yayımlar.</span><span class="sxs-lookup"><span data-stu-id="a18d9-143">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[<span data-ttu-id="a18d9-144">\<İssuedtokenparameters ></span><span class="sxs-lookup"><span data-stu-id="a18d9-144">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="a18d9-145">Belirteç Verenin meta veri uç noktası adresi belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a18d9-145">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a18d9-146">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a18d9-146">Parent Elements</span></span>  
  
|<span data-ttu-id="a18d9-147">Öğe</span><span class="sxs-lookup"><span data-stu-id="a18d9-147">Element</span></span>|<span data-ttu-id="a18d9-148">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a18d9-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a18d9-149">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="a18d9-149">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="a18d9-150">Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-150">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[<span data-ttu-id="a18d9-151">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="a18d9-151">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="a18d9-152">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a18d9-152">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a18d9-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a18d9-153">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a18d9-154">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a18d9-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a18d9-155">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a18d9-155">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a18d9-156">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="a18d9-156">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a18d9-157">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a18d9-157">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a18d9-158">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a18d9-158">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="a18d9-159">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="a18d9-159">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)  
 [<span data-ttu-id="a18d9-160">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="a18d9-160">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a18d9-161">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a18d9-161">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a18d9-162">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a18d9-162">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a18d9-163">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="a18d9-163">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
