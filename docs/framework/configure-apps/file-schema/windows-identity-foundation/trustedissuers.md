---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: bb4cb5178885b90ef25ee827c2f11593ead6e73d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276685"
---
# <a name="trustedissuers"></a><span data-ttu-id="bd31d-101">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="bd31d-101">\<trustedIssuers></span></span>
<span data-ttu-id="bd31d-102">Yapılandırma temelli yayınlayıcı adı tarafından kullanılan Güvenilen yayıncı sertifikaları listesinde yapılandırır (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="bd31d-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="bd31d-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bd31d-103">\<system.identityModel></span></span>  
<span data-ttu-id="bd31d-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bd31d-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bd31d-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="bd31d-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bd31d-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bd31d-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="bd31d-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="bd31d-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="bd31d-108">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="bd31d-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd31d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd31d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd31d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd31d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd31d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd31d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd31d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd31d-112">Attributes</span></span>  
 <span data-ttu-id="bd31d-113">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="bd31d-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bd31d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd31d-114">Child Elements</span></span>  
  
|<span data-ttu-id="bd31d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd31d-115">Element</span></span>|<span data-ttu-id="bd31d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd31d-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="bd31d-117">Sertifika, güvenilen verenler koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="bd31d-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="bd31d-118">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bd31d-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="bd31d-119">Bu özellik gereklidir ve sertifika parmak izini ASN.1 kodlanmış biçiminde içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="bd31d-120">`name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="bd31d-121">Tüm sertifikaları Güvenilen verenler koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd31d-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="bd31d-122">Sertifika, güvenilen verenler koleksiyonundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bd31d-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="bd31d-123">Sertifika ile belirtilen `thumbprint` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="bd31d-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="bd31d-124">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bd31d-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd31d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bd31d-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd31d-126">Element</span></span>|<span data-ttu-id="bd31d-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd31d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd31d-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="bd31d-128">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="bd31d-129">Yayınlayıcı adı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="bd31d-129">Configures the issuer name registry.</span></span> <span data-ttu-id="bd31d-130">**Önemli:**  `type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd31d-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd31d-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd31d-131">Remarks</span></span>  
 <span data-ttu-id="bd31d-132">Windows Identity Foundation (WIF) tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.IssuerNameRegistry> sınıfı ilk günden <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bd31d-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="bd31d-133">Yapılandırma verenin ad Kayıt Defteri'ni yapılandırmasından yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="bd31d-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="bd31d-134">Listenin her verenin adı veren tarafından üretilen belirteçleri imzasını için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="bd31d-135">Güvenilen yayıncı sertifikaları listesi altında belirtilen `<trustedIssuers>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd31d-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="bd31d-136">Listedeki her öğe bir anımsatıcı verenin adı, veren tarafından üretilen belirteçleri imzasını doğrulamak için gereken X.509 sertifikası ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="bd31d-137">Güvenilen sertifikalar ASN.1 kullanarak kodlanmış sertifika parmak izi biçiminde belirtilir ve koleksiyonu kullanılarak eklenen `<add>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd31d-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="bd31d-138">Temizleyin veya verenler (sertifika) kullanarak listeden kaldırma `<clear>` ve `<remove>` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="bd31d-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="bd31d-139">`type` Özniteliği `<issuerNameRegistry>` öğesi başvurmalıdır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfının `<trustedIssuers>` geçerli olması için öğesi.</span><span class="sxs-lookup"><span data-stu-id="bd31d-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd31d-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd31d-140">Example</span></span>  
 <span data-ttu-id="bd31d-141">Aşağıdaki XML tabanlı yapılandırma veren belirtmek ad Kayıt Defteri'ni gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd31d-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd31d-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd31d-142">See also</span></span>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
