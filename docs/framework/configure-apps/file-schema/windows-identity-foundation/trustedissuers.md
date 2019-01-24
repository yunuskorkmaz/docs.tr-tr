---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 1459027ae22344d5b1abc917c490b8e98fa0f2c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634005"
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="504ff-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="504ff-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="504ff-103">Yapılandırma temelli yayınlayıcı adı tarafından kullanılan Güvenilen yayıncı sertifikaları listesinde yapılandırır (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="504ff-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="504ff-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="504ff-104">\<system.identityModel></span></span>  
<span data-ttu-id="504ff-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="504ff-105">\<identityConfiguration></span></span>  
<span data-ttu-id="504ff-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="504ff-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="504ff-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="504ff-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="504ff-108">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="504ff-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="504ff-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="504ff-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504ff-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="504ff-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="504ff-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="504ff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="504ff-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="504ff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="504ff-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="504ff-113">Attributes</span></span>  
 <span data-ttu-id="504ff-114">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="504ff-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="504ff-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="504ff-115">Child Elements</span></span>  
  
|<span data-ttu-id="504ff-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="504ff-116">Element</span></span>|<span data-ttu-id="504ff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="504ff-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="504ff-118">Sertifika, güvenilen verenler koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="504ff-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="504ff-119">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="504ff-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="504ff-120">Bu özellik gereklidir ve sertifika parmak izini ASN.1 kodlanmış biçiminde içermelidir.</span><span class="sxs-lookup"><span data-stu-id="504ff-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="504ff-121">`name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="504ff-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="504ff-122">Tüm sertifikaları Güvenilen verenler koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504ff-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="504ff-123">Sertifika, güvenilen verenler koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="504ff-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="504ff-124">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="504ff-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="504ff-125">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="504ff-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="504ff-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="504ff-126">Parent Elements</span></span>  
  
|<span data-ttu-id="504ff-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="504ff-127">Element</span></span>|<span data-ttu-id="504ff-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="504ff-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="504ff-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="504ff-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="504ff-130">Yayınlayıcı adı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="504ff-130">Configures the issuer name registry.</span></span> <span data-ttu-id="504ff-131">**Önemli:**  `type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="504ff-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="504ff-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="504ff-132">Remarks</span></span>  
 <span data-ttu-id="504ff-133">Windows Identity Foundation (WIF) tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı ilk günden <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="504ff-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="504ff-134">Yapılandırma verenin ad Kayıt Defteri'ni yapılandırmasından yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="504ff-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="504ff-135">Listenin her verenin adı veren tarafından üretilen belirteçleri imzasını için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="504ff-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="504ff-136">Güvenilen yayıncı sertifikaları listesi altında belirtilen `<trustedIssuers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="504ff-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="504ff-137">Listedeki her öğe bir anımsatıcı verenin adı, veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="504ff-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="504ff-138">Güvenilen sertifikalar ASN.1 kullanarak kodlanmış sertifika parmak izi biçiminde belirtilir ve koleksiyonu kullanılarak eklenen `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="504ff-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="504ff-139">Temizleyin veya verenler (sertifika) kullanarak listeden kaldırma `<clear>` ve `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="504ff-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="504ff-140">`type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="504ff-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="504ff-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="504ff-141">Example</span></span>  
 <span data-ttu-id="504ff-142">Aşağıdaki XML tabanlı yapılandırma veren belirtmek ad Kayıt Defteri'ni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="504ff-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="504ff-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="504ff-143">See also</span></span>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
