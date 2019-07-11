---
title: ICorDebugProcess::GetHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56f1dd892429724866182248b0c0413a7d2437cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766064"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="fc044-102">ICorDebugProcess::GetHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="fc044-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="fc044-103">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="fc044-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc044-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc044-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc044-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc044-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="fc044-106">[out] Bir işaretçi bir `HPROCESS` yani işlem tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="fc044-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc044-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc044-107">Remarks</span></span>  
 <span data-ttu-id="fc044-108">Hata ayıklama arabirimi tarafından alınan tanıtıcı aittir.</span><span class="sxs-lookup"><span data-stu-id="fc044-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="fc044-109">Hata ayıklayıcı tanıtıcı kullanmadan önce yinelenen.</span><span class="sxs-lookup"><span data-stu-id="fc044-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc044-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc044-110">Requirements</span></span>  
 <span data-ttu-id="fc044-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc044-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc044-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc044-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc044-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc044-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc044-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc044-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
