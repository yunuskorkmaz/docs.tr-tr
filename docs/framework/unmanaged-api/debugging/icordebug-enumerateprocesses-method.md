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
ms.openlocfilehash: 7bc82c506cf7e223e672a62ca74b215cac870e50
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123851"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="79345-102">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79345-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="79345-103">Hatası ayıklanmakta işlemler için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="79345-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79345-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79345-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79345-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79345-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="79345-106">Hataları ayıklanan işlemlerin Numaralandırıcı Icordebugprocessenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79345-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79345-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79345-107">Requirements</span></span>  
 <span data-ttu-id="79345-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79345-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79345-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79345-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79345-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79345-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79345-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79345-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79345-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79345-112">See also</span></span>

- [<span data-ttu-id="79345-113">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79345-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
