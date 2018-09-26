---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 994677904cada71dbc7cce4b6ca0de1d4dc65014
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085671"
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="54501-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="54501-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="54501-103">İsteğe bağlı yapılandırma için sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıfı veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="54501-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="54501-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="54501-104">\<system.identityModel></span></span>  
<span data-ttu-id="54501-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="54501-105">\<identityConfiguration></span></span>  
<span data-ttu-id="54501-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="54501-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="54501-107">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="54501-107">\<add></span></span>  
<span data-ttu-id="54501-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="54501-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54501-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54501-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54501-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="54501-110">Attributes and Elements</span></span>  
 <span data-ttu-id="54501-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="54501-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54501-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="54501-112">Attributes</span></span>  
  
|<span data-ttu-id="54501-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="54501-113">Attribute</span></span>|<span data-ttu-id="54501-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54501-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54501-115">Certificatevalidationmode'u</span><span class="sxs-lookup"><span data-stu-id="54501-115">certificateValidationMode</span></span>|<span data-ttu-id="54501-116">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="54501-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="54501-117">"PeerOrChainTrust" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="54501-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="54501-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="54501-118">mapToWindows</span></span>|<span data-ttu-id="54501-119">Belirteci işleyicisi doğrulama belirteci için bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="54501-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="54501-120">Varsayılan değer "false" dir.</span><span class="sxs-lookup"><span data-stu-id="54501-120">The default is "false".</span></span>|  
|<span data-ttu-id="54501-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="54501-121">revocationMode</span></span>|<span data-ttu-id="54501-122">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="54501-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="54501-123">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="54501-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="54501-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="54501-124">trustedStoreLocation</span></span>|<span data-ttu-id="54501-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="54501-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="54501-126">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="54501-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="54501-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="54501-127">certificateValidator</span></span>|<span data-ttu-id="54501-128">Öğesinden türetilen özel bir tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="54501-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="54501-129">Varsa `certificateValidationMode` özniteliktir "Özel", bu türden veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="54501-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54501-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="54501-130">Child Elements</span></span>  
 <span data-ttu-id="54501-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="54501-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54501-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="54501-132">Parent Elements</span></span>  
  
|<span data-ttu-id="54501-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="54501-133">Element</span></span>|<span data-ttu-id="54501-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54501-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54501-135">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="54501-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="54501-136">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyona ekler.</span><span class="sxs-lookup"><span data-stu-id="54501-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54501-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="54501-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
