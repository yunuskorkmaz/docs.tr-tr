---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202527"
---
# <a name="issuernameregistry"></a><span data-ttu-id="0f6a3-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="0f6a3-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="0f6a3-102">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verenin ad Kayıt Defteri'ni yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="0f6a3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0f6a3-103">\<system.identityModel></span></span>  
<span data-ttu-id="0f6a3-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0f6a3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="0f6a3-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="0f6a3-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0f6a3-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0f6a3-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="0f6a3-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="0f6a3-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f6a3-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f6a3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f6a3-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f6a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0f6a3-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f6a3-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0f6a3-111">Attributes</span></span>  
  
|<span data-ttu-id="0f6a3-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0f6a3-112">Attribute</span></span>|<span data-ttu-id="0f6a3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f6a3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f6a3-114">türü</span><span class="sxs-lookup"><span data-stu-id="0f6a3-114">type</span></span>|<span data-ttu-id="0f6a3-115">Türetilen bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="0f6a3-116">Özel bir belirtme hakkında daha fazla bilgi için `type`, [özel tür başvurularını] bakın.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f6a3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f6a3-117">Child Elements</span></span>  
  
|<span data-ttu-id="0f6a3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f6a3-118">Element</span></span>|<span data-ttu-id="0f6a3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f6a3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f6a3-120">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="0f6a3-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="0f6a3-121">Zaman `type` özniteliği belirtir, yapılandırma tabanlı verenin ad Kayıt Defteri'ni ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı), [ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="0f6a3-122">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) öğesi gerçekleştirebileceğiniz `<add>`, `<clear>`, veya `<remove>` öğeleri alt öğeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f6a3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0f6a3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0f6a3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="0f6a3-124">Element</span></span>|<span data-ttu-id="0f6a3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f6a3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f6a3-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0f6a3-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="0f6a3-127">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f6a3-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f6a3-128">Remarks</span></span>  
 <span data-ttu-id="0f6a3-129">Tüm veren belirteçleri bir verenin ad Kayıt Defteri'ni kullanarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="0f6a3-130">Bu, türetilen bir nesnedir <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="0f6a3-131">Yayınlayıcı adı belirteçleri karşılık gelen bir veren tarafından üretilen imzaları doğrulamak için gereken şifreleme malzemelerini bir anımsatıcı adına ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="0f6a3-132">Yayınlayıcı adı bağlı olan taraf (RP) uygulaması tarafından güvenilen verenlerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="0f6a3-133">Yayınlayıcı adı türünü kullanarak belirtilen `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="0f6a3-134">`<issuerNameRegistry>` Öğesi, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğeleri olabilir.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="0f6a3-135">Geçersiz kılarak bu alt öğeleri işler mantığın <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="0f6a3-136">WIF sağlayan tek bir veren adı kayıt türü olarak <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="0f6a3-137">Bu sınıf, bir dizi yapılandırmasında belirtilen güvenilen yayıncı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="0f6a3-138">Bir alt yapılandırma öğesi gerektirir `<trustedIssuers>`, güvenilen yayıncı sertifikaları koleksiyonu yapılandırıldığı altında.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="0f6a3-139">Güvenilen sertifikalar ASN.1 kullanarak kodlanmış sertifika parmak izi form ve eklendiğinde veya koleksiyondan kullanarak kaldırıldığında belirtilen `<add>`, `<clear>`, veya `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="0f6a3-140">`<issuerNameRegistry>` Öğesi tarafından temsil edilen <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f6a3-141">Belirtme `<issuerNameRegistry>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="0f6a3-142">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6a3-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="0f6a3-143">Example</span></span>  
 <span data-ttu-id="0f6a3-144">Aşağıdaki XML tabanlı yapılandırma veren belirtmek ad Kayıt Defteri'ni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f6a3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f6a3-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
