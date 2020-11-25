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
ms.openlocfilehash: bf672c90cdbb9e9fb66105820a264a49601b38d7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723460"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="74248-102">ICorDebug::EnumerateProcesses Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74248-102">ICorDebug::EnumerateProcesses Method</span></span>

<span data-ttu-id="74248-103">Hata ayıklamakta olan işlemlere yönelik bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="74248-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74248-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="74248-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74248-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74248-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="74248-106">Ayıklanmakta olan işlemlerin numaralandırıcısının bulunduğu ICorDebugProcessEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74248-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74248-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74248-107">Requirements</span></span>  

 <span data-ttu-id="74248-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74248-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74248-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74248-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74248-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74248-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74248-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74248-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74248-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74248-112">See also</span></span>

- [<span data-ttu-id="74248-113">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74248-113">ICorDebug Interface</span></span>](icordebug-interface.md)
