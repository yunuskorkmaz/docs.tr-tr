---
title: ICorDebugManagedCallback::UnloadClass Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3eb8bf59ee2a91c62a6ff74b1903d92607a9ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197883"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="0f551-102">ICorDebugManagedCallback::UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f551-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="0f551-103">Hata ayıklayıcı, bir sınıf boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="0f551-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f551-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f551-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f551-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f551-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="0f551-106">[in] Sınıfını içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0f551-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="0f551-107">[in] Bu sınıfın temsil ettiği bir Icordebugclass nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f551-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f551-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0f551-108">Remarks</span></span>  
 <span data-ttu-id="0f551-109">Sınıfı Bu çağrıdan sonra başvurulmaması gereken.</span><span class="sxs-lookup"><span data-stu-id="0f551-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f551-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f551-110">Requirements</span></span>  
 <span data-ttu-id="0f551-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f551-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f551-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f551-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f551-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f551-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f551-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f551-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f551-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f551-115">See also</span></span>

- [<span data-ttu-id="0f551-116">LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f551-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="0f551-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f551-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
