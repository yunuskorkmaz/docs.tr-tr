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
ms.openlocfilehash: 7a52e61f41bd1d7f68523dd16f70010ffbba401e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895031"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="33c5c-102">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33c5c-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="33c5c-103">Verilen dizi öğesinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="33c5c-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33c5c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33c5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33c5c-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="33c5c-106">'ndaki Bu `ICorDebugArrayValue` nesnenin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="33c5c-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="33c5c-107">Bu değer Ayrıca, boyutu `indices` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan dizinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="33c5c-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="33c5c-108">'ndaki Her biri `ICorDebugArrayValue` nesnenin boyutu içinde bir konum belirten Dizin değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="33c5c-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="33c5c-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="33c5c-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="33c5c-110">dışı Belirtilen öğenin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="33c5c-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33c5c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33c5c-111">Requirements</span></span>  
 <span data-ttu-id="33c5c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33c5c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33c5c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33c5c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33c5c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="33c5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33c5c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33c5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
