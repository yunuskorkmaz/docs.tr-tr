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
ms.openlocfilehash: e70a1c66baff2d91554dea47e248a7003e30c498
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414618"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="095fd-102">ICorDebugManagedCallback::UnloadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="095fd-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="095fd-103">Hata ayıklayıcı bir sınıf yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="095fd-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="095fd-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="095fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="095fd-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="095fd-106">[in] Bir işaretçi Icordebugappdomain nesneye sınıfı içeren uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="095fd-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="095fd-107">[in] Bir işaretçi Icordebugclass nesneye sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="095fd-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="095fd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="095fd-108">Remarks</span></span>  
 <span data-ttu-id="095fd-109">Sınıfı bu çağrısından sonra başvurulması değil.</span><span class="sxs-lookup"><span data-stu-id="095fd-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095fd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="095fd-110">Requirements</span></span>  
 <span data-ttu-id="095fd-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095fd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095fd-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="095fd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="095fd-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="095fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="095fd-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095fd-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="095fd-115">See Also</span></span>  
 [<span data-ttu-id="095fd-116">LoadClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="095fd-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)  
 [<span data-ttu-id="095fd-117">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="095fd-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
