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
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137237"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="c2cc3-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2cc3-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="c2cc3-103">Belirtilen adresteki daha önce ayarlanan bir kesme noktasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c2cc3-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cc3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2cc3-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2cc3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2cc3-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="c2cc3-106">'ndaki Kesme noktasının ayarlandığı adresi belirten bir `CORDB_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="c2cc3-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2cc3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2cc3-107">Remarks</span></span>  
 <span data-ttu-id="c2cc3-108">Belirtilen kesme noktası daha önce [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)için daha önceki bir çağrı tarafından ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c2cc3-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="c2cc3-109">Hata ayıklamakta olan işlem çalışırken `ClearUnmanagedBreakpoint` yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2cc3-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="c2cc3-110">`ClearUnmanagedBreakpoint` yöntemi, hata ayıklayıcı yalnızca yönetilen modda eklenmişse veya belirtilen adreste hiçbir kesme noktası yoksa bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c2cc3-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2cc3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2cc3-111">Requirements</span></span>  
 <span data-ttu-id="c2cc3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2cc3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2cc3-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c2cc3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2cc3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c2cc3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2cc3-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2cc3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
