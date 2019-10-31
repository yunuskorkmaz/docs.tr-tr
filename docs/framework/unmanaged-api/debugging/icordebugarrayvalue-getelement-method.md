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
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088485"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="e9337-102">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9337-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="e9337-103">Verilen dizi öğesinin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="e9337-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9337-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9337-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9337-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9337-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="e9337-106">'ndaki Bu `ICorDebugArrayValue` nesnesinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="e9337-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="e9337-107">Boyutu, `ICorDebugArrayValue` nesnesinin boyut sayısına eşit olduğundan, bu değer ayrıca `indices` dizisinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="e9337-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="e9337-108">'ndaki Her biri `ICorDebugArrayValue` nesnesinin boyutunda bir konum belirten Dizin değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="e9337-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="e9337-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9337-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="e9337-110">dışı Belirtilen öğenin değerini temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e9337-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9337-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9337-111">Requirements</span></span>  
 <span data-ttu-id="e9337-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9337-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9337-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9337-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9337-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9337-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9337-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9337-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
