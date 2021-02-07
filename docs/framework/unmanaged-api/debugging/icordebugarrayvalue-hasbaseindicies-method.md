---
description: 'Şu konuda daha fazla bilgi edinin: ıcorısegarrayvalue:: HasBaseIndicies yöntemi'
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
ms.openlocfilehash: b251653004801ff2d312dfb34749c413774ddf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722964"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="5cd32-103">ICorDebugArrayValue::HasBaseIndicies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cd32-103">ICorDebugArrayValue::HasBaseIndicies Method</span></span>

<span data-ttu-id="5cd32-104">Bu dizinin herhangi bir boyutunun sıfır olmayan taban dizinine sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="5cd32-104">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd32-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cd32-105">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd32-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cd32-106">Parameters</span></span>  

 `pbHasBaseIndicies`  
 <span data-ttu-id="5cd32-107">dışı `true` Bu nesnenin bir veya daha fazla boyutunun sıfır dışında bir taban dizini varsa, Boolean değeri işaretçisi, `ICorDebugArrayValue` Aksi takdirde, Boolean değeri olur `false` .</span><span class="sxs-lookup"><span data-stu-id="5cd32-107">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd32-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cd32-108">Requirements</span></span>  

 <span data-ttu-id="5cd32-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd32-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd32-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5cd32-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cd32-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5cd32-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cd32-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd32-112">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
