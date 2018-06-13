---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af4dc459da49b46d70276d3f4bcd5f94d2a91ffe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756065"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="1d660-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="1d660-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="1d660-103">Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="1d660-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="1d660-104">Belirli bir işleyici ile kendi Doğrulayıcı yapılandırdıysanız bu ayarları geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="1d660-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="1d660-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1d660-105">\<system.identityModel></span></span>  
<span data-ttu-id="1d660-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1d660-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1d660-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1d660-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d660-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d660-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d660-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d660-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d660-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d660-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d660-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d660-111">Attributes</span></span>  
  
|<span data-ttu-id="1d660-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d660-112">Attribute</span></span>|<span data-ttu-id="1d660-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d660-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d660-114">certificateValidationMode değerini</span><span class="sxs-lookup"><span data-stu-id="1d660-114">certificateValidationMode</span></span>|<span data-ttu-id="1d660-115">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası kullanmak için doğrulama modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1d660-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1d660-116">Varsayılan değer "PeerOrChainTrust" dir.</span><span class="sxs-lookup"><span data-stu-id="1d660-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="1d660-117">Özel Doğrulayıcı sağlayıcısı belirtmek için bu özniteliği "Özel" olarak ayarlanmış ve kullanarak Doğrulayıcı belirtin [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d660-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="1d660-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d660-118">Optional.</span></span>|  
|<span data-ttu-id="1d660-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1d660-119">revocationMode</span></span>|<span data-ttu-id="1d660-120">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası kullanmak için İptali modu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1d660-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1d660-121">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="1d660-121">The default value is "Online".</span></span> <span data-ttu-id="1d660-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d660-122">Optional.</span></span>|  
|<span data-ttu-id="1d660-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1d660-123">trustedStoreLocation</span></span>|<span data-ttu-id="1d660-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposu belirten değer.</span><span class="sxs-lookup"><span data-stu-id="1d660-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1d660-125">Varsayılan değer "LocalMachine" dir.</span><span class="sxs-lookup"><span data-stu-id="1d660-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="1d660-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d660-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d660-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d660-127">Child Elements</span></span>  
  
|<span data-ttu-id="1d660-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d660-128">Element</span></span>|<span data-ttu-id="1d660-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d660-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d660-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="1d660-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="1d660-131">Sertifika doğrulama için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d660-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1d660-132">Bu tür yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) öğesi, "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1d660-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d660-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d660-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1d660-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d660-134">Element</span></span>|<span data-ttu-id="1d660-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d660-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d660-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1d660-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="1d660-137">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d660-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1d660-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1d660-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1d660-139">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d660-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d660-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1d660-140">Remarks</span></span>  
 <span data-ttu-id="1d660-141">A `<certificateValidation>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1d660-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1d660-142">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1d660-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="1d660-143">Bazı belirteci işleyicileri yapılandırmasında sertifika doğrulama ayarları belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1d660-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="1d660-144">Ayarları tek tek belirteç işleyicileri belirtilen hizmet düzeyinde ve güvenlik belirteci işleyicisi koleksiyonu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1d660-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d660-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d660-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
