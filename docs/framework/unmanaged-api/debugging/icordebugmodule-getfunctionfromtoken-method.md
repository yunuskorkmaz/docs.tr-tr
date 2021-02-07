---
description: ': ICorDebugModule:: GetFunctionFromToken yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d6da43441f3774cff44a6f867c3ccf2a8581ebab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691659"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="8a951-103">ICorDebugModule::GetFunctionFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="8a951-103">ICorDebugModule::GetFunctionFromToken Method</span></span>

<span data-ttu-id="8a951-104">Meta veri belirteci tarafından belirtilen işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="8a951-104">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a951-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a951-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a951-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a951-106">Parameters</span></span>  

 `methodDef`  
 <span data-ttu-id="8a951-107">'ndaki `mdMethodDef` İşlevin meta verilerine başvuran bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8a951-107">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="8a951-108">dışı İşlevi temsil eden ICorDebugFunction arabirimi nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8a951-108">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a951-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a951-109">Remarks</span></span>  

 <span data-ttu-id="8a951-110">`GetFunctionFromToken`Geçirilen değer `methodDef` bir Microsoft ara DILI (MSIL) yöntemine başvurmadığından Yöntem bir HRESULT CORDBG_E_FUNCTION_NOT_IL döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a951-110">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a951-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a951-111">Requirements</span></span>  

 <span data-ttu-id="8a951-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a951-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a951-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a951-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a951-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8a951-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a951-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a951-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
