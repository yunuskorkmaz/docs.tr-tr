---
description: 'Hakkında daha fazla bilgi edinin: <certificateValidation>'
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: a12e46487b4fb2ac8071ba1cf9bc5c6057ded060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740073"
---
# \<certificateValidation>

<span data-ttu-id="3e87a-102">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="3e87a-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="3e87a-103">Belirli bir işleyici kendi doğrulayıcısı ile yapılandırıldıysa, bu ayarlar geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="3e87a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e87a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e87a-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e87a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3e87a-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e87a-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3e87a-107">Attributes</span></span>  
  
|<span data-ttu-id="3e87a-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3e87a-108">Attribute</span></span>|<span data-ttu-id="3e87a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e87a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e87a-110">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="3e87a-110">certificateValidationMode</span></span>|<span data-ttu-id="3e87a-111"><xref:System.ServiceModel.Security.X509CertificateValidationMode>X. 509.440 sertifikası için kullanılacak doğrulama modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3e87a-111">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3e87a-112">Varsayılan değer "PeerOrChainTrust" dır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-112">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="3e87a-113">Özel bir doğrulayıcı belirtmek için, bu özniteliği "Custom" olarak ayarlayın ve öğesini kullanarak Doğrulayıcısı belirtin [\<certificateValidator>](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="3e87a-113">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="3e87a-114">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e87a-114">Optional.</span></span>|  
|<span data-ttu-id="3e87a-115">Revocationmodu</span><span class="sxs-lookup"><span data-stu-id="3e87a-115">revocationMode</span></span>|<span data-ttu-id="3e87a-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>X. 509.440 sertifikası için kullanılacak iptal modunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3e87a-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3e87a-117">Varsayılan değer "çevrimiçi" dır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-117">The default value is "Online".</span></span> <span data-ttu-id="3e87a-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e87a-118">Optional.</span></span>|  
|<span data-ttu-id="3e87a-119">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="3e87a-119">trustedStoreLocation</span></span>|<span data-ttu-id="3e87a-120"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>X. 509.440 sertifika deposunu belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="3e87a-120">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="3e87a-121">Varsayılan değer "LocalMachine" dır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-121">The default value is "LocalMachine".</span></span> <span data-ttu-id="3e87a-122">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3e87a-122">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e87a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e87a-123">Child Elements</span></span>  
  
|<span data-ttu-id="3e87a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e87a-124">Element</span></span>|<span data-ttu-id="3e87a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e87a-125">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="3e87a-126">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e87a-126">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="3e87a-127">Bu tür yalnızca `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) öğenin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-127">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3e87a-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3e87a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3e87a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="3e87a-129">Element</span></span>|<span data-ttu-id="3e87a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e87a-130">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="3e87a-131">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e87a-131">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="3e87a-132">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e87a-132">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e87a-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e87a-133">Remarks</span></span>  

 <span data-ttu-id="3e87a-134">Öğesi `<certificateValidation>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="3e87a-134">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="3e87a-135">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3e87a-135">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="3e87a-136">Bazı belirteç işleyicileri, yapılandırmada sertifika doğrulama ayarlarını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3e87a-136">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="3e87a-137">Bağımsız belirteç işleyicilerindeki ayarlar, hem hizmet düzeyinde hem de güvenlik belirteci işleyici koleksiyonunda belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3e87a-137">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e87a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e87a-138">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
