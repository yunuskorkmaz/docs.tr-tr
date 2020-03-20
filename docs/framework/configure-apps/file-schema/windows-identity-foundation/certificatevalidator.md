---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152794"
---
# <a name="certificatevalidator"></a><span data-ttu-id="1d357-101">\<sertifikaValidator></span><span class="sxs-lookup"><span data-stu-id="1d357-101">\<certificateValidator></span></span>
<span data-ttu-id="1d357-102">Sertifika doğrulama için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d357-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1d357-103">Bu tür, yalnızca `certificateValidationMode` [ \<sertifika Doğrulama>](certificatevalidation.md) öğesinin özniteliği "Özel" olarak ayarlanırsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d357-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="1d357-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1d357-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1d357-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1d357-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1d357-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1d357-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1d357-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sertifikaDoğrulama>**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="1d357-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="1d357-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sertifikaValidator>**</span><span class="sxs-lookup"><span data-stu-id="1d357-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d357-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d357-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d357-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d357-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d357-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1d357-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d357-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1d357-112">Attributes</span></span>  
  
|<span data-ttu-id="1d357-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1d357-113">Attribute</span></span>|<span data-ttu-id="1d357-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d357-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d357-115">type</span><span class="sxs-lookup"><span data-stu-id="1d357-115">type</span></span>|<span data-ttu-id="1d357-116"><xref:System.IdentityModel.Selectors.X509CertificateValidator> Sınıftan türeyen özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="1d357-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="1d357-117">Bu tür kullanmak için [ \<sertifika Doğrulama>](certificatevalidation.md) öğesinin özniteliğini "Özel" olarak ayarlayın. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="1d357-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="1d357-118">Öznitelik nasıl belirtilir `type` hakkında daha fazla bilgi için bkz. [Custom Type References](../windows-workflow-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="1d357-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="1d357-119">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1d357-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d357-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d357-120">Child Elements</span></span>  
 <span data-ttu-id="1d357-121">None</span><span class="sxs-lookup"><span data-stu-id="1d357-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d357-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1d357-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1d357-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1d357-123">Element</span></span>|<span data-ttu-id="1d357-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d357-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d357-125">\<sertifikaDoğrulama></span><span class="sxs-lookup"><span data-stu-id="1d357-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="1d357-126">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="1d357-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d357-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d357-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
