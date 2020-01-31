---
title: ICorDebugManagedCallback::ExitAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitAppDomain
helpviewer_keywords:
- ICorDebugManagedCallback::ExitAppDomain method [.NET Framework debugging]
- ExitAppDomain method [.NET Framework debugging]
ms.assetid: d815486e-b3bd-4fe8-ba28-02abdb4d67ba
topic_type:
- apiref
ms.openlocfilehash: 7bfa71ccff4a65e72a6b548a09d27648b67c0ae5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781849"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="8ac82-102">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ac82-102">ICorDebugManagedCallback::ExitAppDomain Method</span></span>
<span data-ttu-id="8ac82-103">Hata ayıklayıcıya bir uygulama etki alanının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="8ac82-103">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ac82-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ac82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ac82-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="8ac82-106">'ndaki Verilen uygulama etki alanını içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ac82-106">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="8ac82-107">'ndaki Çıkış yapan uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8ac82-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ac82-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ac82-108">Requirements</span></span>  
 <span data-ttu-id="8ac82-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ac82-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ac82-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ac82-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ac82-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8ac82-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ac82-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ac82-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac82-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ac82-113">See also</span></span>

- [<span data-ttu-id="8ac82-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ac82-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
