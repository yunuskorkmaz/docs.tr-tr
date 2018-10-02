---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027773"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="d7d72-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="d7d72-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="d7d72-103">Sertifika doğrulama için özel bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7d72-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="d7d72-104">Bu tür, yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d7d72-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="d7d72-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d7d72-105">\<system.identityModel></span></span>  
<span data-ttu-id="d7d72-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d7d72-106">\<identityConfiguration></span></span>  
<span data-ttu-id="d7d72-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="d7d72-107">\<certificateValidation></span></span>  
<span data-ttu-id="d7d72-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="d7d72-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d72-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7d72-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7d72-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7d72-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7d72-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7d72-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7d72-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7d72-112">Attributes</span></span>  
  
|<span data-ttu-id="d7d72-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d7d72-113">Attribute</span></span>|<span data-ttu-id="d7d72-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7d72-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7d72-115">türü</span><span class="sxs-lookup"><span data-stu-id="d7d72-115">type</span></span>|<span data-ttu-id="d7d72-116">Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d7d72-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="d7d72-117">Ayarlama `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) bu türü kullanmak için "özel" öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7d72-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="d7d72-118">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d7d72-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="d7d72-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d7d72-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7d72-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7d72-120">Child Elements</span></span>  
 <span data-ttu-id="d7d72-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7d72-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7d72-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7d72-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d7d72-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7d72-123">Element</span></span>|<span data-ttu-id="d7d72-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7d72-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7d72-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="d7d72-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="d7d72-126">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="d7d72-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7d72-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7d72-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
