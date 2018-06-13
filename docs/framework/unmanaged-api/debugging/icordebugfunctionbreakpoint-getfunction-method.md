---
title: ICorDebugFunctionBreakpoint::GetFunction Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint::GetFunction
helpviewer_keywords:
- ICorDebugFunctionBreakpoint::GetFunction method [.NET Framework debugging]
- GetFunction method, ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 2a62dae5-dd8a-4696-b817-0e1e586c24a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da22570441324a01fea307116bc23601e62919a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411370"
---
# <a name="icordebugfunctionbreakpointgetfunction-method"></a><span data-ttu-id="292a2-102">ICorDebugFunctionBreakpoint::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="292a2-102">ICorDebugFunctionBreakpoint::GetFunction Method</span></span>
<span data-ttu-id="292a2-103">Arabirim işaretçisi kesme ayarlanmış işlevi başvuruda bulunan bir ICorDebugFunction alır.</span><span class="sxs-lookup"><span data-stu-id="292a2-103">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="292a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="292a2-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="292a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="292a2-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="292a2-106">[out] Kesme noktası ayarlanmış işlevin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="292a2-106">[out] A pointer to the address of the function in which the breakpoint is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292a2-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="292a2-107">Requirements</span></span>  
 <span data-ttu-id="292a2-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="292a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292a2-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="292a2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="292a2-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="292a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="292a2-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
