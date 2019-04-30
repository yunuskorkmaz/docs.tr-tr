---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: df52212305e0865b8c03fdd49068cb7c7da4fa38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667372"
---
# <a name="certificatevalidator"></a><span data-ttu-id="a61e4-101">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="a61e4-101">\<certificateValidator></span></span>
<span data-ttu-id="a61e4-102">Sertifika doğrulama için özel bir türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a61e4-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="a61e4-103">Bu tür, yalnızca kullanılan `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Özel" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a61e4-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="a61e4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a61e4-104">\<system.identityModel></span></span>  
<span data-ttu-id="a61e4-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a61e4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a61e4-106">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a61e4-106">\<certificateValidation></span></span>  
<span data-ttu-id="a61e4-107">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="a61e4-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61e4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a61e4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a61e4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61e4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a61e4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a61e4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a61e4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a61e4-111">Attributes</span></span>  
  
|<span data-ttu-id="a61e4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a61e4-112">Attribute</span></span>|<span data-ttu-id="a61e4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61e4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a61e4-114">türü</span><span class="sxs-lookup"><span data-stu-id="a61e4-114">type</span></span>|<span data-ttu-id="a61e4-115">Öğesinden türetilen özel bir türü belirtiyor <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a61e4-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="a61e4-116">Ayarlama `certificateValidationMode` özniteliği [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) bu türü kullanmak için "özel" öğesi.</span><span class="sxs-lookup"><span data-stu-id="a61e4-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="a61e4-117">Belirtme hakkında daha fazla bilgi için `type` özniteliği için bkz: [özel tür başvurularını](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a61e4-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="a61e4-118">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a61e4-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a61e4-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61e4-119">Child Elements</span></span>  
 <span data-ttu-id="a61e4-120">None</span><span class="sxs-lookup"><span data-stu-id="a61e4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a61e4-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a61e4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a61e4-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="a61e4-122">Element</span></span>|<span data-ttu-id="a61e4-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a61e4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a61e4-124">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="a61e4-124">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="a61e4-125">Belirteç işleyicileri sertifikalarını doğrulamak için ayar denetler.</span><span class="sxs-lookup"><span data-stu-id="a61e4-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a61e4-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a61e4-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
