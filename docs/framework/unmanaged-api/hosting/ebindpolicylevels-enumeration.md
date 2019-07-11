---
title: EBindPolicyLevels Numaralandırması
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769764"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="ebb8a-102">EBindPolicyLevels Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ebb8a-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="ebb8a-103">Derleme ilkesini uygulamak veya değiştirmek istediğiniz düzeyinde belirtmek için bayrakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebb8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebb8a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="ebb8a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ebb8a-105">Members</span></span>  
  
|<span data-ttu-id="ebb8a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ebb8a-106">Member</span></span>|<span data-ttu-id="ebb8a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebb8a-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="ebb8a-108">İlke yönetici düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="ebb8a-109">İlke uygulama düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="ebb8a-110">İlkenin ana bilgisayar düzeyinde geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="ebb8a-111">Hiçbir ilke düzeyi bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="ebb8a-112">İlke yayımcı düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="ebb8a-113">İlke değişken düzeylerinde uygulanabilir olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="ebb8a-114">.NET Framework derlemesinin uygulamaları arasındaki taşınabilir destek ilkesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="ebb8a-115">Bkz: [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="ebb8a-116">İlke, ortak dil çalışma zamanı (CLR) birleşik olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebb8a-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebb8a-117">Remarks</span></span>  
 <span data-ttu-id="ebb8a-118">Bu numaralandırma yöntemlerini için geçirilen [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) uygulama ilkesi değişiklikleri belirtmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebb8a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebb8a-119">Requirements</span></span>  
 <span data-ttu-id="ebb8a-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebb8a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebb8a-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebb8a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebb8a-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebb8a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebb8a-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebb8a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebb8a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebb8a-124">See also</span></span>

- [<span data-ttu-id="ebb8a-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebb8a-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ebb8a-126">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ebb8a-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
