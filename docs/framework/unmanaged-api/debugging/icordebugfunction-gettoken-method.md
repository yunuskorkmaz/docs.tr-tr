---
description: ': ICorDebugFunction:: GetToken metodu hakkında daha fazla bilgi edinin'
title: ICorDebugFunction::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 75c8680252c5047aa7263940da76166597e5a283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692426"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="a15ee-103">ICorDebugFunction::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a15ee-103">ICorDebugFunction::GetToken Method</span></span>

<span data-ttu-id="a15ee-104">Bu işlev için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a15ee-104">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15ee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a15ee-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a15ee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a15ee-106">Parameters</span></span>  

 `pMethodDef`  
 <span data-ttu-id="a15ee-107">dışı `mdMethodDef` Bu işlevin meta verilerine başvuran bir belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a15ee-107">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a15ee-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a15ee-108">Requirements</span></span>  

 <span data-ttu-id="a15ee-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a15ee-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15ee-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a15ee-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a15ee-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a15ee-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a15ee-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15ee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
