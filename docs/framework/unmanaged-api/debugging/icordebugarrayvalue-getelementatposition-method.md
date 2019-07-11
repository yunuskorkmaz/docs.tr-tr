---
title: ICorDebugArrayValue::GetElementAtPosition Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cfdaeb1bc298c10cbae01c946ffb867cef21d17
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737553"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="242c5-102">ICorDebugArrayValue::GetElementAtPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="242c5-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="242c5-103">Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranılması öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="242c5-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="242c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="242c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="242c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="242c5-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="242c5-106">[in] Alınacak öğenin konumu.</span><span class="sxs-lookup"><span data-stu-id="242c5-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="242c5-107">[out] Öğenin değerini temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="242c5-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="242c5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="242c5-108">Remarks</span></span>  
 <span data-ttu-id="242c5-109">Çok boyutlu bir dizi düzenini C++ stili dizi düzeni izler.</span><span class="sxs-lookup"><span data-stu-id="242c5-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="242c5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="242c5-110">Requirements</span></span>  
 <span data-ttu-id="242c5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="242c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="242c5-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="242c5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="242c5-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="242c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="242c5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="242c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
