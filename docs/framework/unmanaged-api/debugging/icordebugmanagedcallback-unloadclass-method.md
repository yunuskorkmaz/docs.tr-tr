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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197883"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="c8b0d-102">ICorDebugManagedCallback::UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8b0d-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="c8b0d-103">Hata ayıklayıcı, bir sınıf boşaltılıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8b0d-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8b0d-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b0d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8b0d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c8b0d-106">[in] Sınıfını içeren uygulama etki alanını temsil eden bir Icordebugappdomain nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c8b0d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="c8b0d-107">[in] Bu sınıfın temsil ettiği bir Icordebugclass nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8b0d-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b0d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8b0d-108">Remarks</span></span>  
 <span data-ttu-id="c8b0d-109">Sınıfı Bu çağrıdan sonra başvurulmaması gereken.</span><span class="sxs-lookup"><span data-stu-id="c8b0d-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b0d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8b0d-110">Requirements</span></span>  
 <span data-ttu-id="c8b0d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b0d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b0d-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8b0d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8b0d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b0d-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c8b0d-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c8b0d-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8b0d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8b0d-115">See also</span></span>

- [<span data-ttu-id="c8b0d-116">LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8b0d-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="c8b0d-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8b0d-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
