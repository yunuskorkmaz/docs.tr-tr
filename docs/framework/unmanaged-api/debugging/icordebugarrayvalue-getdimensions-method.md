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
ms.openlocfilehash: c5199794098e4d83588728eeb165aee5f81fe4c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088507"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="63ed9-102">ICorDebugArrayValue::GetDimensions Metodu</span><span class="sxs-lookup"><span data-stu-id="63ed9-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="63ed9-103">Bu dizinin her bir boyutundaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="63ed9-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63ed9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63ed9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63ed9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63ed9-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="63ed9-106">'ndaki Bu ıcorınumber Garrayvalue nesnesinin boyut sayısı.</span><span class="sxs-lookup"><span data-stu-id="63ed9-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="63ed9-107">Boyutu, `ICorDebugArrayValue` nesnesinin boyut sayısına eşit olduğundan, bu değer ayrıca `dims` dizisinin boyutudur.</span><span class="sxs-lookup"><span data-stu-id="63ed9-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="63ed9-108">dışı Her biri bu `ICorDebugArrayValue` nesnesindeki bir boyuttaki öğelerin sayısını belirten bir tamsayılar dizisi.</span><span class="sxs-lookup"><span data-stu-id="63ed9-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63ed9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63ed9-109">Requirements</span></span>  
 <span data-ttu-id="63ed9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63ed9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63ed9-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63ed9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63ed9-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63ed9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63ed9-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63ed9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
