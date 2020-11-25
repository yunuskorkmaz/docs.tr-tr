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
ms.openlocfilehash: 46c2b444984c5a0062f1cfbc0cd29dbe409b16fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723447"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="7259c-102">ICorDebug::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7259c-102">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="7259c-103">Belirtilen işlem için "ICorDebugProcess" örneğine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="7259c-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7259c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7259c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7259c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7259c-105">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="7259c-106">'ndaki İşlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7259c-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="7259c-107">dışı Belirtilen işlem için bir örneğin adresine yönelik bir işaretçi `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="7259c-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7259c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7259c-108">Requirements</span></span>  

 <span data-ttu-id="7259c-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7259c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7259c-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7259c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7259c-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7259c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7259c-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7259c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7259c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7259c-113">See also</span></span>

- [<span data-ttu-id="7259c-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7259c-114">ICorDebug Interface</span></span>](icordebug-interface.md)
