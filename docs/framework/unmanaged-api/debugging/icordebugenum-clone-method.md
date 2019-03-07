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
ms.openlocfilehash: 5d1226f64df379b5c40304221e9e66eebcdb17b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479245"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="8def0-102">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8def0-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="8def0-103">Bu Icordebugenum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8def0-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8def0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8def0-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8def0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8def0-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8def0-106">[out] Adresine bir işaretçi bir `ICorDebugEnum` bu kopyasını nesnesini `ICorDebugEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8def0-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8def0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8def0-107">Requirements</span></span>  
 <span data-ttu-id="8def0-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8def0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8def0-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8def0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8def0-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8def0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8def0-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8def0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
