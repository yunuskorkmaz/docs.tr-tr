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
ms.openlocfilehash: e6e8eb91bbc41faf0dcea010da9aa54995058653
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894974"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="2228b-102">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2228b-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="2228b-103">Bu dizinin herhangi bir boyutunun sıfır olmayan taban dizinine sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="2228b-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2228b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2228b-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2228b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2228b-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="2228b-106">dışı Bu `ICorDebugArrayValue` nesnenin bir veya daha fazla boyutunun sıfır `true` dışında bir taban dizini varsa, Boolean değere yönelik bir işaretçi. Aksi takdirde, Boolean değeri `false`.</span><span class="sxs-lookup"><span data-stu-id="2228b-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2228b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2228b-107">Requirements</span></span>  
 <span data-ttu-id="2228b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2228b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2228b-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2228b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2228b-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2228b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2228b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2228b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
