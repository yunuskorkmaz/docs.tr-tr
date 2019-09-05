---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 8775e3044e58886cfa53a9fd9fc8b4b8ed2105b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251949"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="fadd7-101">\<IssuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="fadd7-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="fadd7-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fadd7-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="fadd7-103">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="fadd7-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fadd7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fadd7-105">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="fadd7-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="fadd7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fadd7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="fadd7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="fadd7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="fadd7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fadd7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="fadd7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<IssuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="fadd7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fadd7-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fadd7-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fadd7-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fadd7-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fadd7-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fadd7-113">Attributes</span></span>  
  
|<span data-ttu-id="fadd7-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fadd7-114">Attribute</span></span>|<span data-ttu-id="fadd7-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fadd7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fadd7-116">türü</span><span class="sxs-lookup"><span data-stu-id="fadd7-116">type</span></span>|<span data-ttu-id="fadd7-117">Verenin belirteç Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fadd7-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="fadd7-118">Sınıf ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türetilmiş bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="fadd7-119">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fadd7-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fadd7-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd7-120">Child Elements</span></span>  
 <span data-ttu-id="fadd7-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="fadd7-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fadd7-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fadd7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fadd7-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="fadd7-123">Element</span></span>|<span data-ttu-id="fadd7-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fadd7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fadd7-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fadd7-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fadd7-126">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="fadd7-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fadd7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fadd7-127">Remarks</span></span>  
 <span data-ttu-id="fadd7-128">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="fadd7-129">İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="fadd7-130">`type` Özniteliğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fadd7-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="fadd7-131">Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="fadd7-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="fadd7-132">Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fadd7-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="fadd7-133">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fadd7-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fadd7-134">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="fadd7-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fadd7-135">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="fadd7-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fadd7-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="fadd7-136">Example</span></span>  
 <span data-ttu-id="fadd7-137">Aşağıdaki XML, ' den <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fadd7-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="fadd7-138">Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden (`<AddAudienceKeyPair>`) başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir.</span><span class="sxs-lookup"><span data-stu-id="fadd7-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="fadd7-139">Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğeyi işlemek için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fadd7-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="fadd7-140">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="fadd7-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="fadd7-141">Tüm örnek için `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="fadd7-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="fadd7-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="fadd7-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fadd7-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fadd7-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
