---
title: ICorDebug::EnumerateProcesses Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: 09a8a2bb38378f5d4a32d7b00b68d02f1aa4c054
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110706"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="6e3a6-102">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e3a6-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="6e3a6-103">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="6e3a6-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e3a6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e3a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e3a6-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="6e3a6-106">Ayıklanmakta olan işlemlerin numaralandırıcısının bulunduğu ICorDebugProcessEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6e3a6-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e3a6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e3a6-107">Requirements</span></span>  
 <span data-ttu-id="6e3a6-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e3a6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e3a6-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e3a6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e3a6-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e3a6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e3a6-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e3a6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3a6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e3a6-112">See also</span></span>

- [<span data-ttu-id="6e3a6-113">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e3a6-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
