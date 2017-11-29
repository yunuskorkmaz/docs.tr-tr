---
title: ICorDebugComObjectValue Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d339d3146a8a9214c3518eac6c31ed5222f9b31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="2415a-102">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2415a-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="2415a-103">Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) ile ilgili bilgileri almak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2415a-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2415a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2415a-104">Methods</span></span>  
  
|<span data-ttu-id="2415a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2415a-105">Method</span></span>|<span data-ttu-id="2415a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2415a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2415a-107">Getcachedınterfacepointers yöntemi</span><span class="sxs-lookup"><span data-stu-id="2415a-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="2415a-108">Üzerinde geçerli RCW önbelleğe ham arabirim işaretçileri alır.</span><span class="sxs-lookup"><span data-stu-id="2415a-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="2415a-109">Getcachedınterfacetypes yöntemi</span><span class="sxs-lookup"><span data-stu-id="2415a-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="2415a-110">Bir numaralandırıcı arabirimi türleri için geçerli nesne için ortası veya bırakıldığı olarak kullanılan olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2415a-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2415a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2415a-111">Remarks</span></span>  
 <span data-ttu-id="2415a-112">"ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcısı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="2415a-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2415a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2415a-113">Requirements</span></span>  
 <span data-ttu-id="2415a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2415a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2415a-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2415a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2415a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2415a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2415a-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2415a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2415a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2415a-118">See Also</span></span>  
 [<span data-ttu-id="2415a-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2415a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2415a-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2415a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
