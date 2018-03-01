---
title: ICorDebugArrayValue::GetBaseIndicies Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 820d81b4538c3cf2bf6fa123df2012ea06e2d978
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetbaseindicies-method"></a><span data-ttu-id="b4d33-102">ICorDebugArrayValue::GetBaseIndicies Metodu</span><span class="sxs-lookup"><span data-stu-id="b4d33-102">ICorDebugArrayValue::GetBaseIndicies Method</span></span>
<span data-ttu-id="b4d33-103">Dizideki her boyut temel dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="b4d33-103">Gets the base index of each dimension in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4d33-104">Syntax</span></span>  
  
```  
HRESULT GetBaseIndicies (  
    [in] ULONG32          cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32           indicies[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4d33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4d33-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="b4d33-106">[in] Bu boyut sayısını `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b4d33-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span> <span data-ttu-id="b4d33-107">Bu değer ayrıca boyutudur `indicies` boyutuna boyutlarını sayıya eşit olduğundan dizi `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b4d33-107">This value is also the size of the `indicies` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indicies`  
 <span data-ttu-id="b4d33-108">[out] Bu boyutun temel dizin (diğer bir deyişle, başlangıç dizini) her biri olan dizisi, `ICorDebugArrayValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b4d33-108">[out] An array of integers, each of which is the base index (that is, the starting index) of a dimension of this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d33-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4d33-109">Requirements</span></span>  
 <span data-ttu-id="b4d33-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d33-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4d33-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4d33-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d33-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d33-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
