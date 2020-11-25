---
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
ms.openlocfilehash: 01e55659bf2a348ec763f51112cbdcd706f27c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730012"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="5d3e9-102">METAHOST_CONFIG_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5d3e9-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>

<span data-ttu-id="5d3e9-103">`pdwConfigFlags` [ICLRMetaHostPolicy:: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yönteminin, `useLegacyV2RuntimeActivationPolicy` yapılandırma dosyasının [ \<startup> öğesindeki](../../configure-apps/file-schema/startup/startup-element.md) varlık varlığını ve ayarlarını belirten parametresinde döndürülen olası bayrakları açıklar.</span><span class="sxs-lookup"><span data-stu-id="5d3e9-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3e9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d3e9-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="5d3e9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5d3e9-105">Members</span></span>  
  
|<span data-ttu-id="5d3e9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="5d3e9-106">Member</span></span>|<span data-ttu-id="5d3e9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d3e9-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="5d3e9-108">`useLegacyV2RuntimeActivationPolicy`Özniteliği [ \<startup> öğede](../../configure-apps/file-schema/startup/startup-element.md)yoktu.</span><span class="sxs-lookup"><span data-stu-id="5d3e9-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="5d3e9-109">`useLegacyV2RuntimeActivationPolicy`Özniteliği vardı ve olarak ayarlanmıştır `true` .</span><span class="sxs-lookup"><span data-stu-id="5d3e9-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="5d3e9-110">`useLegacyV2RuntimeActivationPolicy`Özniteliği vardı ve olarak ayarlanmıştır `false` .</span><span class="sxs-lookup"><span data-stu-id="5d3e9-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="5d3e9-111">Bu maskeyi `pdwConfigFlags` , ile ilgili değerleri almak için ' de döndürülen değere uygulayın `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="5d3e9-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d3e9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d3e9-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d3e9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d3e9-113">Requirements</span></span>  

 <span data-ttu-id="5d3e9-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d3e9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d3e9-115">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="5d3e9-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="5d3e9-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5d3e9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d3e9-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d3e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3e9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d3e9-118">See also</span></span>

- [<span data-ttu-id="5d3e9-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="5d3e9-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="5d3e9-120">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d3e9-120">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="5d3e9-121">\<startup> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5d3e9-121">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
