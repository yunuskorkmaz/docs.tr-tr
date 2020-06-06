---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152794"
---
# \<certificateValidator>
<span data-ttu-id="0af3b-101">Sertifika doğrulaması için özel bir tür belirtir.</span><span class="sxs-lookup"><span data-stu-id="0af3b-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0af3b-102">Bu tür yalnızca `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) öğenin özniteliği "Custom" olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0af3b-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="0af3b-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0af3b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0af3b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0af3b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="0af3b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0af3b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0af3b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0af3b-106">Attributes</span></span>  
  
|<span data-ttu-id="0af3b-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0af3b-107">Attribute</span></span>|<span data-ttu-id="0af3b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0af3b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0af3b-109">tür</span><span class="sxs-lookup"><span data-stu-id="0af3b-109">type</span></span>|<span data-ttu-id="0af3b-110">Sınıfından türetilen özel bir tür belirtir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="0af3b-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0af3b-111">`certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) Bu türü kullanmak için, öğesinin özniteliğini "Custom" olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0af3b-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="0af3b-112">Özniteliği belirtme hakkında daha fazla bilgi için `type` bkz. [özel tür başvuruları](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0af3b-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="0af3b-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="0af3b-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0af3b-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0af3b-114">Child Elements</span></span>  
 <span data-ttu-id="0af3b-115">Yok</span><span class="sxs-lookup"><span data-stu-id="0af3b-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0af3b-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0af3b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="0af3b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="0af3b-117">Element</span></span>|<span data-ttu-id="0af3b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0af3b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="0af3b-119">Belirteç işleyicilerinin sertifikaları doğrulamak için kullandığı ayarları denetler.</span><span class="sxs-lookup"><span data-stu-id="0af3b-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0af3b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0af3b-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
