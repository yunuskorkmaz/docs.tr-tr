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
ms.openlocfilehash: 965ce04b02a0eb1ca30aba065b3e372332e08b55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752294"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="acf9c-102">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acf9c-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="acf9c-103">Bu Icordebugenum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="acf9c-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf9c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="acf9c-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acf9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="acf9c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="acf9c-106">[out] Adresine bir işaretçi bir `ICorDebugEnum` bu kopyasını nesnesini `ICorDebugEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="acf9c-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acf9c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acf9c-107">Requirements</span></span>  
 <span data-ttu-id="acf9c-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acf9c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acf9c-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acf9c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acf9c-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acf9c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acf9c-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acf9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
