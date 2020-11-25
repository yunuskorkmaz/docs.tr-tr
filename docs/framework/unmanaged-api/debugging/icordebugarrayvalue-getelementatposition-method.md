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
ms.openlocfilehash: a6e5ecee9a89da98a73dfb20935c5ec594d5958f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732937"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="5583c-102">ICorDebugArrayValue::GetElementAtPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="5583c-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="5583c-103">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="5583c-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5583c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5583c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5583c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5583c-105">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="5583c-106">'ndaki Alınacak öğenin konumu.</span><span class="sxs-lookup"><span data-stu-id="5583c-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="5583c-107">dışı Öğesinin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5583c-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5583c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5583c-108">Remarks</span></span>  

 <span data-ttu-id="5583c-109">Çok boyutlu bir dizinin düzeni, dizi düzeninin C++ stilini izler.</span><span class="sxs-lookup"><span data-stu-id="5583c-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5583c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5583c-110">Requirements</span></span>  

 <span data-ttu-id="5583c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5583c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5583c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5583c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5583c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5583c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5583c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5583c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
