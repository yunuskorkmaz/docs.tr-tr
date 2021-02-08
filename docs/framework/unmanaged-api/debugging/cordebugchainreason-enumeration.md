---
description: 'Daha fazla bilgi edinin: CorDebugChainReason numaralandırması'
title: CorDebugChainReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
ms.openlocfilehash: 18b6ac9c50c3a44a77a0f63a680b84c70e667e9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801754"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="3de50-103">CorDebugChainReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3de50-103">CorDebugChainReason Enumeration</span></span>

<span data-ttu-id="3de50-104">Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3de50-104">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de50-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3de50-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="3de50-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3de50-106">Members</span></span>  
  
|<span data-ttu-id="3de50-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3de50-107">Member</span></span>|<span data-ttu-id="3de50-108">Description</span><span class="sxs-lookup"><span data-stu-id="3de50-108">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="3de50-109">Hiçbir çağrı zinciri başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="3de50-109">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="3de50-110">Zincir bir Oluşturucu tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-110">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="3de50-111">Zincir bir özel durum filtresi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-111">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="3de50-112">Zincir, güvenliği zorlayan kod tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-112">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="3de50-113">Zincir bir bağlam ilkesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-113">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="3de50-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3de50-114">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="3de50-115">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3de50-115">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="3de50-116">Zincir, iş parçacığı yürütme başlangıcı tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-116">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="3de50-117">Zincir, yönetilen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-117">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="3de50-118">Zincir, yönetilmeyen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-118">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="3de50-119">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3de50-119">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="3de50-120">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3de50-120">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="3de50-121">Zincir bir işlev değerlendirmesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3de50-121">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3de50-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3de50-122">Remarks</span></span>  

 <span data-ttu-id="3de50-123">Bir çağrı zincirinin başlatılması nedenlerini belirlemek için [ıcordebugzincirine:: GetReason](icordebugchain-getreason-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3de50-123">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de50-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3de50-124">Requirements</span></span>  

 <span data-ttu-id="3de50-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de50-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de50-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3de50-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3de50-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3de50-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de50-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de50-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de50-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3de50-129">See also</span></span>

- [<span data-ttu-id="3de50-130">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3de50-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
