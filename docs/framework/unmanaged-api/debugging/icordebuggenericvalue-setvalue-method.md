---
description: ': ICorDebugGenericValue:: SetValue yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugGenericValue::SetValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: e284d9987c8428fadedde0024fd3c65a0d8fe7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791484"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="4fc66-103">ICorDebugGenericValue::SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fc66-103">ICorDebugGenericValue::SetValue Method</span></span>

<span data-ttu-id="4fc66-104">Belirtilen arabellekteki yeni bir değer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="4fc66-104">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc66-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fc66-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fc66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4fc66-106">Parameters</span></span>  

 `pFrom`  
 <span data-ttu-id="4fc66-107">'ndaki Değerin kopyalanacağı arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4fc66-107">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fc66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fc66-108">Remarks</span></span>  

 <span data-ttu-id="4fc66-109">Başvuru türleri için değer, içerik değil başvurudur.</span><span class="sxs-lookup"><span data-stu-id="4fc66-109">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc66-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fc66-110">Requirements</span></span>  

 <span data-ttu-id="4fc66-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fc66-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fc66-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4fc66-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fc66-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4fc66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fc66-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fc66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
