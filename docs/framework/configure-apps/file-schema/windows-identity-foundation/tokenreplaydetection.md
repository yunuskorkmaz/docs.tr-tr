---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283081"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="f2710-101">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="f2710-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="f2710-102">Belirteç yeniden yürütme algılaması sağlar ve belirteçleri sona erme süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2710-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="f2710-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f2710-103">\<system.identityModel></span></span>  
<span data-ttu-id="f2710-104">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f2710-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f2710-105">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="f2710-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2710-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2710-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="f2710-107">Tür</span><span class="sxs-lookup"><span data-stu-id="f2710-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2710-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2710-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f2710-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2710-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2710-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2710-110">Attributes</span></span>  
  
|<span data-ttu-id="f2710-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2710-111">Attribute</span></span>|<span data-ttu-id="f2710-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2710-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2710-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="f2710-113">enabled</span></span>|<span data-ttu-id="f2710-114">Belirteç yeniden yürütme algılaması etkin olup olmadığını belirten bir değeri; belirteç etkinleştirmek için "true" algılama yeniden yürütün.</span><span class="sxs-lookup"><span data-stu-id="f2710-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="f2710-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="f2710-115">expirationPeriod</span></span>|<span data-ttu-id="f2710-116">A <xref:System.TimeSpan> öğenin süresi doldu ve önbellekten kaldırıldı olarak kabul edilmeden önce zaman maksimum miktarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2710-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="f2710-117">Belirtme hakkında daha fazla bilgi için <xref:System.TimeSpan> değerleri, görmek [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2710-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2710-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2710-118">Child Elements</span></span>  
 <span data-ttu-id="f2710-119">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f2710-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2710-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2710-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f2710-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2710-121">Element</span></span>|<span data-ttu-id="f2710-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2710-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2710-123">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f2710-123">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="f2710-124">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2710-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="f2710-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f2710-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="f2710-126">Güvenlik topluluğu için yapılandırma, belirteç işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2710-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2710-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2710-127">Remarks</span></span>  
 <span data-ttu-id="f2710-128">A `<tokenReplayDetection>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyi altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2710-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="f2710-129">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f2710-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="f2710-130">Belirteç yeniden yürütme önbellek türü tarafından belirtilen [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2710-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
