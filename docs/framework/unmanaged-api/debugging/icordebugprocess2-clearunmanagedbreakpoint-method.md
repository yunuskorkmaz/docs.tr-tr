---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14258ef1ae473fc867d86c89ec877ddbf8c80213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="b5cc4-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5cc4-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="b5cc4-103">Önceden ayarlanmış kaldırır verilen adresindeki kesme noktası.</span><span class="sxs-lookup"><span data-stu-id="b5cc4-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5cc4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5cc4-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5cc4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5cc4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="b5cc4-106">[in] A `CORDB_ADDRESS` kesme ayarlandığı adresini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="b5cc4-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5cc4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5cc4-107">Remarks</span></span>  
 <span data-ttu-id="b5cc4-108">Belirtilen kesme noktası daha önce daha önceki bir çağrı tarafından ayarlanacak [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5cc4-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="b5cc4-109">`ClearUnmanagedBreakpoint` Ayıklanacak işlemi çalışırken yöntemi çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b5cc4-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="b5cc4-110">`ClearUnmanagedBreakpoint` Yöntemi, hata ayıklayıcısının yalnızca yönetilen modunda bağlıysa veya belirtilen adresinde hiçbir kesme noktası varsa, bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5cc4-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5cc4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5cc4-111">Requirements</span></span>  
 <span data-ttu-id="b5cc4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5cc4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5cc4-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5cc4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5cc4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5cc4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5cc4-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5cc4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
