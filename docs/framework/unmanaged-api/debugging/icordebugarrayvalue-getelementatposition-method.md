---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbu Garrayvalue:: GetElementAtPosition yöntemi'
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
ms.openlocfilehash: ef8e4a39f5fe4088b1883803aee037c51f410241
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723042"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="9a067-103">ICorDebugArrayValue::GetElementAtPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="9a067-103">ICorDebugArrayValue::GetElementAtPosition Method</span></span>

<span data-ttu-id="9a067-104">Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="9a067-104">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a067-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a067-105">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a067-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a067-106">Parameters</span></span>  

 `nPosition`  
 <span data-ttu-id="9a067-107">'ndaki Alınacak öğenin konumu.</span><span class="sxs-lookup"><span data-stu-id="9a067-107">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9a067-108">dışı Öğesinin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a067-108">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a067-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a067-109">Remarks</span></span>  

 <span data-ttu-id="9a067-110">Çok boyutlu bir dizinin düzeni, dizi düzeninin C++ stilini izler.</span><span class="sxs-lookup"><span data-stu-id="9a067-110">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a067-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a067-111">Requirements</span></span>  

 <span data-ttu-id="9a067-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a067-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a067-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a067-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a067-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9a067-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a067-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a067-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
