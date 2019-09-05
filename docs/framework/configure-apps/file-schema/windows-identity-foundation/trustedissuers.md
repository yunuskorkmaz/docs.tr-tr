---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251755"
---
# <a name="trustedissuers"></a><span data-ttu-id="d1125-101">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="d1125-101">\<trustedIssuers></span></span>
<span data-ttu-id="d1125-102">Yapılandırma tabanlı veren adı kayıt defteri (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d1125-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
<span data-ttu-id="d1125-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d1125-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d1125-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d1125-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d1125-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="d1125-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ıssuernameregbakanlığı >** ](issuernameregistry.md)</span><span class="sxs-lookup"><span data-stu-id="d1125-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)</span></span>\
<span data-ttu-id="d1125-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trustedIssuers >**</span><span class="sxs-lookup"><span data-stu-id="d1125-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1125-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1125-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1125-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1125-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d1125-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1125-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1125-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1125-113">Attributes</span></span>  
 <span data-ttu-id="d1125-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d1125-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1125-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1125-115">Child Elements</span></span>  
  
|<span data-ttu-id="d1125-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1125-116">Element</span></span>|<span data-ttu-id="d1125-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1125-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="d1125-118">Güvenilen verenler koleksiyonuna bir sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="d1125-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="d1125-119">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d1125-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d1125-120">Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d1125-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="d1125-121">`name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1125-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="d1125-122">Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.</span><span class="sxs-lookup"><span data-stu-id="d1125-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="d1125-123">Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d1125-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="d1125-124">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d1125-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d1125-125">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d1125-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1125-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1125-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d1125-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1125-127">Element</span></span>|<span data-ttu-id="d1125-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1125-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1125-129">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="d1125-129">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="d1125-130">Verenin adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="d1125-130">Configures the issuer name registry.</span></span> <span data-ttu-id="d1125-131">**Önemli:**  Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="d1125-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1125-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1125-132">Remarks</span></span>  
 <span data-ttu-id="d1125-133">Windows Identity Foundation (WIF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1125-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="d1125-134">Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="d1125-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="d1125-135">Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d1125-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="d1125-136">Güvenilen veren sertifikalarının listesi `<trustedIssuers>` öğesi altında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d1125-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="d1125-137">Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d1125-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="d1125-138">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak `<add>` eklenir.</span><span class="sxs-lookup"><span data-stu-id="d1125-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="d1125-139">`<clear>` Ve`<remove>` öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1125-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="d1125-140">Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="d1125-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1125-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1125-141">Example</span></span>  
 <span data-ttu-id="d1125-142">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d1125-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1125-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1125-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
