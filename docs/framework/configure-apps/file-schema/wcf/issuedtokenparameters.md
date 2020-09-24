---
title: <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: 120b3f37-7331-4816-b712-d6aab39655a4
ms.openlocfilehash: c90024a0629f39d160967ca00434e48f682d8933
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157323"
---
# \<issuedTokenParameters>

<span data-ttu-id="c90ef-101">Federasyon güvenlik senaryosunda verilen bir güvenlik belirteci için parametreleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-101">Specifies the parameters for a security token issued in a Federated security scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="c90ef-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="c90ef-102">Syntax</span></span>  
  
```xml  
<issuedTokenParameters defaultMessageSecurityVersion="System.ServiceModel.MessageSecurityVersion"
                       inclusionMode="AlwaysToInitiator/AlwaysToRecipient/Never/Once"
                       keySize="Integer"
                       keyType="AsymmetricKey/BearerKey/SymmetricKey"
                       tokenType="String">
  <additionalRequestParameters />
  <claimTypeRequirements>
    <add claimType="URI"
         isOptional="Boolean" />
  </claimTypeRequirements>
  <issuer address="String"
          binding="" />
  <issuerMetadata address="String" />
</issuedTokenParameters>
```  
  
## <a name="type"></a><span data-ttu-id="c90ef-103">Tür</span><span class="sxs-lookup"><span data-stu-id="c90ef-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c90ef-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c90ef-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c90ef-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c90ef-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c90ef-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c90ef-106">Attributes</span></span>  
  
|<span data-ttu-id="c90ef-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c90ef-107">Attribute</span></span>|<span data-ttu-id="c90ef-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c90ef-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c90ef-109">defaultMessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="c90ef-109">defaultMessageSecurityVersion</span></span>|<span data-ttu-id="c90ef-110">Bağlama tarafından desteklenmesi gereken güvenlik belirtimleri sürümlerini (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-110">Specifies the versions of the security specifications, (WS-Security, WS-Trust, WS-Secure Conversation and WS-Security Policy) that must be supported by the binding.</span></span> <span data-ttu-id="c90ef-111">Bu değer türünde <xref:System.ServiceModel.MessageSecurityVersion>.</span><span class="sxs-lookup"><span data-stu-id="c90ef-111">This value is of type <xref:System.ServiceModel.MessageSecurityVersion>.</span></span>|  
|<span data-ttu-id="c90ef-112">Yani ıonmode</span><span class="sxs-lookup"><span data-stu-id="c90ef-112">inclusionMode</span></span>|<span data-ttu-id="c90ef-113">Belirteç ekleme gereksinimlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-113">Specifies the token inclusion requirements.</span></span> <span data-ttu-id="c90ef-114">Bu öznitelik türü <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> .</span><span class="sxs-lookup"><span data-stu-id="c90ef-114">This attribute is of type <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>.</span></span>|  
|<span data-ttu-id="c90ef-115">keySize</span><span class="sxs-lookup"><span data-stu-id="c90ef-115">keySize</span></span>|<span data-ttu-id="c90ef-116">Belirteç anahtar boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c90ef-116">An integer that specifies the token key size.</span></span> <span data-ttu-id="c90ef-117">Varsayılan değer 256 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-117">The default value is 256.</span></span>|  
|<span data-ttu-id="c90ef-118">Anahtar</span><span class="sxs-lookup"><span data-stu-id="c90ef-118">keyType</span></span>|<span data-ttu-id="c90ef-119"><xref:System.IdentityModel.Tokens.SecurityKeyType>Anahtar türünü belirten geçerli bir değeri.</span><span class="sxs-lookup"><span data-stu-id="c90ef-119">A valid value of <xref:System.IdentityModel.Tokens.SecurityKeyType> that specifies the key type.</span></span> <span data-ttu-id="c90ef-120">Varsayılan değer: `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="c90ef-120">The default is `SymmetricKey`.</span></span>|  
|<span data-ttu-id="c90ef-121">Belirteç</span><span class="sxs-lookup"><span data-stu-id="c90ef-121">tokenType</span></span>|<span data-ttu-id="c90ef-122">Belirteç türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="c90ef-122">A string that specifies the token type.</span></span> <span data-ttu-id="c90ef-123">Varsayılan değer "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span><span class="sxs-lookup"><span data-stu-id="c90ef-123">The default is "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAML".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c90ef-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c90ef-124">Child Elements</span></span>  
  
|<span data-ttu-id="c90ef-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c90ef-125">Element</span></span>|<span data-ttu-id="c90ef-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c90ef-126">Description</span></span>|  
|-------------|-----------------|  
|[\<additionalRequestParameters>](additionalrequestparameters-element.md)|<span data-ttu-id="c90ef-127">Ek istek parametrelerini belirten yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c90ef-127">A collection of configuration elements that specify additional request parameters.</span></span>|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="c90ef-128">Gerekli talep türlerinin koleksiyonunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-128">Specifies a collection of required claim types.</span></span><br /><br /> <span data-ttu-id="c90ef-129">Federasyon senaryosunda, hizmetler gelen kimlik bilgileri için gereksinimleri durum olarak alır.</span><span class="sxs-lookup"><span data-stu-id="c90ef-129">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="c90ef-130">Örneğin, gelen kimlik bilgileri belirli bir talep türü kümesine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c90ef-130">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="c90ef-131">Bu koleksiyondaki her öğe, bir Federasyon kimlik bilgilerinde görünmesi beklenen gerekli ve isteğe bağlı taleplerin türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-131">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
|[\<issuer>](issuer-of-issuedtokenparameters.md)|<span data-ttu-id="c90ef-132">Geçerli belirteci veren bitiş noktasını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c90ef-132">A configuration element that specifies the endpoint that issues the current token.</span></span>|  
|[\<issuerMetadata>](issuermetadata-of-issuedtokenparameters.md)|<span data-ttu-id="c90ef-133">Belirteç verenin meta verilerinin uç nokta adresini belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c90ef-133">A configuration element that specifies the endpoint address of the token issuer's metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c90ef-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c90ef-134">Parent Elements</span></span>  
  
|<span data-ttu-id="c90ef-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="c90ef-135">Element</span></span>|<span data-ttu-id="c90ef-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c90ef-136">Description</span></span>|  
|-------------|-----------------|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="c90ef-137">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-137">Specifies the default values used for initiating a secure conversation service.</span></span>|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="c90ef-138">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c90ef-138">Specifies the security options for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c90ef-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c90ef-139">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c90ef-140">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c90ef-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c90ef-141">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c90ef-141">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c90ef-142">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c90ef-142">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="c90ef-143">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c90ef-143">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="c90ef-144">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c90ef-144">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
- [<span data-ttu-id="c90ef-145">Kimlik Doğrulama ile Hizmet Kimliği</span><span class="sxs-lookup"><span data-stu-id="c90ef-145">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c90ef-146">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c90ef-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c90ef-147">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="c90ef-147">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c90ef-148">Federasyon ve Verilen Belirteçler</span><span class="sxs-lookup"><span data-stu-id="c90ef-148">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
