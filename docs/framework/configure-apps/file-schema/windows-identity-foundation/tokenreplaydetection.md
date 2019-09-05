---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251764"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="f3d33-101">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="f3d33-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="f3d33-102">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3d33-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="f3d33-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3d33-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3d33-104">&nbsp;&nbsp;[ **\<System. IdentityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f3d33-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f3d33-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IdentityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f3d33-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f3d33-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**</span><span class="sxs-lookup"><span data-stu-id="f3d33-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d33-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3d33-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="f3d33-108">Tür</span><span class="sxs-lookup"><span data-stu-id="f3d33-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3d33-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3d33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3d33-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3d33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3d33-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3d33-111">Attributes</span></span>  
  
|<span data-ttu-id="f3d33-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3d33-112">Attribute</span></span>|<span data-ttu-id="f3d33-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3d33-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3d33-114">enabled</span><span class="sxs-lookup"><span data-stu-id="f3d33-114">enabled</span></span>|<span data-ttu-id="f3d33-115">Belirteç yeniden yürütme algılamasının etkinleştirilip etkinleştirilmeyeceğini belirten bir değer; Belirteç yeniden yürütme algılamasını etkinleştirmek için "true".</span><span class="sxs-lookup"><span data-stu-id="f3d33-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="f3d33-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="f3d33-116">expirationPeriod</span></span>|<span data-ttu-id="f3d33-117">Bir <xref:System.TimeSpan> öğenin süresi dolmadan ve önbellekten kaldırılmadan önce geçen maksimum süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f3d33-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="f3d33-118">Değerlerin nasıl belirtilmesi <xref:System.TimeSpan> hakkında daha fazla bilgi için bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f3d33-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3d33-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3d33-119">Child Elements</span></span>  
 <span data-ttu-id="f3d33-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3d33-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3d33-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3d33-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3d33-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3d33-122">Element</span></span>|<span data-ttu-id="f3d33-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3d33-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3d33-124">\<IdentityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f3d33-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="f3d33-125">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3d33-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="f3d33-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f3d33-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="f3d33-127">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3d33-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3d33-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3d33-128">Remarks</span></span>  
 <span data-ttu-id="f3d33-129">Öğesi, `<identityConfiguration>` öğesinin altındaki hizmet düzeyinde veya öğesinin altındaki `<securityTokenHandlerConfiguration>` güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="f3d33-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="f3d33-130">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f3d33-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="f3d33-131">Belirteç yeniden yürütme önbelleğinin türü, [ \<TokenReplayCache >](tokenreplaycache.md) öğesi tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f3d33-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
