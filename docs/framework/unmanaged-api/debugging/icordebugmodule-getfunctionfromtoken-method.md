---
title: ICorDebugModule::GetFunctionFromToken Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212587"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="3b1db-102">ICorDebugModule::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="3b1db-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="3b1db-103">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="3b1db-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b1db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b1db-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="3b1db-106">'ndaki `mdMethodDef`İşlevin meta verilerine başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="3b1db-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="3b1db-107">dışı İşlevi temsil eden ICorDebugFunction arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3b1db-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b1db-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b1db-108">Remarks</span></span>  
 <span data-ttu-id="3b1db-109">`GetFunctionFromToken`Geçirilen değer `methodDef` bir Microsoft ara DILI (MSIL) yöntemine başvurmadığından Yöntem bir HRESULT CORDBG_E_FUNCTION_NOT_IL döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b1db-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1db-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b1db-110">Requirements</span></span>  
 <span data-ttu-id="3b1db-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b1db-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b1db-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b1db-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b1db-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b1db-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b1db-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b1db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
