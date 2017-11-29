---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f95d200f74621a40d2987acf68bc554df8d17ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="fe438-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="fe438-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="fe438-103">Belirteç yeniden yürütme algılaması sağlar ve belirteçler için sona erme saati belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe438-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="fe438-104">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="fe438-104">\<system.identityModel></span></span>  
<span data-ttu-id="fe438-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fe438-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fe438-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="fe438-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe438-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe438-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="fe438-108">Tür</span><span class="sxs-lookup"><span data-stu-id="fe438-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe438-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fe438-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fe438-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe438-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fe438-111">Attributes</span></span>  
  
|<span data-ttu-id="fe438-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fe438-112">Attribute</span></span>|<span data-ttu-id="fe438-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe438-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe438-114">Etkin</span><span class="sxs-lookup"><span data-stu-id="fe438-114">enabled</span></span>|<span data-ttu-id="fe438-115">Belirteç yeniden yürütme algılaması etkin olup olmadığını belirten bir değeri; belirteç etkinleştirmek için "true" yeniden yürütme algılaması.</span><span class="sxs-lookup"><span data-stu-id="fe438-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="fe438-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="fe438-116">expirationPeriod</span></span>|<span data-ttu-id="fe438-117">A <xref:System.TimeSpan> en uzun süreyi öğenin süresi doldu ve önbellekten kaldırıldı kabul edilmeden önce belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe438-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="fe438-118">Nasıl belirleneceği hakkında daha fazla bilgi için <xref:System.TimeSpan> değerler, bakın [Timespan değerleri](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe438-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe438-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-119">Child Elements</span></span>  
 <span data-ttu-id="fe438-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="fe438-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe438-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fe438-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fe438-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="fe438-122">Element</span></span>|<span data-ttu-id="fe438-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe438-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe438-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fe438-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="fe438-125">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe438-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="fe438-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fe438-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="fe438-127">Güvenlik bir koleksiyon için yapılandırma belirteci işleyicileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe438-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe438-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe438-128">Remarks</span></span>  
 <span data-ttu-id="fe438-129">A `<tokenReplayDetection>` öğesi altında hizmet düzeyinde belirtilebilir `<identityConfiguration>` öğesi veya güvenlik belirteci işleyicisi koleksiyon düzeyinde altında `<securityTokenHandlerConfiguration>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe438-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="fe438-130">Bir belirteci işleyicisi koleksiyon ayarlarını hizmette belirtilen geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fe438-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="fe438-131">Belirteç yeniden yürütme önbellek türü tarafından belirtilen [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="fe438-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
