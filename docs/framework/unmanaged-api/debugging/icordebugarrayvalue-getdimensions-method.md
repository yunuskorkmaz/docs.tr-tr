---
title: ICorDebugArrayValue::GetDimensions Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c0f4836a3dc848b52ee7fe6947f350e6fab787f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737556"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="20385-102">ICorDebugArrayValue::GetDimensions Metodu</span><span class="sxs-lookup"><span data-stu-id="20385-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="20385-103">Bu dizinin her boyutundaki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="20385-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20385-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20385-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20385-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20385-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="20385-106">[in] Bu Icordebugarrayvalue nesnesinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="20385-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="20385-107">Bu değer ayrıca boyutudur `dims` boyutuna boyutlarını sayısına eşit olduğundan dizi `ICorDebugArrayValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="20385-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="20385-108">[out] Her biri belirtir öğe sayısı bu bir boyutta tamsayı, bir dizi `ICorDebugArrayValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="20385-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20385-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20385-109">Requirements</span></span>  
 <span data-ttu-id="20385-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20385-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20385-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20385-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20385-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20385-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20385-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20385-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
