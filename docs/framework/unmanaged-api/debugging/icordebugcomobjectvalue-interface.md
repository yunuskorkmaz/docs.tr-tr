---
title: ICorDebugComObjectValue Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9adeec14e102ef575f24566980477a285f87ba40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="13d4e-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13d4e-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="13d4e-103">Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) ile ilgili bilgileri almak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13d4e-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13d4e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="13d4e-104">Methods</span></span>  
  
|<span data-ttu-id="13d4e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13d4e-105">Method</span></span>|<span data-ttu-id="13d4e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13d4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13d4e-107">GetCachedInterfacePointers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13d4e-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="13d4e-108">Üzerinde geçerli RCW önbelleğe ham arabirim işaretçileri alır.</span><span class="sxs-lookup"><span data-stu-id="13d4e-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="13d4e-109">GetCachedInterfaceTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13d4e-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="13d4e-110">Bir numaralandırıcı arabirimi türleri için geçerli nesne için ortası veya bırakıldığı olarak kullanılan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="13d4e-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13d4e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13d4e-111">Remarks</span></span>  
 <span data-ttu-id="13d4e-112">"ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcısı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="13d4e-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d4e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13d4e-113">Requirements</span></span>  
 <span data-ttu-id="13d4e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13d4e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13d4e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13d4e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13d4e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13d4e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13d4e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d4e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d4e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13d4e-118">See Also</span></span>  
 [<span data-ttu-id="13d4e-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13d4e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="13d4e-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="13d4e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
