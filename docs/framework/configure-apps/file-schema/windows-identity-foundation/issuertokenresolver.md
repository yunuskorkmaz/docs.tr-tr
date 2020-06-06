---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152677"
---
# \<issuerTokenResolver>
<span data-ttu-id="87ad2-101">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="87ad2-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="87ad2-102">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87ad2-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="87ad2-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87ad2-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87ad2-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="87ad2-104">Attributes and Elements</span></span>  
 <span data-ttu-id="87ad2-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="87ad2-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87ad2-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="87ad2-106">Attributes</span></span>  
  
|<span data-ttu-id="87ad2-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="87ad2-107">Attribute</span></span>|<span data-ttu-id="87ad2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87ad2-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87ad2-109">tür</span><span class="sxs-lookup"><span data-stu-id="87ad2-109">type</span></span>|<span data-ttu-id="87ad2-110">Verenin belirteç Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="87ad2-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="87ad2-111">Sınıf <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya da sınıftan türetilmiş bir tür olmalıdır <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="87ad2-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="87ad2-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="87ad2-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87ad2-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="87ad2-113">Child Elements</span></span>  
 <span data-ttu-id="87ad2-114">Yok</span><span class="sxs-lookup"><span data-stu-id="87ad2-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87ad2-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="87ad2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="87ad2-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="87ad2-116">Element</span></span>|<span data-ttu-id="87ad2-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87ad2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="87ad2-118">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="87ad2-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87ad2-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87ad2-119">Remarks</span></span>  
 <span data-ttu-id="87ad2-120">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87ad2-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="87ad2-121">İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87ad2-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="87ad2-122">Özniteliğini belirtmeniz gerekir `type` .</span><span class="sxs-lookup"><span data-stu-id="87ad2-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="87ad2-123">Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="87ad2-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="87ad2-124">Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="87ad2-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="87ad2-125">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="87ad2-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87ad2-126">Öğenin `<issuerTokenResolver>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="87ad2-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="87ad2-127">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="87ad2-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87ad2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="87ad2-128">Example</span></span>  
 <span data-ttu-id="87ad2-129">Aşağıdaki XML, ' den türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="87ad2-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="87ad2-130">Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden () başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir `<AddAudienceKeyPair>` .</span><span class="sxs-lookup"><span data-stu-id="87ad2-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="87ad2-131">Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> Bu öğeyi işlemek için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="87ad2-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="87ad2-132">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="87ad2-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="87ad2-133">Tüm örnek için `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="87ad2-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="87ad2-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="87ad2-134">Example</span></span>
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="87ad2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ad2-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
