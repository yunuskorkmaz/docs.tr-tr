---
description: 'Hakkında daha fazla bilgi edinin: <issuerNameRegistry>'
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 73eb0d9d4d19f8e25f2db501e8cb3858d346ac2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803860"
---
# \<issuerNameRegistry>

<span data-ttu-id="27c2b-102">Belirteç işleyici koleksiyonundaki işleyiciler tarafından kullanılan veren adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="27c2b-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="27c2b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="27c2b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27c2b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c2b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="27c2b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27c2b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27c2b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="27c2b-106">Attributes</span></span>  
  
|<span data-ttu-id="27c2b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="27c2b-107">Attribute</span></span>|<span data-ttu-id="27c2b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c2b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27c2b-109">tür</span><span class="sxs-lookup"><span data-stu-id="27c2b-109">type</span></span>|<span data-ttu-id="27c2b-110">Sınıfından türeten bir tür <xref:System.IdentityModel.Tokens.IssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="27c2b-110">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="27c2b-111">Özel belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları].</span><span class="sxs-lookup"><span data-stu-id="27c2b-111">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27c2b-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c2b-112">Child Elements</span></span>  
  
|<span data-ttu-id="27c2b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="27c2b-113">Element</span></span>|<span data-ttu-id="27c2b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c2b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="27c2b-115">Öznitelik, `type` yapılandırma tabanlı veren adı kayıt defterini ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı) belirttiğinde, [\<trustedIssuers>](trustedissuers.md) öğe belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-115">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="27c2b-116">[\<trustedIssuers>](trustedissuers.md)Öğesi `<add>` , `<clear>` `<remove>` alt öğeleri olarak, veya öğelerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-116">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27c2b-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="27c2b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="27c2b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="27c2b-118">Element</span></span>|<span data-ttu-id="27c2b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27c2b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="27c2b-120">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="27c2b-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27c2b-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27c2b-121">Remarks</span></span>  

 <span data-ttu-id="27c2b-122">Tüm verenin belirteçleri, bir veren adı kayıt defteri kullanılarak onaylanır.</span><span class="sxs-lookup"><span data-stu-id="27c2b-122">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="27c2b-123">Bu, sınıfından türetilen bir nesnedir <xref:System.IdentityModel.Tokens.IssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="27c2b-123">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="27c2b-124">Veren adı kayıt defteri, bir anımsatıcı adını, ilgili veren tarafından üretilen belirteçlerin imzalarını doğrulamak için gereken şifreleme malzemesiyle ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27c2b-124">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="27c2b-125">Veren adı kayıt defteri, bağlı olan taraf (RP) uygulaması tarafından güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="27c2b-125">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="27c2b-126">Veren adı kayıt defterinin türü, özniteliği kullanılarak belirtilir `type` .</span><span class="sxs-lookup"><span data-stu-id="27c2b-126">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="27c2b-127">`<issuerNameRegistry>`Öğe, belirtilen tür için yapılandırma sağlayan bir veya daha fazla alt öğe içerebilir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-127">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="27c2b-128">Yöntemi geçersiz kılarak bu alt öğeleri işleyen mantığı sağlarsınız <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> .</span><span class="sxs-lookup"><span data-stu-id="27c2b-128">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="27c2b-129">WıF, sınıfından tek bir veren adı kayıt defteri türü sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="27c2b-129">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="27c2b-130">Bu sınıf, yapılandırmada belirtilen bir güvenilen veren sertifikaları kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="27c2b-130">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="27c2b-131">Bu, `<trustedIssuers>` altında güvenilir veren sertifikaları koleksiyonunun yapılandırıldığı bir alt yapılandırma öğesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-131">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="27c2b-132">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve `<add>` , veya öğeleri kullanılarak koleksiyona eklenir veya kaldırılır `<clear>` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="27c2b-132">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="27c2b-133">`<issuerNameRegistry>`Öğesi sınıfı tarafından temsil edilir <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> .</span><span class="sxs-lookup"><span data-stu-id="27c2b-133">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27c2b-134">Öğenin `<issuerNameRegistry>` bir alt öğesi olarak belirtilmesi [\<identityConfiguration>](identityconfiguration.md) kullanım dışı bırakılmıştır, ancak yine de geriye dönük uyumluluk için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-134">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="27c2b-135">`<securityTokenHandlerConfiguration>`Öğesindeki ayarlar, öğesinde olanları geçersiz kılar `<identityConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="27c2b-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27c2b-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="27c2b-136">Example</span></span>  

 <span data-ttu-id="27c2b-137">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="27c2b-137">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27c2b-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c2b-138">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
