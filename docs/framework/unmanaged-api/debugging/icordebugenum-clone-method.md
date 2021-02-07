---
description: ': Icorı, Genum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 18219757980870dcf9663477d195068a76814de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694584"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="0ee2a-103">ICorDebugEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ee2a-103">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="0ee2a-104">Bu ıcorı, Genum nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ee2a-104">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee2a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ee2a-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ee2a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ee2a-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="0ee2a-107">dışı `ICorDebugEnum` Bu nesnenin kopyası olan bir nesnenin adresine yönelik bir işaretçi `ICorDebugEnum` .</span><span class="sxs-lookup"><span data-stu-id="0ee2a-107">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee2a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ee2a-108">Requirements</span></span>  

 <span data-ttu-id="0ee2a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ee2a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ee2a-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ee2a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ee2a-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0ee2a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ee2a-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ee2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
