---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 946ae8601e1e4563becd0b346b6c792724405a45
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165045"
---
# \<issuerTokenResolver>

<span data-ttu-id="f3938-101">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren belirteç çözümleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f3938-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f3938-102">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3938-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="f3938-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3938-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3938-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3938-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f3938-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3938-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3938-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3938-106">Attributes</span></span>  
  
|<span data-ttu-id="f3938-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3938-107">Attribute</span></span>|<span data-ttu-id="f3938-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3938-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3938-109">tür</span><span class="sxs-lookup"><span data-stu-id="f3938-109">type</span></span>|<span data-ttu-id="f3938-110">Verenin belirteç Çözümleyicisinin türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3938-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="f3938-111">Sınıf <xref:System.IdentityModel.Tokens.IssuerTokenResolver> ya da sınıftan türetilmiş bir tür olmalıdır <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="f3938-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="f3938-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f3938-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3938-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3938-113">Child Elements</span></span>  

 <span data-ttu-id="f3938-114">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f3938-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3938-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3938-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f3938-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3938-116">Element</span></span>|<span data-ttu-id="f3938-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3938-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f3938-118">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3938-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3938-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3938-119">Remarks</span></span>  

 <span data-ttu-id="f3938-120">Veren belirteç çözümleyici, gelen belirteçlerde ve iletilerde imzalama belirtecini çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3938-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="f3938-121">İmzayı denetlemek için kullanılan şifreleme malzemesini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f3938-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="f3938-122">Özniteliğini belirtmeniz gerekir `type` .</span><span class="sxs-lookup"><span data-stu-id="f3938-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="f3938-123">Belirtilen tür ya da <xref:System.IdentityModel.Tokens.IssuerTokenResolver> sınıfından türetilen özel bir tür olabilir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="f3938-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="f3938-124">Bazı belirteç işleyicileri yapılandırmada veren belirteç çözümleyici ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f3938-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="f3938-125">Bağımsız belirteç işleyicilerindeki ayarlar, güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f3938-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3938-126">Öğenin `<issuerTokenResolver>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f3938-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="f3938-127">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="f3938-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3938-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3938-128">Example</span></span>  

 <span data-ttu-id="f3938-129">Aşağıdaki XML, ' den türetilen özel bir sınıfa dayalı bir veren belirteç Çözümleyicisi için yapılandırmayı gösterir <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="f3938-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="f3938-130">Belirteç çözümleyici, sınıf için tanımlanan özel bir yapılandırma öğesinden () başlatılan bir hedef kitle anahtar çiftleri sözlüğü içerir `<AddAudienceKeyPair>` .</span><span class="sxs-lookup"><span data-stu-id="f3938-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="f3938-131">Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> Bu öğeyi işlemek için yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f3938-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="f3938-132">Geçersiz kılma aşağıdaki örnekte gösterilmiştir; ancak çağrı yaptığı Yöntemler breçekimi için gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="f3938-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="f3938-133">Tüm örnek için `CustomToken` örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="f3938-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="f3938-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3938-134">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3938-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3938-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
