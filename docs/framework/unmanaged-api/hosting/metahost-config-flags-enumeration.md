---
description: 'Hakkında daha fazla bilgi edinin: METAHOST_CONFIG_FLAGS numaralandırması'
title: METAHOST_CONFIG_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 56d70f50d3b4c48b7fbf1aa3be6fc11cda904638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679647"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="56ce7-103">METAHOST_CONFIG_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="56ce7-103">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="56ce7-104">`pdwConfigFlags` [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yönteminin, `useLegacyV2RuntimeActivationPolicy` yapılandırma dosyasının [ \<startup> öğesindeki](../../configure-apps/file-schema/startup/startup-element.md) varlık varlığını ve ayarlarını belirten parametresinde döndürülen olası bayrakları açıklar.</span><span class="sxs-lookup"><span data-stu-id="56ce7-104">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ce7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="56ce7-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="56ce7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="56ce7-106">Members</span></span>  
  
|<span data-ttu-id="56ce7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="56ce7-107">Member</span></span>|<span data-ttu-id="56ce7-108">Description</span><span class="sxs-lookup"><span data-stu-id="56ce7-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="56ce7-109">`useLegacyV2RuntimeActivationPolicy`Özniteliği [ \<startup> öğede](../../configure-apps/file-schema/startup/startup-element.md)yoktu.</span><span class="sxs-lookup"><span data-stu-id="56ce7-109">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="56ce7-110">`useLegacyV2RuntimeActivationPolicy`Özniteliği vardı ve olarak ayarlanmıştır `true` .</span><span class="sxs-lookup"><span data-stu-id="56ce7-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="56ce7-111">`useLegacyV2RuntimeActivationPolicy`Özniteliği vardı ve olarak ayarlanmıştır `false` .</span><span class="sxs-lookup"><span data-stu-id="56ce7-111">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="56ce7-112">Bu maskeyi `pdwConfigFlags` , ile ilgili değerleri almak için ' de döndürülen değere uygulayın `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="56ce7-112">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ce7-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56ce7-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ce7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56ce7-114">Requirements</span></span>  

 <span data-ttu-id="56ce7-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56ce7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ce7-116">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="56ce7-116">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="56ce7-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="56ce7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56ce7-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ce7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ce7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56ce7-119">See also</span></span>

- [<span data-ttu-id="56ce7-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="56ce7-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="56ce7-121">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56ce7-121">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="56ce7-122">\<startup> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="56ce7-122">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
