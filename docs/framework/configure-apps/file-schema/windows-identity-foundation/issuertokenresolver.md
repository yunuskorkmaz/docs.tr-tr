---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: eefd18c206b7f013c3a423df424c795583c0dde8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216337"
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="5fb22-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="5fb22-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="5fb22-103">Belirteci işleyicisi koleksiyondaki işleyiciler tarafından kullanılan verici belirteç çözümleyici kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5fb22-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="5fb22-104">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fb22-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="5fb22-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5fb22-105">\<system.identityModel></span></span>  
<span data-ttu-id="5fb22-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5fb22-106">\<identityConfiguration></span></span>  
<span data-ttu-id="5fb22-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5fb22-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5fb22-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5fb22-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5fb22-109">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="5fb22-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb22-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fb22-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fb22-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fb22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5fb22-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fb22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fb22-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fb22-113">Attributes</span></span>  
  
|<span data-ttu-id="5fb22-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fb22-114">Attribute</span></span>|<span data-ttu-id="5fb22-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fb22-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fb22-116">türü</span><span class="sxs-lookup"><span data-stu-id="5fb22-116">type</span></span>|<span data-ttu-id="5fb22-117">Veren belirteç çözümleyici türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fb22-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="5fb22-118">Aşağıdakilerden biri olması gereken <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı veya, türetilen tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5fb22-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="5fb22-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5fb22-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fb22-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fb22-120">Child Elements</span></span>  
 <span data-ttu-id="5fb22-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="5fb22-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fb22-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fb22-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5fb22-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fb22-123">Element</span></span>|<span data-ttu-id="5fb22-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fb22-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fb22-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5fb22-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="5fb22-126">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fb22-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fb22-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5fb22-127">Remarks</span></span>  
 <span data-ttu-id="5fb22-128">Veren belirteç Çözümleyici, imzalama belirtecinin gelen belirteçleri ve iletileri çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fb22-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="5fb22-129">İmzayı denetlemek için kullanılan şifreleme malzemelerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fb22-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="5fb22-130">Belirtmelisiniz `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5fb22-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="5fb22-131">Belirtilen türü olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya öğesinden türetilen özel bir tür <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5fb22-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="5fb22-132">Bazı belirteç işleyicileri yapılandırmasında veren belirteç çözümleyici ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fb22-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="5fb22-133">Ayarları tek tek belirteç işleyicileri güvenlik belirteci işleyicisi koleksiyonda belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="5fb22-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fb22-134">Belirtme `<issuerTokenResolver>` öğesi alt öğesi olarak [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi kullanım dışı bırakıldı, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5fb22-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="5fb22-135">Ayarları `<securityTokenHandlerConfiguration>` öğesini geçersiz kılar üzerinde `<identityConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5fb22-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb22-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fb22-136">Example</span></span>  
 <span data-ttu-id="5fb22-137">Aşağıdaki XML yapılandırması için özel bir sınıf türetildiği temel alan bir veren belirteç çözümleyici gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="5fb22-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="5fb22-138">Belirteç Çözümleyici, bir özel yapılandırma öğesinden başlatılmış olan bir sözlük İzleyici anahtar çifti tutar (`<AddAudienceKeyPair>`) sınıfı için tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="5fb22-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="5fb22-139">Sınıf geçersiz kılmalarını <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğenin işlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5fb22-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="5fb22-140">Geçersiz kılma, aşağıdaki örnekte gösterilmiştir; Ancak, çağırdığı yöntemleri uzatmamak için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="5fb22-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="5fb22-141">Tam bir örnek için bkz `CustomToken` örnek.</span><span class="sxs-lookup"><span data-stu-id="5fb22-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="5fb22-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fb22-142">Example</span></span>  
  
```  
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fb22-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5fb22-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
