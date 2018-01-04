---
title: "CorDebugChainReason Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1951983c9d167862169bd6178dc65693d724dc0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="2cd80-102">CorDebugChainReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="2cd80-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="2cd80-103">Neden veya çağrı zincirine başlatma nedenlerle gösterir.</span><span class="sxs-lookup"><span data-stu-id="2cd80-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cd80-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2cd80-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2cd80-105">Members</span></span>  
  
|<span data-ttu-id="2cd80-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2cd80-106">Member</span></span>|<span data-ttu-id="2cd80-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cd80-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="2cd80-108">Hiçbir çağrı zincirine başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="2cd80-109">Zincirdeki bir Oluşturucu tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="2cd80-110">Zincirdeki bir özel durum Filtresi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="2cd80-111">Zincir güvenlik zorlar kodu tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="2cd80-112">Zincirdeki bir bağlam İlkesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="2cd80-113">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="2cd80-114">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="2cd80-115">Zincirdeki bir iş parçacığı yürütme başlangıç tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="2cd80-116">Zincir giriş yönetilen koda tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="2cd80-117">Zincir giriş yönetilmeyen koda tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="2cd80-118">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="2cd80-119">Kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="2cd80-120">Zincirdeki bir işlev değerlendirmesi tarafından başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2cd80-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd80-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cd80-121">Remarks</span></span>  
 <span data-ttu-id="2cd80-122">Kullanım [Icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) çağrı zincirine başlatma nedenlerle onaylaması için yöntem.</span><span class="sxs-lookup"><span data-stu-id="2cd80-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd80-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cd80-123">Requirements</span></span>  
 <span data-ttu-id="2cd80-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd80-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd80-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cd80-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cd80-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cd80-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cd80-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd80-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd80-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd80-128">See Also</span></span>  
 [<span data-ttu-id="2cd80-129">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="2cd80-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
