---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667359"
---
# <a name="certificatevalidation"></a><span data-ttu-id="6a168-101">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="6a168-101">\<certificateValidation></span></span>
<span data-ttu-id="6a168-102">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="6a168-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="6a168-103">Belirli bir işleyici kendi Doğrulayıcı ile yapılandırılmışsa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="6a168-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="6a168-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="6a168-104">\<system.identityModel></span></span>  
<span data-ttu-id="6a168-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6a168-105">\<identityConfiguration></span></span>  
<span data-ttu-id="6a168-106">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="6a168-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a168-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a168-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a168-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a168-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6a168-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a168-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a168-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6a168-110">Attributes</span></span>  
  
|<span data-ttu-id="6a168-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6a168-111">Attribute</span></span>|<span data-ttu-id="6a168-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a168-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a168-113">Certificatevalidationmode'u</span><span class="sxs-lookup"><span data-stu-id="6a168-113">certificateValidationMode</span></span>|<span data-ttu-id="6a168-114">Bir <xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 sertifikası için kullanılacak doğrulama modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6a168-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6a168-115">"PeerOrChainTrust" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6a168-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="6a168-116">Özel Doğrulayıcı sağlayıcısı belirtmek için bu özniteliği "Özel" olarak ayarlanmış ve kullanarak Doğrulayıcı belirtin [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a168-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="6a168-117">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6a168-117">Optional.</span></span>|  
|<span data-ttu-id="6a168-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6a168-118">revocationMode</span></span>|<span data-ttu-id="6a168-119">Bir <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 sertifikası için İptal modu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6a168-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="6a168-120">Varsayılan değer "Çevrimiçi" olur.</span><span class="sxs-lookup"><span data-stu-id="6a168-120">The default value is "Online".</span></span> <span data-ttu-id="6a168-121">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6a168-121">Optional.</span></span>|  
|<span data-ttu-id="6a168-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6a168-122">trustedStoreLocation</span></span>|<span data-ttu-id="6a168-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 Sertifika deposunun belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="6a168-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="6a168-124">"LocalMachine" varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6a168-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="6a168-125">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="6a168-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a168-126">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a168-126">Child Elements</span></span>  
  
|<span data-ttu-id="6a168-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a168-127">Element</span></span>|<span data-ttu-id="6a168-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a168-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a168-129">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="6a168-129">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="6a168-130">Sertifika doğrulama için özel bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a168-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="6a168-131">Bu tür, yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6a168-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a168-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6a168-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6a168-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a168-133">Element</span></span>|<span data-ttu-id="6a168-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a168-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a168-135">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6a168-135">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="6a168-136">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6a168-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="6a168-137">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6a168-137">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="6a168-138">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a168-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a168-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a168-139">Remarks</span></span>  
 <span data-ttu-id="6a168-140">A `<certificateValidation>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="6a168-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="6a168-141">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6a168-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="6a168-142">Bazı belirteç işleyicileri yapılandırmada sertifika doğrulaması ayarları belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a168-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="6a168-143">Ayarları tek tek belirteç işleyicileri belirtilen hizmet düzeyinde ve güvenlik belirteci işleyicisi koleksiyonu geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6a168-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a168-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a168-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
