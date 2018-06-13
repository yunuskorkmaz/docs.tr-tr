---
title: ICorDebugFunctionBreakpoint::GetOffset Metodu
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
ms.openlocfilehash: aca1d77ace512ca84cda3b6844d214e4c8d6cad7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412071"
---
# <a name="icordebugfunctionbreakpointgetoffset-method"></a><span data-ttu-id="bee3a-102">ICorDebugFunctionBreakpoint::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="bee3a-102">ICorDebugFunctionBreakpoint::GetOffset Method</span></span>
<span data-ttu-id="bee3a-103">İşlevin içinden kesme uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="bee3a-103">Gets the offset of the breakpoint within the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee3a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bee3a-104">Syntax</span></span>  
  
```  
HRESULT GetOffset (  
    [out] ULONG32  *pnOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bee3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bee3a-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="bee3a-106">[out] Kesme noktası uzaklığını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bee3a-106">[out] A pointer to the offset of the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bee3a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bee3a-107">Requirements</span></span>  
 <span data-ttu-id="bee3a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee3a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee3a-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bee3a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bee3a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bee3a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bee3a-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee3a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
