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
ms.openlocfilehash: e9c341ba3d0164e65cd752baa20f674fe3afc714
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405440"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="6a9d5-102">ICorDebugArrayValue::GetDimensions Metodu</span><span class="sxs-lookup"><span data-stu-id="6a9d5-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="6a9d5-103">Bu dizinin her boyut öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6a9d5-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a9d5-104">Syntax</span></span>  
  
```  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a9d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a9d5-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="6a9d5-106">[in] Bu Icordebugarrayvalue nesnesinin dimensions sayısı.</span><span class="sxs-lookup"><span data-stu-id="6a9d5-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="6a9d5-107">Bu değer ayrıca boyutudur `dims` boyutuna boyutlarını sayıya eşit olduğundan dizi `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6a9d5-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="6a9d5-108">[out] Her biri belirtir öğelerin sayısı bu boyutundaki dizisi, `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6a9d5-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9d5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a9d5-109">Requirements</span></span>  
 <span data-ttu-id="6a9d5-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9d5-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9d5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9d5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
