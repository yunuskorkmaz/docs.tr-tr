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
ms.openlocfilehash: fa2be894af6e44d09c25a736f45acba56052f9fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895048"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="87e21-102">ICorDebugArrayValue::GetDimensions Metodu</span><span class="sxs-lookup"><span data-stu-id="87e21-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="87e21-103">Bu dizinin her bir boyutundaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="87e21-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87e21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87e21-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="87e21-106">'ndaki Bu ıcorınumber Garrayvalue nesnesinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="87e21-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="87e21-107">Bu değer Ayrıca, boyutu `dims` `ICorDebugArrayValue` nesnenin boyut sayısına eşit olduğundan dizinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="87e21-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="87e21-108">dışı Her biri, bu `ICorDebugArrayValue` nesnedeki bir boyuttaki öğelerin sayısını belirten bir tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="87e21-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e21-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87e21-109">Requirements</span></span>  
 <span data-ttu-id="87e21-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e21-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e21-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87e21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87e21-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87e21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e21-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
