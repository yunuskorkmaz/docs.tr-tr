---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 66d4e0d6a121f807f5f372b3f39577b0bb3c4ca6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="576db-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="576db-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="576db-103">İçin isteğe bağlı yapılandırma sağlar <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> sınıf veya türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="576db-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="576db-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="576db-104">\<system.identityModel></span></span>  
<span data-ttu-id="576db-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="576db-105">\<identityConfiguration></span></span>  
<span data-ttu-id="576db-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="576db-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="576db-107">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="576db-107">\<add></span></span>  
<span data-ttu-id="576db-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="576db-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576db-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="576db-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="576db-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="576db-110">Attributes and Elements</span></span>  
 <span data-ttu-id="576db-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="576db-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="576db-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="576db-112">Attributes</span></span>  
  
|<span data-ttu-id="576db-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="576db-113">Attribute</span></span>|<span data-ttu-id="576db-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="576db-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="576db-115">certificateValidationMode değerini</span><span class="sxs-lookup"><span data-stu-id="576db-115">certificateValidationMode</span></span>|<span data-ttu-id="576db-116">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="576db-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="576db-117">Varsayılan değer "PeerOrChainTrust" dir.</span><span class="sxs-lookup"><span data-stu-id="576db-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="576db-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="576db-118">mapToWindows</span></span>|<span data-ttu-id="576db-119">Belirteci işleyicisi Doğrulama belirtecini bir Windows hesabı gelen UPN Talebi kullanarak eşlemelisiniz olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="576db-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="576db-120">Varsayılan değer "false" dir.</span><span class="sxs-lookup"><span data-stu-id="576db-120">The default is "false".</span></span>|  
|<span data-ttu-id="576db-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="576db-121">revocationMode</span></span>|<span data-ttu-id="576db-122">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="576db-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="576db-123">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="576db-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="576db-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="576db-124">trustedStoreLocation</span></span>|<span data-ttu-id="576db-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="576db-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="576db-126">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="576db-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="576db-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="576db-127">certificateValidator</span></span>|<span data-ttu-id="576db-128">Türetilen bir özel tür <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="576db-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="576db-129">Varsa `certificateValidationMode` özniteliği "Özel", bu türünün bir örneği veren sertifika doğrulaması için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="576db-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="576db-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="576db-130">Child Elements</span></span>  
 <span data-ttu-id="576db-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="576db-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="576db-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="576db-132">Parent Elements</span></span>  
  
|<span data-ttu-id="576db-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="576db-133">Element</span></span>|<span data-ttu-id="576db-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="576db-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="576db-135">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="576db-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="576db-136">Belirtilen güvenlik belirteci işleyicisi belirteci işleyicisi koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="576db-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="576db-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="576db-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
