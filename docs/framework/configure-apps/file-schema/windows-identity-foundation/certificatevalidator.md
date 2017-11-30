---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="aaf14-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="aaf14-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="aaf14-103">Sertifika doğrulama için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="aaf14-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="aaf14-104">Bu tür yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) öğesi, "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="aaf14-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="aaf14-105">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="aaf14-105">\<system.identityModel></span></span>  
<span data-ttu-id="aaf14-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="aaf14-106">\<identityConfiguration></span></span>  
<span data-ttu-id="aaf14-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="aaf14-107">\<certificateValidation></span></span>  
<span data-ttu-id="aaf14-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="aaf14-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf14-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaf14-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaf14-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaf14-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aaf14-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aaf14-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaf14-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aaf14-112">Attributes</span></span>  
  
|<span data-ttu-id="aaf14-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aaf14-113">Attribute</span></span>|<span data-ttu-id="aaf14-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaf14-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaf14-115">türü</span><span class="sxs-lookup"><span data-stu-id="aaf14-115">type</span></span>|<span data-ttu-id="aaf14-116">Türetilen bir özel tür belirtir <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aaf14-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="aaf14-117">Ayarlama `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) bu türünü kullanmak için "özel" öğesi.</span><span class="sxs-lookup"><span data-stu-id="aaf14-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="aaf14-118">Nasıl belirleneceği hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvuruları](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="aaf14-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="aaf14-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="aaf14-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaf14-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaf14-120">Child Elements</span></span>  
 <span data-ttu-id="aaf14-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="aaf14-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aaf14-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aaf14-122">Parent Elements</span></span>  
  
|<span data-ttu-id="aaf14-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="aaf14-123">Element</span></span>|<span data-ttu-id="aaf14-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaf14-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaf14-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="aaf14-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="aaf14-126">Sertifikaları doğrulamak için belirteci işleyicileri kullanma ayarlarını denetler.</span><span class="sxs-lookup"><span data-stu-id="aaf14-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aaf14-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="aaf14-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
