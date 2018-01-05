---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d459c9ea807114c4f63995ba8fbbb288ea5463b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="16d9e-102">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="16d9e-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="16d9e-103">COM aranabilir sarmalayıcısı (saat) işaretçi yönetilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="16d9e-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16d9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16d9e-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16d9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16d9e-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="16d9e-106">[in] COM aranabilir sarmalayıcısı (saat) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="16d9e-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="16d9e-107">[out] Bir işaretçi adresine "ICorDebugValue" nesnenin karşılık gelen Yönetilen Nesne verilen saatin tersi YÖNDE işaretçiyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="16d9e-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16d9e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16d9e-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16d9e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16d9e-109">Requirements</span></span>  
 <span data-ttu-id="16d9e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16d9e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16d9e-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16d9e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16d9e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16d9e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16d9e-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16d9e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d9e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16d9e-114">See Also</span></span>  
 [<span data-ttu-id="16d9e-115">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16d9e-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="16d9e-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="16d9e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
