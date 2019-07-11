---
title: ICorDebugCode::GetSize Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52ba9d5bac5e772d721d38e4e8a7ba6757d0ae2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747494"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="8f0fe-102">ICorDebugCode::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="8f0fe-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="8f0fe-103">Bu "Icordebugcode" tarafından temsil edilen ikili kod bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8f0fe-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f0fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f0fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f0fe-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="8f0fe-106">[out] Bu kod boyutunu bayt cinsinden ikili bir işaretçiye `ICorDebugCode` nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f0fe-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f0fe-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f0fe-107">Requirements</span></span>  
 <span data-ttu-id="8f0fe-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0fe-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0fe-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f0fe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f0fe-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f0fe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f0fe-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0fe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0fe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f0fe-112">See also</span></span>
