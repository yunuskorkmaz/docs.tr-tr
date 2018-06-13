---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f0cef2590bb301e6897aa4922454942ecdd0957
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755233"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="0569e-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="0569e-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="0569e-103">Belirteç yeniden yürütme algılaması sağlar ve belirteçler için sona erme saati belirtir.</span><span class="sxs-lookup"><span data-stu-id="0569e-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="0569e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0569e-104">\<system.identityModel></span></span>  
<span data-ttu-id="0569e-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0569e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0569e-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="0569e-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0569e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0569e-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="0569e-108">Tür</span><span class="sxs-lookup"><span data-stu-id="0569e-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0569e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0569e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0569e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0569e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0569e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0569e-111">Attributes</span></span>  
  
|<span data-ttu-id="0569e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0569e-112">Attribute</span></span>|<span data-ttu-id="0569e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0569e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0569e-114">Etkin</span><span class="sxs-lookup"><span data-stu-id="0569e-114">enabled</span></span>|<span data-ttu-id="0569e-115">Belirteç yeniden yürütme algılaması etkin olup olmadığını belirten bir değeri; belirteç etkinleştirmek için "true" yeniden yürütme algılaması.</span><span class="sxs-lookup"><span data-stu-id="0569e-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="0569e-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="0569e-116">expirationPeriod</span></span>|<span data-ttu-id="0569e-117">A <xref:System.TimeSpan> en uzun süreyi öğenin süresi doldu ve önbellekten kaldırıldı kabul edilmeden önce belirtir.</span><span class="sxs-lookup"><span data-stu-id="0569e-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="0569e-118">Nasıl belirleneceği hakkında daha fazla bilgi için <xref:System.TimeSpan> değerler, bakın [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="0569e-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0569e-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0569e-119">Child Elements</span></span>  
 <span data-ttu-id="0569e-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="0569e-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0569e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0569e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0569e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0569e-122">Element</span></span>|<span data-ttu-id="0569e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0569e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0569e-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0569e-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="0569e-125">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0569e-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="0569e-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="0569e-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="0569e-127">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="0569e-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0569e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0569e-128">Remarks</span></span>  
 <span data-ttu-id="0569e-129">A `<tokenReplayDetection>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="0569e-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="0569e-130">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0569e-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="0569e-131">Belirteç yeniden yürütme önbellek türü tarafından belirtilen [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="0569e-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
