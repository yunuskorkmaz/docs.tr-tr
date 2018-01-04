---
title: "ICorDebug::EnumerateProcesses Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffabcc97a4af33fc859cd096e671f98d52e89e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="2a38a-102">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a38a-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="2a38a-103">Ayıklanacak işlemleri için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="2a38a-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a38a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a38a-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a38a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a38a-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="2a38a-106">Ayıklanacak işlemleri için Numaralandırıcı bir Icordebugprocessenum nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a38a-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a38a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a38a-107">Requirements</span></span>  
 <span data-ttu-id="2a38a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a38a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a38a-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a38a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a38a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a38a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a38a-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a38a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a38a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a38a-112">See Also</span></span>  
 [<span data-ttu-id="2a38a-113">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a38a-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
