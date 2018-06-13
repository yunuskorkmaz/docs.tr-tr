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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da16a22c71c1fac1932f74a9af18fbc30eb326f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410838"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="a14be-102">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a14be-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="a14be-103">Bu Icordebugenum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a14be-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a14be-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a14be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a14be-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a14be-106">[out] Adresine bir işaretçi bir `ICorDebugEnum` bu kopyası olan nesne `ICorDebugEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="a14be-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a14be-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a14be-107">Requirements</span></span>  
 <span data-ttu-id="a14be-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a14be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a14be-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a14be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a14be-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a14be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a14be-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a14be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
