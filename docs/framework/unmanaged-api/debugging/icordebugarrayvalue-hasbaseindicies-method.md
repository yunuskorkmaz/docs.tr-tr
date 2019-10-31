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
ms.openlocfilehash: 418ebb51df3f2d86011ee2e77022c3ee5c7ac0b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088231"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="0c63a-102">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c63a-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="0c63a-103">Bu dizinin herhangi bir boyutunun sıfır olmayan taban dizinine sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="0c63a-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c63a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c63a-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c63a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c63a-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="0c63a-106">dışı Bu `ICorDebugArrayValue` nesnesinin bir veya daha fazla boyutunun sıfır dışında bir taban dizini varsa `true` Boolean değere yönelik bir işaretçi. Aksi takdirde, Boolean değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="0c63a-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c63a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c63a-107">Requirements</span></span>  
 <span data-ttu-id="0c63a-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c63a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c63a-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0c63a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c63a-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0c63a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c63a-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c63a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
