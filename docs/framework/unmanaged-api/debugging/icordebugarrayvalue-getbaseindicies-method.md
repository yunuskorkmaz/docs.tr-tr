---
description: 'Şu konuda daha fazla bilgi edinin: ıcorısegarrayvalue:: GetBaseIndicies yöntemi'
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
ms.openlocfilehash: ac38123860cc3187b7dc2398b32244387d19c5ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723128"
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="0aebc-103">ICorDebugArrayValue::GetBaseIndicies Metodu</span><span class="sxs-lookup"><span data-stu-id="0aebc-103">ICorDebugArrayValue::GetBaseIndicies Method</span></span>

<span data-ttu-id="0aebc-104">Dizideki her boyutun temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="0aebc-104">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aebc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0aebc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32           indicies[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aebc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0aebc-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="0aebc-107">'ndaki Bu nesnenin boyut sayısı `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="0aebc-107">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="0aebc-108">Bu değer Ayrıca, `indicies` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="0aebc-108">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="0aebc-109">dışı Her biri, bu nesnenin bir boyutunun temel dizini (yani, başlangıç dizini) olan tamsayılar dizisi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="0aebc-109">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aebc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0aebc-110">Requirements</span></span>  

 <span data-ttu-id="0aebc-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aebc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aebc-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0aebc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aebc-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0aebc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aebc-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aebc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
