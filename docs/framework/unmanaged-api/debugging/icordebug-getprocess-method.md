---
title: ICorDebug::GetProcess Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acdcb15f22c130601394ee1bb259207e5e3df23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="02388-102">ICorDebug::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="02388-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="02388-103">Bir işaretçi "ICorDebugProcess" örneği için belirtilen işlem alır.</span><span class="sxs-lookup"><span data-stu-id="02388-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02388-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02388-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02388-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02388-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="02388-106">[in] İşlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="02388-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="02388-107">[out] Adresine bir işaretçi bir `ICorDebugProcess` belirtilen işlem için örnek.</span><span class="sxs-lookup"><span data-stu-id="02388-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02388-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02388-108">Requirements</span></span>  
 <span data-ttu-id="02388-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02388-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02388-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02388-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02388-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02388-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02388-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02388-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02388-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="02388-113">See Also</span></span>  
 [<span data-ttu-id="02388-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02388-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
