---
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
ms.openlocfilehash: 2f53e3e938f62e714bf421ee7ba0cbf0a47b9f8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132277"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="a2e91-102">CorDebugChainReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a2e91-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="a2e91-103">Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e91-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2e91-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a2e91-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a2e91-105">Members</span></span>  
  
|<span data-ttu-id="a2e91-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a2e91-106">Member</span></span>|<span data-ttu-id="a2e91-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e91-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="a2e91-108">Hiçbir çağrı zinciri başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="a2e91-109">Zincir bir Oluşturucu tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="a2e91-110">Zincir bir özel durum filtresi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="a2e91-111">Zincir, güvenliği zorlayan kod tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="a2e91-112">Zincir bir bağlam ilkesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="a2e91-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="a2e91-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="a2e91-115">Zincir, iş parçacığı yürütme başlangıcı tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="a2e91-116">Zincir, yönetilen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="a2e91-117">Zincir, yönetilmeyen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="a2e91-118">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="a2e91-119">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="a2e91-120">Zincir bir işlev değerlendirmesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="a2e91-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2e91-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2e91-121">Remarks</span></span>  
 <span data-ttu-id="a2e91-122">Bir çağrı zincirinin başlatılması nedenlerini belirlemek için [ıcordebugzincirine:: GetReason](icordebugchain-getreason-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a2e91-122">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e91-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2e91-123">Requirements</span></span>  
 <span data-ttu-id="a2e91-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2e91-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2e91-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2e91-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2e91-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2e91-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2e91-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2e91-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e91-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e91-128">See also</span></span>

- [<span data-ttu-id="a2e91-129">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a2e91-129">Debugging Enumerations</span></span>](debugging-enumerations.md)
