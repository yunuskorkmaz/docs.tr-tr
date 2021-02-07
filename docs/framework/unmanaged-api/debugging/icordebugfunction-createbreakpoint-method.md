---
description: ': ICorDebugFunction:: CreateBreakpoint yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4d55a818352ff98b67c95d5ef15417f2e9e64d40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692634"
---
# <a name="icordebugfunctioncreatebreakpoint-method"></a><span data-ttu-id="f2406-103">ICorDebugFunction::CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2406-103">ICorDebugFunction::CreateBreakpoint Method</span></span>

<span data-ttu-id="f2406-104">Bu işlevin başlangıcında bir kesme noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2406-104">Creates a breakpoint at the beginning of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2406-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2406-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateBreakpoint (  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2406-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2406-106">Parameters</span></span>  

 `ppBreakpoint`  
 <span data-ttu-id="f2406-107">dışı İşlevin yeni kesme noktasını temsil eden ICorDebugFunctionBreakpoint nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2406-107">[out] A pointer to the address of an ICorDebugFunctionBreakpoint object that represents the new breakpoint for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2406-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2406-108">Requirements</span></span>  

 <span data-ttu-id="f2406-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2406-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2406-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2406-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2406-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2406-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2406-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2406-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
