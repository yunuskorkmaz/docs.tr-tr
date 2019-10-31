---
title: ICorDebugEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 2ec769c343ad055132c6d84e64600fc459357a85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124700"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="c9709-102">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9709-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="c9709-103">Bu ıcorı, Genum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9709-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9709-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9709-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9709-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9709-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c9709-106">dışı Bu `ICorDebugEnum` nesnesinin bir kopyası olan `ICorDebugEnum` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9709-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9709-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9709-107">Requirements</span></span>  
 <span data-ttu-id="c9709-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9709-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9709-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9709-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9709-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9709-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9709-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9709-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
