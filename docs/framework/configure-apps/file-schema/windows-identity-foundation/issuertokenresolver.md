---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942636"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="3ed7c-101">\<IssuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="3ed7c-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3ed7c-103">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="3ed7c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3ed7c-104">\<system.identityModel></span></span>  
<span data-ttu-id="3ed7c-105">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3ed7c-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3ed7c-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="3ed7c-108">\<IssuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed7c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ed7c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ed7c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ed7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ed7c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ed7c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3ed7c-112">Attributes</span></span>  
  
|<span data-ttu-id="3ed7c-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3ed7c-113">Attribute</span></span>|<span data-ttu-id="3ed7c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ed7c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ed7c-115">türü</span><span class="sxs-lookup"><span data-stu-id="3ed7c-115">type</span></span>|<span data-ttu-id="3ed7c-116">Verenin belirteç Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="3ed7c-117">Sınıf ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıftan türetilmiş bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="3ed7c-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ed7c-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ed7c-119">Child Elements</span></span>  
 <span data-ttu-id="3ed7c-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ed7c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3ed7c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3ed7c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="3ed7c-122">Element</span></span>|<span data-ttu-id="3ed7c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ed7c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ed7c-124">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3ed7c-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3ed7c-125">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ed7c-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ed7c-126">Remarks</span></span>  
 <span data-ttu-id="3ed7c-127">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="3ed7c-128">İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="3ed7c-129">`type` Özniteliğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="3ed7c-130">Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="3ed7c-131">Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="3ed7c-132">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ed7c-133">Öğesini IdentityConfiguration > öğesinin bir alt öğesi [olarak belirtmek kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir. \<](identityconfiguration.md) `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="3ed7c-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="3ed7c-134">Öğesindeki ayarlar, `<identityConfiguration>` öğesinde olanları geçersiz kılar. `<securityTokenHandlerConfiguration>`</span><span class="sxs-lookup"><span data-stu-id="3ed7c-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed7c-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ed7c-135">Example</span></span>  
 <span data-ttu-id="3ed7c-136">Aşağıdaki XML, ' den <xref:System.IdentityModel.Tokens.IssuerTokenResolver>türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="3ed7c-137">Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden (`<AddAudienceKeyPair>`) başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="3ed7c-138">Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> bu öğeyi işlemek için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="3ed7c-139">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="3ed7c-140">Tüm örnek için `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="3ed7c-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="3ed7c-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ed7c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ed7c-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
