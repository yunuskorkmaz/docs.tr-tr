---
description: 'Hakkında daha fazla bilgi edinin: <tokenReplayDetection>'
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a8a6b754a3282afe4f2932296b06b84c09fb6f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786544"
---
# \<tokenReplayDetection>

<span data-ttu-id="a78b0-102">Belirteç yeniden yürütme algılamayı etkinleştirilir ve belirteçler için süre sonu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a78b0-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="a78b0-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="a78b0-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="a78b0-104">Tür</span><span class="sxs-lookup"><span data-stu-id="a78b0-104">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a78b0-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a78b0-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a78b0-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a78b0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a78b0-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a78b0-107">Attributes</span></span>  
  
|<span data-ttu-id="a78b0-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a78b0-108">Attribute</span></span>|<span data-ttu-id="a78b0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a78b0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a78b0-110">enabled</span><span class="sxs-lookup"><span data-stu-id="a78b0-110">enabled</span></span>|<span data-ttu-id="a78b0-111">Belirteç yeniden yürütme algılamasının etkinleştirilip etkinleştirilmeyeceğini belirten bir değer; Belirteç yeniden yürütme algılamasını etkinleştirmek için "true".</span><span class="sxs-lookup"><span data-stu-id="a78b0-111">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="a78b0-112">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="a78b0-112">expirationPeriod</span></span>|<span data-ttu-id="a78b0-113">Bir <xref:System.TimeSpan> öğenin süresi dolmadan ve önbellekten kaldırılmadan önce geçen maksimum süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="a78b0-113">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="a78b0-114">Değerlerin nasıl belirtilmesi hakkında daha fazla bilgi için <xref:System.TimeSpan> bkz. [TimeSpan değerleri](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="a78b0-114">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a78b0-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a78b0-115">Child Elements</span></span>  

 <span data-ttu-id="a78b0-116">Yok</span><span class="sxs-lookup"><span data-stu-id="a78b0-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a78b0-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a78b0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a78b0-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a78b0-118">Element</span></span>|<span data-ttu-id="a78b0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a78b0-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="a78b0-120">Hizmet düzeyi kimlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a78b0-120">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a78b0-121">Bir güvenlik belirteci işleyicileri koleksiyonu için yapılandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="a78b0-121">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a78b0-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a78b0-122">Remarks</span></span>  

 <span data-ttu-id="a78b0-123">Öğesi `<tokenReplayDetection>` , öğesinin altındaki hizmet düzeyinde `<identityConfiguration>` veya öğesinin altındaki güvenlik belirteci işleyicisi koleksiyonu düzeyinde belirtilebilir `<securityTokenHandlerConfiguration>` .</span><span class="sxs-lookup"><span data-stu-id="a78b0-123">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="a78b0-124">Belirteç işleyici koleksiyonundaki ayarlar, hizmette belirtilen ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a78b0-124">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="a78b0-125">Belirteç yeniden yürütme önbelleğinin türü, öğesi tarafından belirtilir [\<tokenReplayCache>](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="a78b0-125">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
