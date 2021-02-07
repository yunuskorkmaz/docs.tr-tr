---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2:: ClearUnmanagedBreakpoint Yöntemi'
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
ms.openlocfilehash: fba31a479e9bac525109e14c02995e78918d4c17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746639"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="bed8c-103">ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bed8c-103">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>

<span data-ttu-id="bed8c-104">Belirtilen adresteki daha önce ayarlanan bir kesme noktasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bed8c-104">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed8c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bed8c-105">Syntax</span></span>  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed8c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bed8c-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="bed8c-107">'ndaki `CORDB_ADDRESS` Kesme noktasının ayarlandığı adresi belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="bed8c-107">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bed8c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bed8c-108">Remarks</span></span>  

 <span data-ttu-id="bed8c-109">Belirtilen kesme noktası daha önce [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)için daha önceki bir çağrı tarafından ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bed8c-109">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="bed8c-110">`ClearUnmanagedBreakpoint`Yöntemi, hata ayıklamakta olan işlem çalışırken çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="bed8c-110">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="bed8c-111">`ClearUnmanagedBreakpoint`Hata ayıklayıcı yalnızca yönetilen modda eklenmişse veya belirtilen adreste hiçbir kesme noktası yoksa, yöntemi bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="bed8c-111">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed8c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bed8c-112">Requirements</span></span>  

 <span data-ttu-id="bed8c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed8c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed8c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bed8c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bed8c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bed8c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bed8c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bed8c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
