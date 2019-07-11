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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356f7ec9c50ce511883cbf0f5fbcb729493c92af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737574"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="6f2c8-102">ICorDebugArrayValue::GetElement Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f2c8-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="6f2c8-103">Belirli bir dizi öğenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f2c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f2c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f2c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f2c8-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="6f2c8-106">[in] Bu boyut sayısını `ICorDebugArrayValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="6f2c8-107">Bu değer ayrıca boyutudur `indices` boyutuna boyutlarını sayısına eşit olduğundan dizi `ICorDebugArrayValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="6f2c8-108">[in] Dizin değerlerini, her biri bir boyutu içinde bir konumu belirtir bir dizi `ICorDebugArrayValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="6f2c8-109">Bu değer null olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6f2c8-110">[out] Belirtilen öğenin değerini temsil eden bir Icordebugvalue nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f2c8-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f2c8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f2c8-111">Requirements</span></span>  
 <span data-ttu-id="6f2c8-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f2c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f2c8-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f2c8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f2c8-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f2c8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f2c8-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f2c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
