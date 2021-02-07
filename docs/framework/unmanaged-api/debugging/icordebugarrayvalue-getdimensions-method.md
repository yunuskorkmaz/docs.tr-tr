---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbu Garrayvalue:: GetDimensions Yöntemi'
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
ms.openlocfilehash: 007a48891a01e5779e3f9ef10cec720d6647c8f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723107"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="c82b3-103">ICorDebugArrayValue::GetDimensions Metodu</span><span class="sxs-lookup"><span data-stu-id="c82b3-103">ICorDebugArrayValue::GetDimensions Method</span></span>

<span data-ttu-id="c82b3-104">Bu dizinin her bir boyutundaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c82b3-104">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c82b3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c82b3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c82b3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c82b3-106">Parameters</span></span>  

 `cdim`  
 <span data-ttu-id="c82b3-107">'ndaki Bu ıcorınumber Garrayvalue nesnesinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="c82b3-107">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="c82b3-108">Bu değer Ayrıca, `dims` boyutu nesnenin boyut sayısına eşit olduğundan dizinin boyutudur `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="c82b3-108">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="c82b3-109">dışı Her biri, bu nesnedeki bir boyuttaki öğelerin sayısını belirten bir tamsayılar dizisi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="c82b3-109">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c82b3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c82b3-110">Requirements</span></span>  

 <span data-ttu-id="c82b3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c82b3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c82b3-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c82b3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c82b3-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c82b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c82b3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c82b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
