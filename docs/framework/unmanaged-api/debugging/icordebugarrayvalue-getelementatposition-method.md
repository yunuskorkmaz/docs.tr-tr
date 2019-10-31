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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088423"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="63c39-102">ICorDebugArrayValue::GetElementAtPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="63c39-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="63c39-103">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="63c39-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63c39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63c39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63c39-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="63c39-106">'ndaki Alınacak öğenin konumu.</span><span class="sxs-lookup"><span data-stu-id="63c39-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="63c39-107">dışı Öğesinin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63c39-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63c39-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63c39-108">Remarks</span></span>  
 <span data-ttu-id="63c39-109">Çok boyutlu bir dizinin düzeni, C++ dizi düzeninin stilini izler.</span><span class="sxs-lookup"><span data-stu-id="63c39-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c39-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63c39-110">Requirements</span></span>  
 <span data-ttu-id="63c39-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c39-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63c39-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c39-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63c39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c39-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
