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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190450"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="3e31b-102">CorDebugChainReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3e31b-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="3e31b-103">Neden veya çağrı zincirinin başlatma nedenlerle gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e31b-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e31b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e31b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="3e31b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3e31b-105">Members</span></span>  
  
|<span data-ttu-id="3e31b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3e31b-106">Member</span></span>|<span data-ttu-id="3e31b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e31b-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="3e31b-108">Hiçbir çağrı zinciri başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="3e31b-109">Zincir Oluşturucu tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="3e31b-110">Zinciri, özel durum Filtresi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="3e31b-111">Zincir güvenlik zorlar kod tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="3e31b-112">Zincirdeki bir bağlam İlkesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="3e31b-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="3e31b-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="3e31b-115">Zincir tarafından bir iş parçacığı yürütme başlangıcı başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="3e31b-116">Zincirinin yönetilen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="3e31b-117">Zincir yönetilmeyen koda giriş tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="3e31b-118">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="3e31b-119">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="3e31b-120">Zincirdeki bir işlev değerlendirmesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="3e31b-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e31b-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e31b-121">Remarks</span></span>  
 <span data-ttu-id="3e31b-122">Kullanım [Icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) başlatma bir çağrı zincirinin nedenlerini belirlemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3e31b-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e31b-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e31b-123">Requirements</span></span>  
 <span data-ttu-id="3e31b-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e31b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e31b-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e31b-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e31b-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e31b-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3e31b-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="3e31b-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3e31b-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e31b-128">See also</span></span>

- [<span data-ttu-id="3e31b-129">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3e31b-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
