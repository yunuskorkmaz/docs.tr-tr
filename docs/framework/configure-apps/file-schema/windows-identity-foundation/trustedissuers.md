---
description: 'Hakkında daha fazla bilgi edinin: <trustedIssuers>'
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 8789eaa38666e22f6a58b3178103aef4408677b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786518"
---
# \<trustedIssuers>

<span data-ttu-id="8fb14-102">Yapılandırma tabanlı veren adı kayıt defteri () tarafından kullanılan güvenilir veren sertifikalarının listesini yapılandırır <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="8fb14-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="8fb14-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="8fb14-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fb14-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fb14-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8fb14-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8fb14-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fb14-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8fb14-106">Attributes</span></span>  

 <span data-ttu-id="8fb14-107">Yok</span><span class="sxs-lookup"><span data-stu-id="8fb14-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8fb14-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fb14-108">Child Elements</span></span>  
  
|<span data-ttu-id="8fb14-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fb14-109">Element</span></span>|<span data-ttu-id="8fb14-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fb14-110">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="8fb14-111">Güvenilen verenler koleksiyonuna bir sertifika ekler.</span><span class="sxs-lookup"><span data-stu-id="8fb14-111">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="8fb14-112">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-112">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="8fb14-113">Bu öznitelik gereklidir ve sertifika parmak izinin ASN. 1 kodlu biçimini içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-113">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="8fb14-114">`name`Özniteliği isteğe bağlıdır ve sertifika için kolay bir ad belirtmek üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-114">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="8fb14-115">Güvenilen verenler koleksiyonundan tüm sertifikaları temizler.</span><span class="sxs-lookup"><span data-stu-id="8fb14-115">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="8fb14-116">Güvenilen verenler koleksiyonundan bir sertifikayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8fb14-116">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="8fb14-117">Sertifika, `thumbprint` özniteliğiyle belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-117">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="8fb14-118">Bu öznitelik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-118">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8fb14-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8fb14-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8fb14-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="8fb14-120">Element</span></span>|<span data-ttu-id="8fb14-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fb14-121">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="8fb14-122">Verenin adı kayıt defterini yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="8fb14-122">Configures the issuer name registry.</span></span> <span data-ttu-id="8fb14-123">**Önemli:**  `type` Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fb14-123">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb14-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fb14-124">Remarks</span></span>  

 <span data-ttu-id="8fb14-125">Windows Identity Foundation (WıF) <xref:System.IdentityModel.Tokens.IssuerNameRegistry> , sınıfının kutudan, sınıfının tek bir uygulamasını sağlar <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> .</span><span class="sxs-lookup"><span data-stu-id="8fb14-125">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="8fb14-126">Yapılandırma verenin adı kayıt defteri, yapılandırmadan yüklenen güvenilen verenler listesini tutar.</span><span class="sxs-lookup"><span data-stu-id="8fb14-126">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="8fb14-127">Liste, verenin adını veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-127">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="8fb14-128">Güvenilen veren sertifikalarının listesi öğesi altında belirtilir `<trustedIssuers>` .</span><span class="sxs-lookup"><span data-stu-id="8fb14-128">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="8fb14-129">Listedeki her öğe, bu veren tarafından üretilen belirteçlerin imzasını doğrulamak için gereken X. 509.440 sertifikasıyla bir anımsatıcı veren adını ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-129">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="8fb14-130">Güvenilen Sertifikalar, sertifika parmak izinin ASN. 1 kodlu formu kullanılarak belirtilir ve koleksiyon öğesi kullanılarak eklenir `<add>` .</span><span class="sxs-lookup"><span data-stu-id="8fb14-130">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="8fb14-131">Ve öğelerini kullanarak listeden verenler (Sertifikalar) temizleyebilir veya kaldırabilirsiniz `<clear>` `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="8fb14-131">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="8fb14-132">`type`Öğesinin özniteliği, `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` öğesinin geçerli olması için sınıfına başvurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fb14-132">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fb14-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="8fb14-133">Example</span></span>  

 <span data-ttu-id="8fb14-134">Aşağıdaki XML, yapılandırma tabanlı veren adı kayıt defterinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8fb14-134">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fb14-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb14-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
