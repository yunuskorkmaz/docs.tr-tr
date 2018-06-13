---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f9daea7d6b78e2f6790050b35dde62db6058c60b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757476"
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="5ac08-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="5ac08-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="5ac08-103">Güvenilen yayıncı sertifikaları yapılandırma temelli verenin adı kayıt defteri tarafından kullanılan listesini yapılandırır (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="5ac08-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="5ac08-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5ac08-104">\<system.identityModel></span></span>  
<span data-ttu-id="5ac08-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5ac08-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5ac08-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="5ac08-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5ac08-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5ac08-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="5ac08-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="5ac08-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="5ac08-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="5ac08-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac08-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ac08-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ac08-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac08-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5ac08-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ac08-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ac08-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ac08-113">Attributes</span></span>  
 <span data-ttu-id="5ac08-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ac08-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5ac08-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac08-115">Child Elements</span></span>  
  
|<span data-ttu-id="5ac08-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ac08-116">Element</span></span>|<span data-ttu-id="5ac08-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac08-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="5ac08-118">Bir sertifika, güvenilen verenler koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="5ac08-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="5ac08-119">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5ac08-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="5ac08-120">Bu özniteliği gereklidir ve sertifika parmak izi ASN.1 kodlanmış form içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5ac08-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="5ac08-121">`name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ac08-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="5ac08-122">Tüm sertifikaları Güvenilen verenler koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5ac08-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="5ac08-123">Bir sertifika, güvenilen verenler koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5ac08-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="5ac08-124">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="5ac08-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="5ac08-125">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5ac08-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5ac08-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ac08-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5ac08-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ac08-127">Element</span></span>|<span data-ttu-id="5ac08-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ac08-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ac08-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="5ac08-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="5ac08-130">Yayınlayıcı adı kaydını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="5ac08-130">Configures the issuer name registry.</span></span> <span data-ttu-id="5ac08-131">**Önemli:** `type` özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> için sınıf `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ac08-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ac08-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ac08-132">Remarks</span></span>  
 <span data-ttu-id="5ac08-133">Windows Identity Foundation (WIF) sağlar, tek bir uygulama <xref:System.IdentityModel.Tokens.IssuerNameRegistry> kutusunu dışında sınıfı <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5ac08-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="5ac08-134">Yapılandırma yayınlayıcı adı kaydını yapılandırmasından yüklenen güvenilen verenlerin bir listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="5ac08-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="5ac08-135">Listenin her verenin adı veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="5ac08-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="5ac08-136">Güvenilen yayıncı sertifikaları listesi altında belirtilen `<trustedIssuers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ac08-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="5ac08-137">Her bir öğe listesi anımsatıcı verenin adı, veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="5ac08-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="5ac08-138">Güvenilir sertifikalar ASN.1 kullanılarak kodlanmış form sertifika parmak izi belirtilir ve koleksiyon kullanılarak eklenen `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ac08-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="5ac08-139">İşaretini kaldırın veya verenler (sertifika) kullanarak listeden kaldırmak `<clear>` ve `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5ac08-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="5ac08-140">`type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> için sınıf `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="5ac08-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ac08-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ac08-141">Example</span></span>  
 <span data-ttu-id="5ac08-142">Aşağıdaki XML tabanlı yapılandırma veren belirtmek adı kayıt defteri gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5ac08-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ac08-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ac08-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
