---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: df512960b522f17dc9247bb5959e246c8c1f15b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169810"
---
# \<tokenReplayDetection>

<span data-ttu-id="dd7a8-101">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="dd7a8-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd7a8-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="dd7a8-103">Tür</span><span class="sxs-lookup"><span data-stu-id="dd7a8-103">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd7a8-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd7a8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dd7a8-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd7a8-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dd7a8-106">Attributes</span></span>  
  
|<span data-ttu-id="dd7a8-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dd7a8-107">Attribute</span></span>|<span data-ttu-id="dd7a8-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd7a8-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd7a8-109">enabled</span><span class="sxs-lookup"><span data-stu-id="dd7a8-109">enabled</span></span>|<span data-ttu-id="dd7a8-110">Belirteç yeniden yürütme algılamasının etkinleştirilip etkinleştirilmeyeceğini belirten bir değer; Belirteç yeniden yürütme algılamasını etkinleştirmek için "true".</span><span class="sxs-lookup"><span data-stu-id="dd7a8-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="dd7a8-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="dd7a8-111">expirationPeriod</span></span>|<span data-ttu-id="dd7a8-112">Bir <xref:System.TimeSpan> öğenin süresi dolmadan ve önbellekten kaldırılmadan önce geçen maksimum süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="dd7a8-113">Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd7a8-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd7a8-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd7a8-114">Child Elements</span></span>  

 <span data-ttu-id="dd7a8-115">Yok</span><span class="sxs-lookup"><span data-stu-id="dd7a8-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd7a8-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dd7a8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dd7a8-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="dd7a8-117">Element</span></span>|<span data-ttu-id="dd7a8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd7a8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="dd7a8-119">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="dd7a8-120">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd7a8-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd7a8-121">Remarks</span></span>  

 <span data-ttu-id="dd7a8-122">Öğesi `<tokenReplayDetection>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="dd7a8-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="dd7a8-123">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dd7a8-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="dd7a8-124">Belirteç yeniden yürütme önbelleğinin türü, öğesi tarafından belirtilir [\<tokenReplayCache>](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="dd7a8-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
