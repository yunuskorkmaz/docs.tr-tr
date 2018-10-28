---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: de3ceb5d84d17307c69e9155834a0a584e6920a1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185920"
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="37ab3-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="37ab3-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="37ab3-103">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verenin ad Kayıt Defteri'ni yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="37ab3-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="37ab3-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37ab3-104">\<system.identityModel></span></span>  
<span data-ttu-id="37ab3-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ab3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="37ab3-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="37ab3-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="37ab3-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ab3-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="37ab3-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="37ab3-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ab3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37ab3-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ab3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37ab3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37ab3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ab3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37ab3-112">Attributes</span></span>  
  
|<span data-ttu-id="37ab3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37ab3-113">Attribute</span></span>|<span data-ttu-id="37ab3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ab3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37ab3-115">türü</span><span class="sxs-lookup"><span data-stu-id="37ab3-115">type</span></span>|<span data-ttu-id="37ab3-116">Türetilen bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ab3-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="37ab3-117">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.</span><span class="sxs-lookup"><span data-stu-id="37ab3-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37ab3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab3-118">Child Elements</span></span>  
  
|<span data-ttu-id="37ab3-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="37ab3-119">Element</span></span>|<span data-ttu-id="37ab3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ab3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ab3-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="37ab3-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="37ab3-122">Zaman `type` özniteliği belirtir, yapılandırma tabanlı verenin ad Kayıt Defteri'ni ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="37ab3-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="37ab3-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi gerçekleştirebileceğiniz `<add>`, `<clear>`, veya `<remove>` öğeleri alt öğeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="37ab3-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37ab3-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="37ab3-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="37ab3-125">Element</span></span>|<span data-ttu-id="37ab3-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ab3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ab3-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="37ab3-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="37ab3-128">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="37ab3-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ab3-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37ab3-129">Remarks</span></span>  
 <span data-ttu-id="37ab3-130">Tüm veren belirteçleri bir verenin ad Kayıt Defteri'ni kullanarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="37ab3-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="37ab3-131">Bu, türetilen bir nesnedir <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ab3-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="37ab3-132">Yayınlayıcı adı belirteçleri karşılık gelen bir veren tarafından üretilen imzaları doğrulamak için gereken şifreleme malzemelerini bir anımsatıcı adına ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="37ab3-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="37ab3-133">Yayınlayıcı adı bağlı olan taraf (RP) uygulaması tarafından güvenilen verenlerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="37ab3-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="37ab3-134">Yayınlayıcı adı türünü kullanarak belirtilen `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="37ab3-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="37ab3-135">`<issuerNameRegistry>` Öğesi, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="37ab3-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="37ab3-136">Geçersiz kılarak bu alt öğeleri işler mantığın <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="37ab3-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="37ab3-137">WIF sağlayan tek bir veren adı kayıt türü olarak <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ab3-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="37ab3-138">Bu sınıf, bir dizi yapılandırmasında belirtilen güvenilen yayıncı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="37ab3-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="37ab3-139">Bir alt yapılandırma öğesi gerektirir `<trustedIssuers>`, güvenilen yayıncı sertifikaları koleksiyonu yapılandırıldığı altında.</span><span class="sxs-lookup"><span data-stu-id="37ab3-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="37ab3-140">Güvenilen sertifikalar ASN.1 kullanarak kodlanmış sertifika parmak izi form ve eklendiğinde veya koleksiyondan kullanarak kaldırıldığında belirtilen `<add>`, `<clear>`, veya `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="37ab3-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="37ab3-141">`<issuerNameRegistry>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="37ab3-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37ab3-142">Belirtme `<issuerNameRegistry>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="37ab3-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="37ab3-143">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="37ab3-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ab3-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="37ab3-144">Example</span></span>  
 <span data-ttu-id="37ab3-145">Aşağıdaki XML tabanlı yapılandırma veren belirtmek ad Kayıt Defteri'ni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="37ab3-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37ab3-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37ab3-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
