---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152456"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="5fc61-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="5fc61-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="5fc61-102"><xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> Sınıf veya türetilmiş sınıflar için isteğe bağlı yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fc61-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="5fc61-103">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5fc61-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5fc61-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5fc61-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5fc61-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5fc61-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5fc61-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlikTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="5fc61-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="5fc61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>ekleyin**](add.md)</span><span class="sxs-lookup"><span data-stu-id="5fc61-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="5fc61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span><span class="sxs-lookup"><span data-stu-id="5fc61-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc61-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fc61-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fc61-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fc61-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5fc61-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fc61-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fc61-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5fc61-112">Attributes</span></span>  
  
|<span data-ttu-id="5fc61-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5fc61-113">Attribute</span></span>|<span data-ttu-id="5fc61-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fc61-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fc61-115">sertifikaDoğrulamaModu</span><span class="sxs-lookup"><span data-stu-id="5fc61-115">certificateValidationMode</span></span>|<span data-ttu-id="5fc61-116">X.509 sertifikası için kullanılacak doğrulama modunu belirten bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> değer.</span><span class="sxs-lookup"><span data-stu-id="5fc61-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5fc61-117">Varsayılan değer "PeerOrChainTrust"tır.</span><span class="sxs-lookup"><span data-stu-id="5fc61-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="5fc61-118">haritaToWindows</span><span class="sxs-lookup"><span data-stu-id="5fc61-118">mapToWindows</span></span>|<span data-ttu-id="5fc61-119">Belirteç işleyicisinin gelen UPN talebini kullanarak doğrulama belirteciyle bir Windows hesabıyla eşlemesi gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fc61-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="5fc61-120">Varsayılan "false" olur.</span><span class="sxs-lookup"><span data-stu-id="5fc61-120">The default is "false".</span></span>|  
|<span data-ttu-id="5fc61-121">iptalModu</span><span class="sxs-lookup"><span data-stu-id="5fc61-121">revocationMode</span></span>|<span data-ttu-id="5fc61-122">X.509 sertifikası için kullanılacak iptal modunu belirten bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değer.</span><span class="sxs-lookup"><span data-stu-id="5fc61-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5fc61-123">Varsayılan değer "Çevrimiçi"dir.</span><span class="sxs-lookup"><span data-stu-id="5fc61-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="5fc61-124">güvenilirStoreLocation</span><span class="sxs-lookup"><span data-stu-id="5fc61-124">trustedStoreLocation</span></span>|<span data-ttu-id="5fc61-125">X.509 sertifika deposunu belirten bir <xref:System.Security.Cryptography.X509Certificates.StoreLocation> değer.</span><span class="sxs-lookup"><span data-stu-id="5fc61-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="5fc61-126">Varsayılan değer "LocalMachine"dir.</span><span class="sxs-lookup"><span data-stu-id="5fc61-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="5fc61-127">sertifikaValidator</span><span class="sxs-lookup"><span data-stu-id="5fc61-127">certificateValidator</span></span>|<span data-ttu-id="5fc61-128">'den <xref:System.IdentityModel.Selectors.X509CertificateValidator>türeyen özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="5fc61-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="5fc61-129">`certificateValidationMode` Öznitelik "Özel" ise, bu tür bir örneği veren sertifika doğrulama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fc61-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fc61-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fc61-130">Child Elements</span></span>  
 <span data-ttu-id="5fc61-131">None</span><span class="sxs-lookup"><span data-stu-id="5fc61-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fc61-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5fc61-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5fc61-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="5fc61-133">Element</span></span>|<span data-ttu-id="5fc61-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5fc61-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fc61-135">\<>ekleyin</span><span class="sxs-lookup"><span data-stu-id="5fc61-135">\<add></span></span>](add.md)|<span data-ttu-id="5fc61-136">Belirteç işleyicisi koleksiyonuna belirtilen güvenlik belirteci işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="5fc61-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5fc61-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fc61-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
