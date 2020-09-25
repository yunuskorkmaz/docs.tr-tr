---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 08cddd19f40f039f86e100cc7ee6a78633502eb2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185567"
---
# \<trustedIssuers>

<span data-ttu-id="ac933-101">Yapılandırma tabanlı veren adı kayıt defteri () tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="ac933-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="ac933-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="ac933-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac933-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac933-103">Attributes and Elements</span></span>  

 <span data-ttu-id="ac933-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac933-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac933-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac933-105">Attributes</span></span>  

 <span data-ttu-id="ac933-106">Yok</span><span class="sxs-lookup"><span data-stu-id="ac933-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ac933-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac933-107">Child Elements</span></span>  
  
|<span data-ttu-id="ac933-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac933-108">Element</span></span>|<span data-ttu-id="ac933-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac933-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="ac933-110">Güvenilen verenler koleksiyonuna bir sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="ac933-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="ac933-111">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ac933-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="ac933-112">Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ac933-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="ac933-113">`name`Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ac933-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="ac933-114">Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.</span><span class="sxs-lookup"><span data-stu-id="ac933-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="ac933-115">Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ac933-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="ac933-116">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ac933-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="ac933-117">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ac933-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ac933-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac933-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ac933-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac933-119">Element</span></span>|<span data-ttu-id="ac933-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac933-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="ac933-121">Verenin adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ac933-121">Configures the issuer name registry.</span></span> <span data-ttu-id="ac933-122">**Önemli:**  `type` Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac933-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac933-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac933-123">Remarks</span></span>  

 <span data-ttu-id="ac933-124">Windows Identity Foundation (WıF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="ac933-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="ac933-125">Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="ac933-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="ac933-126">Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="ac933-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="ac933-127">Güvenilen veren sertifikalarının listesi öğesi altında belirtilir `<trustedIssuers>` .</span><span class="sxs-lookup"><span data-stu-id="ac933-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="ac933-128">Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="ac933-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="ac933-129">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak eklenir `<add>` .</span><span class="sxs-lookup"><span data-stu-id="ac933-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="ac933-130">Ve öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz `<clear>` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="ac933-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="ac933-131">`type`Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ac933-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac933-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac933-132">Example</span></span>  

 <span data-ttu-id="ac933-133">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac933-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac933-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac933-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
