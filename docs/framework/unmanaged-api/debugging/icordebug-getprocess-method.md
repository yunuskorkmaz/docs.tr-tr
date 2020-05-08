---
title: ICorDebug::GetProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 59afc8ae7d66e81e4dca3923f9c6f7ff3a3a6605
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895379"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="223f2-102">ICorDebug::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="223f2-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="223f2-103">Belirtilen işlem için "ICorDebugProcess" örneğine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="223f2-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="223f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="223f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="223f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="223f2-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="223f2-106">'ndaki İşlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="223f2-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="223f2-107">dışı Belirtilen işlem için bir `ICorDebugProcess` örneğin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="223f2-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="223f2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="223f2-108">Requirements</span></span>  
 <span data-ttu-id="223f2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="223f2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="223f2-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="223f2-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="223f2-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="223f2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="223f2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="223f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223f2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="223f2-113">See also</span></span>

- [<span data-ttu-id="223f2-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="223f2-114">ICorDebug Interface</span></span>](icordebug-interface.md)
