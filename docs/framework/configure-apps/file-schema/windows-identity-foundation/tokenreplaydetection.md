---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944293"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="1b36c-101">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="1b36c-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="1b36c-102">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b36c-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="1b36c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1b36c-103">\<system.identityModel></span></span>  
<span data-ttu-id="1b36c-104">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1b36c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1b36c-105">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="1b36c-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b36c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b36c-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="1b36c-107">Tür</span><span class="sxs-lookup"><span data-stu-id="1b36c-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b36c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b36c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1b36c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b36c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b36c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b36c-110">Attributes</span></span>  
  
|<span data-ttu-id="1b36c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1b36c-111">Attribute</span></span>|<span data-ttu-id="1b36c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b36c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b36c-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="1b36c-113">enabled</span></span>|<span data-ttu-id="1b36c-114">Belirteç yeniden yürütme algılamasının etkinleştirilip etkinleştirilmeyeceğini belirten bir değer; Belirteç yeniden yürütme algılamasını etkinleştirmek için "true".</span><span class="sxs-lookup"><span data-stu-id="1b36c-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="1b36c-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="1b36c-115">expirationPeriod</span></span>|<span data-ttu-id="1b36c-116">Bir <xref:System.TimeSpan> öğenin süresi dolmadan ve önbellekten kaldırılmadan önce geçen maksimum süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="1b36c-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="1b36c-117">Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1b36c-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b36c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b36c-118">Child Elements</span></span>  
 <span data-ttu-id="1b36c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b36c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b36c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b36c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1b36c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b36c-121">Element</span></span>|<span data-ttu-id="1b36c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b36c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b36c-123">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1b36c-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="1b36c-124">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b36c-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1b36c-125">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1b36c-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="1b36c-126">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1b36c-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b36c-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b36c-127">Remarks</span></span>  
 <span data-ttu-id="1b36c-128">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="1b36c-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1b36c-129">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="1b36c-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="1b36c-130">Belirteç yeniden yürütme önbelleğinin türü, [ \<TokenReplayCache >](tokenreplaycache.md) öğesi tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1b36c-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
