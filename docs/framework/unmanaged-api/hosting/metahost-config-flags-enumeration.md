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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e322f5c7119d13c8a872bd87d00c1e55324b581
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135784"
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="e1dd3-102">METAHOST_CONFIG_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e1dd3-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="e1dd3-103">Döndürülen olası bayraklar açıklar `pdwConfigFlags` parametresinin [Iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) varlığını gösteren ve ayarıyla yöntemi `useLegacyV2RuntimeActivationPolicy` özniteliğini [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="e1dd3-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1dd3-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="e1dd3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e1dd3-105">Members</span></span>  
  
|<span data-ttu-id="e1dd3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e1dd3-106">Member</span></span>|<span data-ttu-id="e1dd3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1dd3-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="e1dd3-108">`useLegacyV2RuntimeActivationPolicy` Özniteliği mevcut değildi [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span><span class="sxs-lookup"><span data-stu-id="e1dd3-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="e1dd3-109">`useLegacyV2RuntimeActivationPolicy` Öznitelik varsa ve için `true`.</span><span class="sxs-lookup"><span data-stu-id="e1dd3-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="e1dd3-110">`useLegacyV2RuntimeActivationPolicy` Öznitelik varsa ve için `false`.</span><span class="sxs-lookup"><span data-stu-id="e1dd3-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="e1dd3-111">Döndürülen değer bu maskesi uygulamak `pdwConfigFlags` ilgili değerleri almak için `useLegacyV2RuntimeActivationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="e1dd3-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1dd3-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1dd3-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1dd3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1dd3-113">Requirements</span></span>  
 <span data-ttu-id="e1dd3-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1dd3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1dd3-115">**Üst bilgi:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="e1dd3-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="e1dd3-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e1dd3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e1dd3-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e1dd3-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e1dd3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1dd3-118">See also</span></span>

- [<span data-ttu-id="e1dd3-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e1dd3-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="e1dd3-120">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1dd3-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
- [<span data-ttu-id="e1dd3-121">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="e1dd3-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
