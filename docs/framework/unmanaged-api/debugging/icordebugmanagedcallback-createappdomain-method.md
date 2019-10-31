---
title: ICorDebugManagedCallback::CreateAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: fa829d0a08846287835d2ac66a461b4b9b27a09a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090238"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="f2d9a-102">ICorDebugManagedCallback::CreateAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2d9a-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>
<span data-ttu-id="f2d9a-103">Hata ayıklayıcıya bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f2d9a-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2d9a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2d9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2d9a-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="f2d9a-106">'ndaki Uygulama etki alanının oluşturulduğu işlemi temsil eden ICorDebugProcess nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2d9a-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f2d9a-107">'ndaki Oluşturulmuş uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2d9a-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d9a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2d9a-108">Requirements</span></span>  
 <span data-ttu-id="f2d9a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d9a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d9a-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f2d9a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2d9a-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f2d9a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2d9a-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d9a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d9a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2d9a-113">See also</span></span>

- [<span data-ttu-id="f2d9a-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2d9a-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
