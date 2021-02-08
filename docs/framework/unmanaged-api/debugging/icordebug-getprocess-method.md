---
description: ': ICorDebug:: GetProcess Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a24bb0ec645a337b1202b954c165a76bcf8fad9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801312"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="be493-103">ICorDebug::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be493-103">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="be493-104">Belirtilen işlem için "ICorDebugProcess" örneğine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="be493-104">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be493-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be493-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be493-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be493-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="be493-107">'ndaki İşlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="be493-107">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="be493-108">dışı Belirtilen işlem için bir örneğin adresine yönelik bir işaretçi `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="be493-108">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be493-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be493-109">Requirements</span></span>  

 <span data-ttu-id="be493-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be493-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be493-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be493-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be493-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be493-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be493-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be493-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be493-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be493-114">See also</span></span>

- [<span data-ttu-id="be493-115">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be493-115">ICorDebug Interface</span></span>](icordebug-interface.md)
