---
description: 'Bu konuda daha fazla bilgi edinin: EBindPolicyLevels numaralandırması'
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
ms.openlocfilehash: 00e10cff79cdd782e8d9ab8e9b7e1e3f388fb1ee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785620"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="c7681-103">EBindPolicyLevels Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c7681-103">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="c7681-104">Derleme ilkesini uygulamak veya değiştirmek için kullanılacak düzeyi belirleyen bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7681-104">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7681-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7681-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c7681-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c7681-106">Members</span></span>  
  
|<span data-ttu-id="c7681-107">Üye</span><span class="sxs-lookup"><span data-stu-id="c7681-107">Member</span></span>|<span data-ttu-id="c7681-108">Description</span><span class="sxs-lookup"><span data-stu-id="c7681-108">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="c7681-109">İlkenin yönetici düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-109">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="c7681-110">Bu ilkenin uygulama düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-110">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="c7681-111">İlkenin ana bilgisayar düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-111">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="c7681-112">İlke düzeyindeki bayrakları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-112">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="c7681-113">İlkenin yayımcı düzeyinde uygulanması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-113">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="c7681-114">İlkenin değişken düzeylerinde geçerli olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-114">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="c7681-115">İlkenin .NET Framework bütünleştirilmiş kod uygulamaları arasında taşınabilirliği desteklemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-115">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="c7681-116">Bkz [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) . yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7681-116">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="c7681-117">İlkenin ortak dil çalışma zamanı (CLR) ile birleştirilmiş olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c7681-117">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7681-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7681-118">Remarks</span></span>  

 <span data-ttu-id="c7681-119">Bu numaralandırma, uygulama ilkesindeki değişiklikleri belirtmek için [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) arabiriminin yöntemlerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c7681-119">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7681-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7681-120">Requirements</span></span>  

 <span data-ttu-id="c7681-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7681-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7681-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c7681-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7681-123">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7681-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7681-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7681-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7681-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7681-125">See also</span></span>

- [<span data-ttu-id="c7681-126">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7681-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c7681-127">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c7681-127">Hosting Enumerations</span></span>](hosting-enumerations.md)
