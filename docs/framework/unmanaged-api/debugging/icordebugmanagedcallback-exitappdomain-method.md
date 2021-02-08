---
description: ': ICorDebugManagedCallback:: Exbir Ppdomain yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a08f29c6c4c8196b968118433c31afb715935aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803626"
---
# <a name="icordebugmanagedcallbackexitappdomain-method"></a><span data-ttu-id="2779d-103">ICorDebugManagedCallback::ExitAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2779d-103">ICorDebugManagedCallback::ExitAppDomain Method</span></span>

<span data-ttu-id="2779d-104">Hata ayıklayıcıya bir uygulama etki alanının çıkış olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="2779d-104">Notifies the debugger that an application domain has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2779d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2779d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2779d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2779d-106">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="2779d-107">'ndaki Verilen uygulama etki alanını içeren işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2779d-107">[in] A pointer to an ICorDebugProcess object that represents the process that contains the given application domain.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="2779d-108">'ndaki Çıkış yapan uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2779d-108">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has exited.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2779d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2779d-109">Requirements</span></span>  

 <span data-ttu-id="2779d-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2779d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2779d-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2779d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2779d-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2779d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2779d-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2779d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2779d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2779d-114">See also</span></span>

- [<span data-ttu-id="2779d-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2779d-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
