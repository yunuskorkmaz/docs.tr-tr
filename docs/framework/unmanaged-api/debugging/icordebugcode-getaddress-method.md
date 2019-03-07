---
title: ICorDebugCode::GetAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetAddress
helpviewer_keywords:
- GetAddress method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetAddress method [.NET Framework debugging]
ms.assetid: cc507cb0-df2e-49c2-b32e-0c3271a8df9a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dda5883d8a1de11fa282e8b8e0fafe924f2d8b7a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494512"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="c6b90-102">ICorDebugCode::GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6b90-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="c6b90-103">Göreli sanal adres (RVA) bu "ICorDebugCode" arabirimi temsil eden kod kesimini alır.</span><span class="sxs-lookup"><span data-stu-id="c6b90-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6b90-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6b90-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6b90-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="c6b90-106">[out] Kod kesiminin RVA işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c6b90-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6b90-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6b90-107">Requirements</span></span>  
 <span data-ttu-id="c6b90-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6b90-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6b90-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6b90-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6b90-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6b90-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6b90-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6b90-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b90-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b90-112">See also</span></span>

