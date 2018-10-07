---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838346"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="6abd6-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="6abd6-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="6abd6-103">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="6abd6-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="6abd6-104">Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="6abd6-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="6abd6-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6abd6-105">\<system.identityModel></span></span>  
<span data-ttu-id="6abd6-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6abd6-106">\<identityConfiguration></span></span>  
<span data-ttu-id="6abd6-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="6abd6-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6abd6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6abd6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6abd6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6abd6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6abd6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6abd6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6abd6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6abd6-111">Attributes</span></span>  
  
|<span data-ttu-id="6abd6-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6abd6-112">Attribute</span></span>|<span data-ttu-id="6abd6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6abd6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6abd6-114">Certificatevalidationmode'u</span><span class="sxs-lookup"><span data-stu-id="6abd6-114">certificateValidationMode</span></span>|<span data-ttu-id="6abd6-115">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6abd6-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6abd6-116">"PeerOrChainTrust" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6abd6-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="6abd6-117">Özel Doğrulayıcı sağlayıcısı belirtmek için bu özniteliği "Özel" olarak ayarlanmış ve kullanarak Doğrulayıcı belirtin [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6abd6-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="6abd6-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6abd6-118">Optional.</span></span>|  
|<span data-ttu-id="6abd6-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6abd6-119">revocationMode</span></span>|<span data-ttu-id="6abd6-120">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6abd6-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6abd6-121">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="6abd6-121">The default value is "Online".</span></span> <span data-ttu-id="6abd6-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6abd6-122">Optional.</span></span>|  
|<span data-ttu-id="6abd6-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6abd6-123">trustedStoreLocation</span></span>|<span data-ttu-id="6abd6-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6abd6-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="6abd6-125">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6abd6-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="6abd6-126">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6abd6-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6abd6-127">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6abd6-127">Child Elements</span></span>  
  
|<span data-ttu-id="6abd6-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="6abd6-128">Element</span></span>|<span data-ttu-id="6abd6-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6abd6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6abd6-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="6abd6-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="6abd6-131">Sertifika doğrulama için özel bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6abd6-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="6abd6-132">Bu tür, yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6abd6-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6abd6-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6abd6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6abd6-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="6abd6-134">Element</span></span>|<span data-ttu-id="6abd6-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6abd6-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6abd6-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6abd6-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="6abd6-137">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6abd6-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="6abd6-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6abd6-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="6abd6-139">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6abd6-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6abd6-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6abd6-140">Remarks</span></span>  
 <span data-ttu-id="6abd6-141">A `<certificateValidation>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6abd6-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="6abd6-142">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6abd6-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="6abd6-143">Bazı belirteç işleyicileri yapılandırmada sertifika doğrulaması ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6abd6-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="6abd6-144">Ayarları tek tek belirteç işleyicileri belirtilen hizmet düzeyinde ve güvenlik belirteci işleyicisi koleksiyonu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6abd6-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6abd6-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="6abd6-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
