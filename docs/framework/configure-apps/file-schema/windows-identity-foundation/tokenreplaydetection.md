---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: bd2272cb83dc0183d5008cfa178e11783f51ca2d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205937"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="47422-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="47422-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="47422-103">Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="47422-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="47422-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="47422-104">\<system.identityModel></span></span>  
<span data-ttu-id="47422-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="47422-105">\<identityConfiguration></span></span>  
<span data-ttu-id="47422-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="47422-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47422-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47422-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="47422-108">Tür</span><span class="sxs-lookup"><span data-stu-id="47422-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47422-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47422-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47422-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47422-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47422-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47422-111">Attributes</span></span>  
  
|<span data-ttu-id="47422-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47422-112">Attribute</span></span>|<span data-ttu-id="47422-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47422-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47422-114">Etkin</span><span class="sxs-lookup"><span data-stu-id="47422-114">enabled</span></span>|<span data-ttu-id="47422-115">Belirteç yeniden yürütme algılaması etkin olup olmadığını belirten bir değeri; belirteç etkinleştirmek için "true" algılama yeniden yürütün.</span><span class="sxs-lookup"><span data-stu-id="47422-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="47422-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="47422-116">expirationPeriod</span></span>|<span data-ttu-id="47422-117">A <xref:System.TimeSpan> öğenin süresi doldu ve önbellekten kaldırıldı olarak kabul edilmeden önce zaman maksimum miktarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47422-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="47422-118">Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="47422-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47422-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47422-119">Child Elements</span></span>  
 <span data-ttu-id="47422-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="47422-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47422-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47422-121">Parent Elements</span></span>  
  
|<span data-ttu-id="47422-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="47422-122">Element</span></span>|<span data-ttu-id="47422-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47422-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47422-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="47422-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="47422-125">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="47422-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="47422-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="47422-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="47422-127">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="47422-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47422-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47422-128">Remarks</span></span>  
 <span data-ttu-id="47422-129">A `<tokenReplayDetection>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="47422-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="47422-130">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="47422-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="47422-131">Belirteç yeniden yürütme önbellek türü tarafından belirtilen [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="47422-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
