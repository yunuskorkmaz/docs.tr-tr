---
title: ICorDebugArrayValue::GetElement Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 0b6b6f46c7fff8f1d4c2ad555c93423f9ca8ac09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698159"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="c3710-102">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3710-102">ICorDebugArrayValue::GetElement Method</span></span>

<span data-ttu-id="c3710-103">Verilen dizi öğesinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c3710-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3710-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c3710-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3710-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3710-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="c3710-106">'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="c3710-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="c3710-107">Bu değer Ayrıca, `indices` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="c3710-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="c3710-108">'ndaki Her biri nesnenin boyutu içinde bir konum belirten Dizin değerleri dizisi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="c3710-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="c3710-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3710-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c3710-110">dışı Belirtilen öğenin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3710-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3710-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3710-111">Requirements</span></span>  

 <span data-ttu-id="c3710-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3710-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3710-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3710-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3710-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3710-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3710-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3710-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
