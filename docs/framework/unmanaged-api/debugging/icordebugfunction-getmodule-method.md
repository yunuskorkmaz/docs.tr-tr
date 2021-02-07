---
description: ': ICorDebugFunction:: GetModule yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFunction::GetModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 62087cdf0443b2ef495461aab74cfa047b95efca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692478"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="919b5-103">ICorDebugFunction::GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="919b5-103">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="919b5-104">Bu işlevin tanımlandığı modülü alır.</span><span class="sxs-lookup"><span data-stu-id="919b5-104">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919b5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="919b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="919b5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="919b5-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="919b5-107">dışı Bu işlevin tanımlandığı modülü temsil eden bir ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="919b5-107">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919b5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="919b5-108">Requirements</span></span>  

 <span data-ttu-id="919b5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919b5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919b5-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="919b5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="919b5-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="919b5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="919b5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919b5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
