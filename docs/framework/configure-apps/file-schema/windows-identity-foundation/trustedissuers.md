---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944267"
---
# <a name="trustedissuers"></a><span data-ttu-id="2386c-101">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="2386c-101">\<trustedIssuers></span></span>
<span data-ttu-id="2386c-102">Yapılandırma tabanlı veren adı kayıt defteri (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2386c-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="2386c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2386c-103">\<system.identityModel></span></span>  
<span data-ttu-id="2386c-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2386c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2386c-105">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="2386c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2386c-106">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="2386c-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="2386c-107">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="2386c-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="2386c-108">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="2386c-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2386c-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2386c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2386c-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="2386c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2386c-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2386c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2386c-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2386c-112">Attributes</span></span>  
 <span data-ttu-id="2386c-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="2386c-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2386c-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="2386c-114">Child Elements</span></span>  
  
|<span data-ttu-id="2386c-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="2386c-115">Element</span></span>|<span data-ttu-id="2386c-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2386c-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="2386c-117">Güvenilen verenler koleksiyonuna bir sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="2386c-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="2386c-118">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2386c-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="2386c-119">Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2386c-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="2386c-120">`name` Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2386c-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="2386c-121">Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.</span><span class="sxs-lookup"><span data-stu-id="2386c-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="2386c-122">Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2386c-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="2386c-123">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2386c-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="2386c-124">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2386c-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2386c-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="2386c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="2386c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="2386c-126">Element</span></span>|<span data-ttu-id="2386c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2386c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2386c-128">\<ıssuernameregbakanlığı ></span><span class="sxs-lookup"><span data-stu-id="2386c-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="2386c-129">Verenin adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="2386c-129">Configures the issuer name registry.</span></span> <span data-ttu-id="2386c-130">**Önemli:**  Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="2386c-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2386c-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2386c-131">Remarks</span></span>  
 <span data-ttu-id="2386c-132">Windows Identity Foundation (WIF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2386c-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="2386c-133">Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="2386c-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="2386c-134">Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="2386c-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="2386c-135">Güvenilen veren sertifikalarının listesi `<trustedIssuers>` öğesi altında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2386c-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="2386c-136">Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="2386c-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="2386c-137">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak `<add>` eklenir.</span><span class="sxs-lookup"><span data-stu-id="2386c-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="2386c-138">`<clear>` Ve`<remove>` öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2386c-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="2386c-139">Öğesinin özniteliği, öğesinin geçerli olması için <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> sınıfına başvurmalıdır. `<trustedIssuers>` `type` `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="2386c-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2386c-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="2386c-140">Example</span></span>  
 <span data-ttu-id="2386c-141">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2386c-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2386c-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2386c-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
