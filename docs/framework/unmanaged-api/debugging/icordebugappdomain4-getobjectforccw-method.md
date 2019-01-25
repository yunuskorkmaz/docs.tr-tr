---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eeb0b80ba691d813e3193f7ae746129c6725e1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506543"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="ff9bc-102">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="ff9bc-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="ff9bc-103">COM çağrılabilir sarmalayıcı (CCW) işaretçisinden bir yönetilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="ff9bc-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff9bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff9bc-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff9bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff9bc-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="ff9bc-106">[in] COM çağrılabilir sarmalayıcı (CCW) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ff9bc-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="ff9bc-107">[out] Verilen CCW işaretçisi karşılık gelen yönetilen nesneyi temsil eden bir "ICorDebugValue" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ff9bc-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff9bc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff9bc-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff9bc-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff9bc-109">Requirements</span></span>  
 <span data-ttu-id="ff9bc-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff9bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff9bc-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff9bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff9bc-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff9bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff9bc-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff9bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff9bc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff9bc-114">See also</span></span>
- [<span data-ttu-id="ff9bc-115">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff9bc-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="ff9bc-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ff9bc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
