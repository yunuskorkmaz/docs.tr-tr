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
ms.openlocfilehash: 07cab119810c4da25d16a4ad7c13f2d2bda16455
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140317"
---
# <a name="metahost_config_flags-enumeration"></a><span data-ttu-id="7d7f1-102">METAHOST_CONFIG_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7d7f1-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="7d7f1-103">[Ilrmetahostpolicy:: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yönteminin `pdwConfigFlags` parametresinde döndürülen olası bayrakları açıklar ve bu [öğe,\<başlatma > öğesinde](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` özniteliğinin varlığını ve ayarını yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d7f1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7d7f1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7d7f1-105">Members</span></span>  
  
|<span data-ttu-id="7d7f1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7d7f1-106">Member</span></span>|<span data-ttu-id="7d7f1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d7f1-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="7d7f1-108">`useLegacyV2RuntimeActivationPolicy` özniteliği [\<startup > öğesinde](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)yoktu.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="7d7f1-109">`useLegacyV2RuntimeActivationPolicy` özniteliği vardı ve `true`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="7d7f1-110">`useLegacyV2RuntimeActivationPolicy` özniteliği vardı ve `false`olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="7d7f1-111">Bu maskeyi, `useLegacyV2RuntimeActivationPolicy`ilgili değerleri almak için `pdwConfigFlags` döndürülen değere uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d7f1-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d7f1-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d7f1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d7f1-113">Requirements</span></span>  
 <span data-ttu-id="7d7f1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d7f1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d7f1-115">**Üst bilgi:** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="7d7f1-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="7d7f1-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7d7f1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d7f1-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d7f1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7f1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d7f1-118">See also</span></span>

- [<span data-ttu-id="7d7f1-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7d7f1-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="7d7f1-120">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d7f1-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="7d7f1-121">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="7d7f1-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
