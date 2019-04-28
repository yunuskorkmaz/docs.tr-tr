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
ms.openlocfilehash: 49f5ed8b24d81ba8f32a9fe0ad7488693718bde9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645675"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="7ce4f-102">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ce4f-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="7ce4f-103">Bu dizinin tüm boyutlarının sıfır olmayan bir temel dizinini sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="7ce4f-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ce4f-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ce4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ce4f-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="7ce4f-106">[out] Boolean bir değer için bir işaretçi `true` varsa bu, bir veya daha fazla boyutları `ICorDebugArrayValue` nesne sıfır olmayan bir temel dizinini gerekir; aksi takdirde, Boolean değeridir `false`.</span><span class="sxs-lookup"><span data-stu-id="7ce4f-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce4f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ce4f-107">Requirements</span></span>  
 <span data-ttu-id="7ce4f-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ce4f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ce4f-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ce4f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ce4f-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ce4f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ce4f-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ce4f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
