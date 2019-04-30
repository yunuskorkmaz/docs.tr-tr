---
title: ICorDebugFunctionBreakpoint::GetOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetOffset
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: e619eae4-3ac3-4c37-bba4-55e59989b9cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6253191340c2f2d4f42f47d580b9d923ab3ff041
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651694"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="84e66-102">ICorDebugFunctionBreakpoint::GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84e66-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="84e66-103">İşlev içinde kesme noktasının uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="84e66-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84e66-104">Syntax</span></span>  
  
```  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84e66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84e66-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="84e66-106">[out] Kesme noktası uzaklığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="84e66-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84e66-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84e66-107">Requirements</span></span>  
 <span data-ttu-id="84e66-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84e66-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84e66-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84e66-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84e66-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84e66-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84e66-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e66-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
