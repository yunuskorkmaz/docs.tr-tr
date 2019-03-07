---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4dcfb977f5ca87f2219fd3ed8ef87d16c2defd2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472657"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="7aeb5-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7aeb5-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="7aeb5-103">Önceden ayarlanmış kaldırır kesme noktasında belirli adres.</span><span class="sxs-lookup"><span data-stu-id="7aeb5-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aeb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7aeb5-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aeb5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7aeb5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7aeb5-106">[in] A `CORDB_ADDRESS` Kesme noktasının ayarlandığı adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7aeb5-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7aeb5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7aeb5-107">Remarks</span></span>  
 <span data-ttu-id="7aeb5-108">Belirtilen kesme noktası daha önce daha önceki bir çağrı tarafından ayarlanacak [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="7aeb5-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="7aeb5-109">`ClearUnmanagedBreakpoint` Ayıklanan işlemin çalışırken yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="7aeb5-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="7aeb5-110">`ClearUnmanagedBreakpoint` Yöntemi yalnızca yönetilen modunda hata ayıklayıcıyı eklediyseniz ya da belirtilen adresteki hiçbir kesme noktası varsa, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7aeb5-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aeb5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7aeb5-111">Requirements</span></span>  
 <span data-ttu-id="7aeb5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aeb5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aeb5-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7aeb5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aeb5-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aeb5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aeb5-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aeb5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
