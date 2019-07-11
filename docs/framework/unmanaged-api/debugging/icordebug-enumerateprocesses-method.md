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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1a4da6df58c928582a830ef92d286437cb5003c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738222"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="0f1db-102">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f1db-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="0f1db-103">Hatası ayıklanmakta işlemler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="0f1db-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f1db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f1db-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f1db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f1db-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="0f1db-106">Hataları ayıklanan işlemlerin Numaralandırıcı Icordebugprocessenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f1db-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f1db-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f1db-107">Requirements</span></span>  
 <span data-ttu-id="0f1db-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f1db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f1db-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f1db-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f1db-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f1db-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f1db-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f1db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f1db-112">See also</span></span>

- [<span data-ttu-id="0f1db-113">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f1db-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
