---
title: ICorDebugArrayValue::GetBaseIndicies Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetBaseIndicies
helpviewer_keywords:
- ICorDebugArrayValue::GetBaseIndicies method [.NET Framework debugging]
- GetBaseIndicies method [.NET Framework debugging]
ms.assetid: 868b339b-acdb-4fe0-91c7-b85f4fba99eb
topic_type:
- apiref
ms.openlocfilehash: ea5c5a728afb9ac90f8599c833caab11fd0c65fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731468"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="ef585-102">ICorDebugArrayValue::GetBaseIndicies Metodu</span><span class="sxs-lookup"><span data-stu-id="ef585-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="ef585-103">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="ef585-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef585-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ef585-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef585-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef585-105">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="ef585-106">'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="ef585-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="ef585-107">Bu değer Ayrıca, `indicies` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="ef585-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="ef585-108">dışı Her biri, bu nesnenin bir boyutunun temel dizini (yani, başlangıç dizini) olan tamsayılar dizisi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="ef585-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef585-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef585-109">Requirements</span></span>  

 <span data-ttu-id="ef585-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef585-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef585-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef585-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef585-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ef585-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef585-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef585-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
