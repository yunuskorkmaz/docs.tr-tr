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
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726853"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="3b78a-102">EBindPolicyLevels Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3b78a-102">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="3b78a-103">Derleme ilkesini uygulamak veya değiştirmek için kullanılacak düzeyi belirleyen bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b78a-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b78a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3b78a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3b78a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3b78a-105">Members</span></span>  
  
|<span data-ttu-id="3b78a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3b78a-106">Member</span></span>|<span data-ttu-id="3b78a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b78a-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="3b78a-108">İlkenin yönetici düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="3b78a-109">Bu ilkenin uygulama düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="3b78a-110">İlkenin ana bilgisayar düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="3b78a-111">İlke düzeyindeki bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="3b78a-112">İlkenin yayımcı düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="3b78a-113">İlkenin değişken düzeylerinde geçerli olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="3b78a-114">İlkenin .NET Framework bütünleştirilmiş kod uygulamaları arasında taşınabilirliği desteklemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="3b78a-115">Bkz [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) . yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b78a-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="3b78a-116">İlkenin ortak dil çalışma zamanı (CLR) ile birleştirilmiş olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b78a-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b78a-117">Remarks</span></span>  

 <span data-ttu-id="3b78a-118">Bu numaralandırma, uygulama ilkesindeki değişiklikleri belirtmek için [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) arabiriminin yöntemlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3b78a-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b78a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b78a-119">Requirements</span></span>  

 <span data-ttu-id="3b78a-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b78a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b78a-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b78a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b78a-122">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b78a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b78a-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b78a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b78a-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b78a-124">See also</span></span>

- [<span data-ttu-id="3b78a-125">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b78a-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3b78a-126">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3b78a-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
