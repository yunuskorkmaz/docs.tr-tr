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
ms.openlocfilehash: 28e0cded33b49e3aadc0564bae3a60bee76c4396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677394"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="26889-102">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26889-102">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="26889-103">Bu ıcorı, Genum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26889-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26889-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="26889-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26889-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26889-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="26889-106">dışı `ICorDebugEnum` Bu nesnenin kopyası olan bir nesnenin adresine yönelik bir işaretçi `ICorDebugEnum` .</span><span class="sxs-lookup"><span data-stu-id="26889-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26889-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26889-107">Requirements</span></span>  

 <span data-ttu-id="26889-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26889-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26889-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26889-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26889-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26889-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26889-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26889-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
