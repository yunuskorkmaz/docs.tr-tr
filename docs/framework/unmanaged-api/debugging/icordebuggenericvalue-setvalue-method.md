---
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
ms.openlocfilehash: 972a981188c36236b81f3da17c09abeeb1e32857
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212197"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="25593-102">ICorDebugGenericValue::SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25593-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="25593-103">Belirtilen arabellekteki yeni bir değer kopyalar.</span><span class="sxs-lookup"><span data-stu-id="25593-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25593-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25593-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25593-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25593-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="25593-106">'ndaki Değerin kopyalanacağı arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="25593-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25593-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25593-107">Remarks</span></span>  
 <span data-ttu-id="25593-108">Başvuru türleri için değer, içerik değil başvurudur.</span><span class="sxs-lookup"><span data-stu-id="25593-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25593-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25593-109">Requirements</span></span>  
 <span data-ttu-id="25593-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25593-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25593-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25593-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25593-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="25593-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25593-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25593-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
