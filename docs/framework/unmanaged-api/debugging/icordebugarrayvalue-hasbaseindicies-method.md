---
title: ICorDebugArrayValue::HasBaseIndicies Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c488ca3a77f2c2b2a40c6143989cd86adf071787
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737435"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="c544d-102">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c544d-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="c544d-103">Bu dizinin tüm boyutlarının sıfır olmayan bir temel dizinini sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c544d-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c544d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c544d-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c544d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c544d-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="c544d-106">[out] Boolean bir değer için bir işaretçi `true` varsa bu, bir veya daha fazla boyutları `ICorDebugArrayValue` nesne sıfır olmayan bir temel dizinini gerekir; aksi takdirde, Boolean değeridir `false`.</span><span class="sxs-lookup"><span data-stu-id="c544d-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c544d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c544d-107">Requirements</span></span>  
 <span data-ttu-id="c544d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c544d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c544d-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c544d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c544d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c544d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c544d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c544d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
