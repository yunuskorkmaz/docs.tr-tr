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
ms.openlocfilehash: fbdf8649e3cb2221e5c74eefd22959dc4b382236
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747691"
---
# <a name="icordebugcodegetaddress-method"></a><span data-ttu-id="8fc69-102">ICorDebugCode::GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fc69-102">ICorDebugCode::GetAddress Method</span></span>
<span data-ttu-id="8fc69-103">Göreli sanal adres (RVA) bu "ICorDebugCode" arabirimi temsil eden kod kesimini alır.</span><span class="sxs-lookup"><span data-stu-id="8fc69-103">Gets the relative virtual address (RVA) of the code segment that this "ICorDebugCode" interface represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fc69-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS *pStart  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fc69-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fc69-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="8fc69-106">[out] Kod kesiminin RVA işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8fc69-106">[out] A pointer to the RVA of the code segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc69-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fc69-107">Requirements</span></span>  
 <span data-ttu-id="8fc69-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc69-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fc69-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fc69-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fc69-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fc69-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc69-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fc69-112">See also</span></span>
