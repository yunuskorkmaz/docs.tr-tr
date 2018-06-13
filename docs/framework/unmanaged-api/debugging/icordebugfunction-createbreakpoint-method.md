---
title: ICorDebugFunction::CreateBreakpoint Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::CreateBreakpoint
helpviewer_keywords:
- ICorDebugFunction::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: ffd0f708-0d21-4fae-a395-63b6c45828fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2881b1f420d8e177e093969b2cdd9f2ff36883f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412531"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="677a6-102">ICorDebugFunction::CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="677a6-102">ICorDebugFunction::CreateBreakpoint Method</span></span>
<span data-ttu-id="677a6-103">Bu işlev, başında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="677a6-103">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="677a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="677a6-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="677a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="677a6-105">Parameters</span></span>  
 `ppBreakpoint`  
 <span data-ttu-id="677a6-106">[out] Bir işaretçi adresine Icordebugfunctionbreakpoint nesnenin işlevi için yeni kesme temsil eder.</span><span class="sxs-lookup"><span data-stu-id="677a6-106">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="677a6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="677a6-107">Requirements</span></span>  
 <span data-ttu-id="677a6-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677a6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677a6-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="677a6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="677a6-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="677a6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="677a6-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="677a6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
