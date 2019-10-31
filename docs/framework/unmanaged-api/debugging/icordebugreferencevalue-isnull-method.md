---
title: ICorDebugReferenceValue::IsNull Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9d5047b1d44f836d10b659f18cf885eba3b0e973
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139827"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="60126-102">ICorDebugReferenceValue::IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60126-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="60126-103">Bu ICorDebugReferenceValue değerinin null bir değer olup olmadığını belirten bir değer alır, bu durumda `ICorDebugReferenceValue` bir nesneyi işaret etmez.</span><span class="sxs-lookup"><span data-stu-id="60126-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60126-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60126-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60126-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60126-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="60126-106">dışı Bu `ICorDebugReferenceValue` nesnesi null ise `true` Boole değeri işaretçisi; Aksi takdirde, `pbNull` `false`.</span><span class="sxs-lookup"><span data-stu-id="60126-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60126-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60126-107">Requirements</span></span>  
 <span data-ttu-id="60126-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60126-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60126-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60126-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60126-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="60126-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60126-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60126-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
