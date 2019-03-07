---
title: ICorDebugThreadEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b80e0cc026ce80950c14436abb2e84548f9adb64
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499582"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="8b4ce-102">ICorDebugThreadEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b4ce-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="8b4ce-103">Numaralandırma, geçerli konumdan başlayarak belirtilen Icordebugthread örnek sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b4ce-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b4ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b4ce-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8b4ce-106">[in] Sayısını `ICorDebugThread` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="8b4ce-107">[out] Bir dizi işaretçileri, her biri için işaret eden bir `ICorDebugThread` bir iş parçacığını temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8b4ce-108">[out] İşaretçi sayısına `ICorDebugThread` gerçekte döndürülen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="8b4ce-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="8b4ce-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b4ce-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b4ce-110">Requirements</span></span>  
 <span data-ttu-id="8b4ce-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b4ce-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b4ce-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4ce-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b4ce-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4ce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b4ce-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4ce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
