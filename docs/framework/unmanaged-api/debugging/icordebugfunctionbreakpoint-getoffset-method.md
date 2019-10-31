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
ms.openlocfilehash: e0e4bfb3f7adb0242456dfc3a4703ca56f118476
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138165"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="fb11e-102">ICorDebugFunctionBreakpoint::GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb11e-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="fb11e-103">İşlev içindeki kesme noktasının konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="fb11e-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb11e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb11e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb11e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb11e-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="fb11e-106">dışı Kesme noktasının uzaklığa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb11e-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb11e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb11e-107">Requirements</span></span>  
 <span data-ttu-id="fb11e-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb11e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb11e-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb11e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb11e-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fb11e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb11e-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb11e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
