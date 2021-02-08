---
description: ': ICorDebug:: EnumerateProcesses yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 44ee21a820a1c9f94f1d66c93ff040b504bfcc93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791588"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="e39aa-103">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e39aa-103">ICorDebug::EnumerateProcesses Method</span></span>

<span data-ttu-id="e39aa-104">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e39aa-104">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39aa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e39aa-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e39aa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e39aa-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="e39aa-107">Ayıklanmakta olan işlemlerin numaralandırıcısının bulunduğu ICorDebugProcessEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e39aa-107">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e39aa-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e39aa-108">Requirements</span></span>  

 <span data-ttu-id="e39aa-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39aa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39aa-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e39aa-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e39aa-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e39aa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e39aa-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39aa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39aa-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e39aa-113">See also</span></span>

- [<span data-ttu-id="e39aa-114">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e39aa-114">ICorDebug Interface</span></span>](icordebug-interface.md)
