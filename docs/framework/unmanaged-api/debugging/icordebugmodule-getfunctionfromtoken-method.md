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
ms.openlocfilehash: cb966a918c63b4fbc00dcf52819b9384427dfdaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129584"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="86a80-102">ICorDebugModule::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="86a80-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="86a80-103">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="86a80-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86a80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86a80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86a80-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86a80-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="86a80-106">'ndaki İşlevin meta verilerine başvuran bir `mdMethodDef` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="86a80-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="86a80-107">dışı İşlevi temsil eden ICorDebugFunction arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86a80-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86a80-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86a80-108">Remarks</span></span>  
 <span data-ttu-id="86a80-109">`methodDef` geçirilen değer bir Microsoft ara dili (MSIL) yöntemine başvurmadığından `GetFunctionFromToken` yöntemi bir CORDBG_E_FUNCTION_NOT_IL HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="86a80-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a80-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86a80-110">Requirements</span></span>  
 <span data-ttu-id="86a80-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86a80-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a80-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="86a80-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a80-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="86a80-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a80-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
